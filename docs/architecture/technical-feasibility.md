# Technical Feasibility

> **Status:** Iteration 1b, 1 September 2026.
>
> **This document was written after a full inspection of the repository, not from planning material.** Every status label below reflects what is actually present in the repository as of 1 September 2026.

---

## Repository State — Verified

Recursive inspection on 1 September 2026 found **thirteen files**: twelve Markdown documents and one `.gitignore`.

**There is no application code in this repository.** Specifically, the following do not exist:

| Expected artefact | Present? |
|---|---|
| `package.json` / any dependency manifest | No |
| Expo configuration (`app.json`, `app.config.*`) | No |
| Any `.ts`, `.tsx`, `.js`, or `.jsx` file | No |
| Supabase client, migrations, or SQL | No |
| API or serverless function implementation | No |
| AI provider integration | No |
| Workload or capacity calculation logic | No |
| Camera or image capture implementation | No |
| `.env.example` | No |
| Diagram or image assets | No |
| `app/` directory | No |

Git state: one commit (`d05853e`, "Initial commit"). The rewritten `README.md` and `.gitignore` are modified but uncommitted; `docs/`, `presentation/`, and `prototype/` are untracked. **None of the current documentation is on the remote yet.**

Everything in this document is therefore **planned** unless explicitly marked otherwise. No component is implemented, partially implemented, or tested.

---

## Intended Stack

| Layer | Technology | Rationale |
|---|---|---|
| Mobile | React Native + Expo | One codebase for iOS and Android; camera available without a custom native build; fast iteration during a short phase |
| Database, auth, storage | Supabase | PostgreSQL, authentication, file storage, and Row Level Security in one service on a free tier |
| Server / AI gateway | Vercel serverless functions | Keeps provider credentials off the device; per-request session verification; free tier |
| AI | Claude API | Vision plus language in one provider |
| Notifications | Expo Notifications | Local scheduling is sufficient for the prototype |

**Firebase is explicitly not the application backend.** Supabase covers the same needs without a second service.

**No AI model has been selected.** An identifier carried in earlier planning material does not correspond to a currently available model. Model selection happens at implementation time and must be verified against the provider's current lineup.

---

## Intended Architecture

```text
┌──────────────────────────────────────────┐
│        React Native / Expo (mobile)      │
│  camera · workload views · confirmation  │
│  holds only EXPO_PUBLIC_* values         │
└───────────┬──────────────────┬───────────┘
            │                  │
            │ anon key + RLS   │ session token
            ▼                  ▼
┌────────────────────┐  ┌────────────────────────┐
│      Supabase      │  │  Vercel serverless API │
│  Auth              │  │  verifies session      │
│  PostgreSQL        │  │  validates schema      │
│  Storage           │  │                        │
│  Row Level Security│  │  server-only secrets   │
└────────────────────┘  └───────────┬────────────┘
                                    │
                                    ▼
                        ┌────────────────────────┐
                        │       Claude API       │
                        │  vision · explanation  │
                        └────────────────────────┘
```

The mobile application never contacts the AI provider directly. It has no credential capable of doing so.

---

## Primary Data Flow — Physical-to-Digital Capture

This is the highest-priority technical proof.

```text
1. User photographs a physical source
2. Image is submitted to SEALY's server endpoint with the user's session token
3. Server verifies the session                      → 401 if invalid
4. Server calls the AI provider with the image
5. Model returns structured candidate items
6. Server validates against a schema                → invalid items surfaced, never persisted
7. Candidates returned to the app in review state   → NOT written to the database
8. User reviews each item: edit / accept / reject
9. Only confirmed items are persisted to Supabase
10. Workload calculation runs over the updated task set (deterministic, on-device or server)
11. Overloaded days identified and displayed
12. AI is given the computed result and asked to explain it
```

Steps 7 and 8 are non-negotiable. See [ai-responsibility.md](ai-responsibility.md).

---

## Data Model — Prototype Scope

The prototype implements the minimum needed for the core journey:

| Entity | Purpose |
|---|---|
| Profile | User identity, extending Supabase auth |
| Workspace | Grouping across life areas — academic, career, personal, physical |
| Task | Title, workspace, due date, estimated effort, status, source (manual or extracted) |

`estimated_effort` is load-bearing. Without it there is no capacity calculation and SEALY is a task list.

A far larger relational schema exists in earlier planning material — subjects, project groups, comments, mood logs, habits, focus sessions, workload snapshots, notification logs. It is **deferred**, retained as a future reference, and deliberately not implemented during the prototype phase. Implementing it now would cost days and would not improve the core journey.

**Status: no schema has been created in Supabase.**

---

## Workload / Capacity Metric

**Status: not implemented, and the formulation is not yet decided.**

Two formulations exist in project history. This is an open decision, recorded honestly rather than resolved by assertion.

### Formulation A — capacity versus demand (Iteration 1 direction)

For a given day: sum the estimated effort of commitments due, compare against the user's available hours, and report the difference directly.

> "Thursday contains approximately 7 hours of estimated work while you have around 4 hours of available capacity."

**Advantages:** trivially explainable, obviously deterministic, uses units a student already understands, and makes no claim beyond arithmetic. Requires no calibration.

**Requires:** effort estimates on tasks, and a notion of available hours per day.

### Formulation B — weighted composite score (earlier planning material)

A 0–100 figure combining deadline density, workload volume, recent mood input, and consistency signals under fixed weights.

**Advantages:** single comparable number; captures signals beyond raw hours.

**Disadvantages:** the weights are unvalidated; a 0–100 figure invites interpretation as a probability or a diagnosis; it is harder to explain concretely. It was originally designed under burnout framing that the team has since rejected.

### Current position

