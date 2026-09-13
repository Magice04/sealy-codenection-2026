# SEAL — Technical Feasibility

> **Status: design/prototype architecture only. No application code is implemented in this repository.**

The feasibility goal is not to prove every future feature. It is to show that the **core decision loop** can be built with common mobile/backend patterns while keeping ambitious automation outside the MVP.

## Core loop to prove

```text
Import source
→ structured candidate
→ user confirmation
→ task/event data
→ calculate work-to-finish and time-left
→ Focus / Adjust / Take-a-Break recommendation
→ user-approved action
```

## Intended stack

| Concern | Intended choice | Why |
|---|---|---|
| Mobile | React Native + Expo + TypeScript | One mobile codebase and fast prototyping |
| Backend/database | Supabase + PostgreSQL | Auth, relational storage, RLS and fast setup |
| Auth | Supabase Auth | Fits backend choice |
| Data protection | Row Level Security | User-scoped records |
| Local state | Zustand | Small predictable client state layer |
| Server/cache | TanStack Query | Request/cache lifecycle |
| Calendar | Google Calendar API | Read-only schedule context first |
| Notifications | Expo Notifications | Prototype-friendly reminders |
| OCR | Provider to be chosen | Keep provider swappable behind an adapter |
| Recommendation | Deterministic rules | Explainable/testable MVP |
| Optional AI | extraction cleanup / decomposition / explanation | Helpful but not required for arithmetic |

## Architecture

```text
┌──────────────────────────────────────────┐
│ React Native / Expo                     │
│ Home · Import · Plan · Focus · Insights │
└──────────────────┬───────────────────────┘
                   │
          ┌────────┴────────┐
          │                 │
          ▼                 ▼
 Google Calendar        Supabase
 (read-only first)      Auth + Postgres + RLS
          │                 │
          └────────┬────────┘
                   ▼
          Candidate / Task model
                   │
                   ▼
        Workload-Capacity Engine
                   │
          ┌────────┼─────────┐
          ▼        ▼         ▼
        Focus    Adjust   Take a Break
```

OCR and future adapters feed the same Candidate Intake boundary; they should not each invent their own scheduling model.

## Normalised data model

### Candidate item

| Field | Example |
|---|---|
| type | task / event |
| title | ISP640 Project Plan |
| course | ISP640 · Computing Project Management |
| deadline | 2026-07-03 17:00 |
| estimated_minutes | 90 |
| source | imported PDF / screenshot / calendar |
| confidence | optional extraction confidence |
| needs_confirmation | true |

### Confirmed task

| Field | Purpose |
|---|---|
| id | stable record |
| user_id | ownership |
| title | display name |
| course / context | optional academic context |
| due_at | deadline |
| estimated_minutes | required for capacity reasoning |
| status | planned / done / deferred |
| source | traceability |
| source_ref | optional source metadata |

### Calendar event

| Field | Purpose |
|---|---|
| start_at / end_at | occupied time |
| title | display |
| source | Google Calendar / manual/imported |
| confirmed | whether user accepted it |

## Core calculation

The current prototype uses straightforward arithmetic rather than a weighted mystery score.

```text
work_to_finish = sum(estimated_minutes for relevant unfinished work)
time_left = usable free minutes before the relevant deadlines
shortfall = work_to_finish - time_left
```

Example:

```text
90 + 65 + 60 = 215 minutes (3h35)
time left       = 160 minutes (2h40)
shortfall       = 55 minutes
```

### Why this is preferred

- understandable in seconds;
- traceable to visible tasks;
- no unvalidated 0–100 weighting;
- easier for the user to correct when an estimate is wrong;
- easy to unit test.

## Recommendation rules

A simple MVP rule set remains sufficient:

```text
IF work_to_finish > time_left
    → ADJUST / REBALANCE
ELSE IF recovery_need_high AND no critical deadline soon
    → TAKE A BREAK / RECOVER
ELSE IF important unfinished work exists
    → FOCUS
```

The rule returns a **recommendation**, not an enforced mode.

## Adjustment mechanics

The latest prototype narrows plan changes to four understandable actions.

### Keep

No schedule change.

### Add