Formulation A is favoured because it is directly explainable and consistent with the terminology decision. Formulation B is retained as a possible later layer once effort estimates prove reliable.

**Decision required before implementation.** Whichever is chosen, it is deterministic application code and AI does not compute it.

---

## Security Model

| Value | Location | Exposure |
|---|---|---|
| `EXPO_PUBLIC_SUPABASE_URL` | Mobile bundle | Public by design |
| `EXPO_PUBLIC_SUPABASE_ANON_KEY` | Mobile bundle | Public by design; safe **only** because Row Level Security is enforced |
| `EXPO_PUBLIC_API_URL` | Mobile bundle | Public by design |
| `ANTHROPIC_API_KEY` | Server environment only | Never in the mobile bundle |
| `SUPABASE_SERVICE_ROLE_KEY` | Server environment only | Never in the mobile bundle; bypasses RLS |

**Rules:**

1. Anything prefixed `EXPO_PUBLIC_` is compiled into the app and must be treated as public.
2. Server secrets exist only in the serverless environment.
3. Every server endpoint verifies the caller's session before any AI call.
4. Row Level Security is enabled on every user-owned table, so a leaked anon key does not expose other users' data.
5. Real `.env` files are never committed.

**Verified:** `.gitignore` correctly ignores `.env` and `.env.*` while permitting `.env.example` (lines 33–35). No secrets, tokens, or credentials were found anywhere in the repository.

**Gap:** `.env.example` does not exist. It should be created so the required variable names are documented without any values. **TODO.**

---

## Feature Status

Status determined by repository inspection, not by documentation claims.

### Implemented

**None.** No feature is implemented.

### Partially implemented

**None.**

### Planned — prototype-critical

| Feature | Notes |
|---|---|
| Expo application scaffold | Must launch on a device or emulator |
| Minimal Supabase layer (Profile / Workspace / Task) | Including RLS |
| Camera capture | Highest-priority technical proof |
| AI extraction endpoint | Server-side, session-verified |
| Human confirmation review screen | Per-item edit / accept / reject |
| Deterministic workload calculation | Formulation to be decided |
| Workload visualisation | Across life areas and across days |
| Overloaded-day identification | Follows from the calculation |
| Explainable contributing factors | Which commitments cause the overload |
| Rebalancing suggestions | Proposals only; user approves |
| Recovery recommendations | Protected time |
| SEALY conversational interface | Constrained to explaining computed results |

### Planned — optional spikes, not submission blockers

Scheme of Work importer · mood and energy input · general AI chat · realtime board proof · basic focus timer

### Deferred

Advanced Kanban · sprint and Jira-style views · realtime group collaboration · task dependencies · full Pomodoro system · ambient audio · full habit tracking · XP, levels, and badges · advanced gamification · complex remote push notifications

These remain part of the product vision and may be revisited in a later build phase. **None should be described as implemented or in progress.**

### Explored and abandoned

Firebase backend · custom OCR model training · AI-generated workload score · AR overlay · web-first product · multi-model routing · bulk-accept without per-item review · burnout diagnosis framing

Reasons are recorded in the [evolution log](../ideation/SEALY_Ideation_and_Prototype_Evolution_Log.md).

---

## Risks

| Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|
| **No code exists and the prototype phase is underway** | Certain | High | Scope is already reduced to one core journey; the capture proof is the single highest priority |
| Extraction quality on poor photographs | High | Medium | Human confirmation is the safety net; capture guidance in the UI |
| Effort estimates are unreliable, undermining the capacity metric | High | High | Let users adjust estimates; keep the calculation transparent so errors are visible and correctable |
| Ambiguous academic date formats | Medium | Medium | Flag uncertain dates for explicit confirmation |
| Free-tier limits (AI rate limits, storage, bandwidth) | Medium | Medium | Compress images before upload; avoid retaining images after extraction; keep request volume low during demos |
| Network latency during a live demonstration | Medium | High | Have a pre-captured result available as a fallback |
| Expo Go native module limitations | Medium | Medium | Test capture on a physical device early |
| Documentation and diagram work competing with build time | High | Medium | Diagrams require no code and can proceed in parallel |
| **Competition timeline is ambiguous** | Open | High | See below |

### Open timeline question

The [evolution log](../ideation/SEALY_Ideation_and_Prototype_Evolution_Log.md) records a Building Phase of 21 September – 11 October 2026. Earlier planning material treats 13 September 2026 as the final submission deadline. These are materially different and change how much must be built now. **Must be confirmed against official CodeNection materials.** No documentation in this repository should assume either version until it is resolved.

---

## Prototype Architecture Versus Future Architecture

| Concern | Prototype | Future |
|---|---|---|
| Data model | Profile / Workspace / Task | Full relational schema |
| Workload metric | Single deterministic calculation | Possible weighted composite layer |
| Collaboration | None | Group workspaces, realtime |
| Notifications | Local only | Server-scheduled |
| AI surface | Extraction and explanation | Plus Scheme of Work, rebalancing, conversation |
| Offline | Not handled | Local-first with sync |

---

## Feasibility Assessment

**Is the prototype achievable?** The core journey — capture, extract, confirm, calculate, visualise, explain — is achievable on this stack. Every component is a well-understood pattern, and the AI usage is narrow and bounded.

**The honest risk is time, not technology.** With no code written, the determining factor is scope discipline. The Iteration 1 decision to reduce scope to a single end-to-end journey is what makes this realistic.

**A working capture-to-confirmation-to-visualisation path demonstrates the concept better than a broader set of unfinished features.**

---

## Related Documents

- [AI Responsibility Model](ai-responsibility.md)
- [Ideation and Prototype Evolution Log](../ideation/SEALY_Ideation_and_Prototype_Evolution_Log.md)
- [Prototype Overview](../../prototype/README.md)