“Add” currently means **ask SEAL for another plan option**, not add another task. The Figma prototype contains five fixed alternative arrangements to demonstrate the intended experience.

A real engine would generate bounded alternatives from the same task/deadline/free-slot data and validate each before showing it.

### Move

Move the whole task to a different slot. A real implementation can use a calendar-style interaction, but the core business rule should be independent of drag-and-drop UI.

Current concept constraint:

- warn before overlap;
- no more than two concurrent items in the prototype rule;
- user confirms an overlapping placement.

### Defer

Two explicit reasons:

- the deadline changed → update due date and place it again;
- it is no longer urgent → postpone to the next acceptable slot.

## Plan view feasibility

The Today/Week experience can be implemented from the same event/task model.

- Today: chronological events + urgent work.
- Week: five/seven-day grid with events and due items.
- Task detail: course, source, due time, estimate, requirements, suggested subtasks.

The Figma demo uses uploaded academic documents for realistic course/deadline text. A production build would ingest the user's own sources and ask for confirmation.

## Insights feasibility

7-day, 30-day and semester views are aggregates over persisted events/tasks/focus/recovery history. No special AI is needed.

Example queries:

- sum workload minutes by day/week;
- count overload periods;
- count Focus / Adjust / Take-a-Break actions;
- compare required vs available minutes;
- identify assessment/deadline clusters.

The current Figma values are static examples, not live analytics.

## Focus app-pausing feasibility

The product rule is simple:

> only selected apps are paused; unselected apps remain available.

Actual enforcement is not cross-platform JavaScript-only functionality. Native iOS/Android restrictions, permissions and platform APIs must be evaluated separately. Therefore:

- **MVP prototype:** show configuration and behaviour concept;
- **future native build:** implement only if platform APIs and competition scope allow it.

Do not make app blocking a dependency of the workload-capacity engine.

## OCR / import feasibility

MVP import can start with a single supported path:

```text
Photo / screenshot
→ OCR
→ structured candidate
→ user confirmation
```

The exact OCR provider is intentionally not locked yet. The adapter should return the same Candidate Item structure regardless of provider.

## Future agentic sources

Telegram/share adapters and authorised headless-browser portal intake are technically plausible but increase authentication, privacy and reliability risk.

They belong after the MVP boundary:

```text
Future source adapter
→ Candidate Intake
→ same confirmation
→ same task/event model
```

## Security

For a real implementation:

1. RLS on every user-owned Supabase table.
2. No service-role key in the Expo bundle.
3. OAuth tokens stored/handled according to provider guidance.
4. OCR/AI provider secrets server-side when required.
5. User explicitly authorises external sources.
6. Extracted content remains a candidate until confirmed.
7. Avoid retaining raw documents/photos unless necessary.

## Scope assessment

### Feasible core

- Expo UI
- Supabase auth/data
- one OCR/import path
- Google Calendar read-only
- user confirmation
- deterministic arithmetic
- rule-based recommendation
- Today/Week plan
- simple insights

### Stretch

- AI-assisted decomposition
- Share-to-SEAL
- Telegram intake
- richer behavioural insights
- Desk Presence experiment

### Future / risky

- broad headless-browser automation
- native app blocking across both platforms
- system-wide usage monitoring
- wearables
- deep autonomous rescheduling

## Main technical risks

| Risk | Impact | Mitigation |
|---|---|---|
| Wrong effort estimate | High | user-editable estimates; show arithmetic |
| Bad OCR | Medium | confirmation/edit step |
| Ambiguous dates | High | explicit confirmation |
| Calendar OAuth complexity | Medium | read-only first |
| Native app-blocking limits | High | keep outside core |
| Agentic portal brittleness | High | future, supported-site adapters only |
| Demo overclaims | High | clearly label prototype simulation |

## Competition timeline

The official CodeNection material supplied to the team gives a submission deadline of **13 September 2026, 11:59 PM**. Documentation should not retain the earlier contradictory “build after submission” assumption.

## Related documents

- [AI Responsibility](ai-responsibility.md)
- [Prototype Overview](../../prototype/README.md)
- [Evolution Log](../ideation/SEAL_Ideation_and_Prototype_Evolution_Log.md)
