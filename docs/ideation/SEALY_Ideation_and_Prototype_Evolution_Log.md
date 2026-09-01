# SEALY — Ideation and Prototype Evolution Log

> **Event:** CodeNection 2026  
> **Track:** Lifestyle & Personal Productivity  
> **Problem Statement:** Stress & Workload Manager  
> **Prototype Phase:** 31 August 2026 – 13 September 2026  
> **Purpose:** Record how SEALY evolves during the Workshop & Prototype Phase, including ideas considered, refinements, dropped directions, technical decisions, mentor feedback, and prototype changes.

---

## 31 August 2026 — Iteration 0: Initial Ideation

### Problem Understanding

The team reviewed the **Stress & Workload Manager** challenge and identified that student overload usually does not come from one single responsibility. It develops when several responsibilities accumulate across different areas of life.

Examples include:

- Assignments and exams
- Final Year Project work
- Part-time work
- Internship and career preparation
- Social commitments
- Clubs and extracurricular activities
- Physical wellbeing
- Personal errands
- Household responsibilities
- Rest and recovery

These responsibilities are often managed through disconnected tools and environments such as Google Calendar, WhatsApp, Notion, sticky notes, printed academic materials, whiteboards, and personal memory.

The initial insight was:

> Students may not have a clear picture of their total workload until commitments begin colliding and their available time and energy are already heavily consumed.

### Initial Solution Concept

The team proposed **SEALY**, an AI-powered mobile workload and stress-management companion for students.

The initial feature exploration included:

- Camera-based task scanning
- AI task extraction
- Workload visualisation
- AI conversational coaching
- Burnout prediction
- Mood and energy tracking
- Calendar planning
- Kanban boards
- Sprint/Jira-style views
- Pomodoro focus timer
- Ambient focus sounds
- Habit tracking
- Group project collaboration
- Task dependencies
- Scheme of Work importing
- Push notifications
- XP, levels, badges, and streaks
- A seal mascot with different emotional states

The feature list was intentionally broad. The team did not commit to implementing everything.

### Initial Differentiation Hypothesis

The team identified a possible gap in existing productivity tools:

> Many productivity applications expect users to manually enter information that is already digital, while students still manage important academic responsibilities through physical notes, printed documents, whiteboards, and memory.

This led to the physical-to-digital capture idea:

1. Student photographs physical notes or academic material.
2. AI extracts possible tasks.
3. The student reviews the extracted information.
4. Confirmed tasks enter the workload system.

### Initial Technical Direction

- **Mobile:** React Native with Expo
- **Database / Auth / Storage:** Supabase
- **Backend / AI Gateway:** Vercel Serverless Functions
- **AI:** Claude API
- **Notifications:** Expo Notifications

Firebase was not selected as SEALY's application backend.

### Decision

The team decided to treat the broad concept as the initial ideation baseline and refine it before attempting a full implementation.

### Outcome

This became **Iteration 0 of SEALY**.

---

## 1 September 2026 — Iteration 1: Problem and Scope Refinement

### Refined Problem Definition

The problem was refined from:

> Students are stressed and need help managing tasks.

to:

> **University students often cannot clearly see their total workload across academic, career, social, physical, and personal responsibilities. Because these commitments are fragmented across different tools and environments, students may continue overcommitting and only recognise overload after their available time and energy have already been exceeded.**

This interpretation better matches the challenge because the solution should not only track stress. It should help students understand their load, rebalance responsibilities, and move toward recovery before overload becomes severe.

### Target User

The primary user persona is:

#### Haziq

- **Age:** 21
- **Background:** Final-year Computer Science student
- **Situation:** Balancing academic responsibilities, career preparation, extracurricular commitments, everyday errands, and personal wellbeing

Example responsibilities:

- Final Year Project
- Database assignment
- Midterm revision
- Internship interview preparation
- Club responsibilities
- Grocery shopping
- Laundry
- Exercise
- Social commitments
- Personal rest

Haziq currently uses a mix of:

- WhatsApp
- Google Calendar
- Notion
- Sticky notes
- Printed academic documents
- Personal memory

### Key User Insight

No single responsibility appears catastrophic by itself.

The overload becomes visible only when all responsibilities are considered together.

### Refined Solution Hypothesis

> **If students can see their total workload across different areas of life and receive actionable rebalancing suggestions before major commitments collide, they can make better workload decisions and reduce the risk of becoming severely overloaded.**

---

## Refined Core Prototype Journey

The team reduced SEALY to one primary end-to-end experience:

1. Student captures current responsibilities.
2. SEALY scans physical notes or academic material using the phone camera.
3. AI extracts possible tasks and deadlines.
4. The user reviews, edits, accepts, or rejects the extracted items.
5. Confirmed tasks are incorporated into the user's workload.
6. SEALY visualises workload across different areas of life.
7. The system identifies overloaded days or workload categories.
8. SEALY explains what is causing the overload.
9. SEALY recommends specific workload adjustments.
10. The student reviews and approves suggested changes.
11. SEALY recommends or protects recovery time.
12. The student's workload becomes more manageable.

### Core Flow

> **Capture → Understand → Visualise → Rebalance → Recover**

---

## Prototype-Critical Features

- Workload capture
- Camera-based scanning
- AI task extraction
- Human confirmation before saving AI-generated tasks
- Workload category visualisation
- Workload/capacity analysis
- Overloaded-day identification
- Explainable workload factors
- AI rebalancing suggestions
- Recovery recommendations
- SEALY as the conversational interface

---

## Deferred / Stretch Features

These remain part of the larger product vision but are outside the critical prototype path:

- Advanced Kanban boards
- Sprint/Jira views
- Realtime group collaboration
- Task dependencies
- Full Pomodoro system
- Ambient sound mixer
- Full habit tracking
- XP and badges
- Advanced gamification
- Complex remote push notifications
- Full group-project workflow

These may be revisited during the **Building Phase (21 September – 11 October 2026)** if the core system is stable.

---

## AI Responsibility Refinement

The team decided that SEALY should not be a generic chatbot with a mascot.

### AI Responsibilities

AI may:

- Understand camera images
- Extract possible tasks and deadlines
- Interpret natural-language requests
- Explain workload conditions
- Suggest workload adjustments
- Help break large tasks into smaller actions
- Communicate through SEALY's personality
- Assist with Scheme of Work extraction

### Application Responsibilities

Normal application logic should handle:

- Authentication
- Task storage
- Deadline calculations
- Workload calculations
- Capacity/risk scoring
- Scheduling rules
- Task completion
- Data validation
- Permissions
- Database access control
- Task dependencies
- Streak calculations

This distinction prevents SEALY from becoming only an AI wrapper.

---

## Workload / Capacity Risk Decision

The original concept used the term **burnout prediction**.

The team refined this because an application-generated score should not be presented as a medical diagnosis or as certainty that a student will experience burnout.

The prototype will instead focus on:

- Workload capacity
- Workload risk
- Overloaded days
- Commitment collisions
- Load imbalance

Example:

> "Thursday is overloaded because you have approximately seven hours of estimated work but only four hours of available time."

This is preferred over:

> "You will burn out on Thursday."

The workload score should be calculated by deterministic application logic. AI may explain the result but should not invent the score.

---

## Human-in-the-Loop Decision

AI-generated tasks should not be silently inserted into the user's workload.

The scan flow should be:

1. Camera image submitted.
2. AI extracts candidate tasks.
3. SEALY displays the extracted items.
4. User reviews the information.
5. User may edit, accept, or reject individual items.
6. Only confirmed items are saved.

This improves trust, accuracy, control, safety, and explainability.

---

## Updated Technical Architecture

```text
React Native / Expo
        |
        |--------------------> Supabase
        |                       - Auth
        |                       - PostgreSQL
        |                       - Storage
        |                       - Row Level Security
        |
        |--------------------> Vercel Serverless API
                                |
                                |----> Claude API
```

### Supabase Responsibilities

- Authentication
- PostgreSQL data
- User-owned tasks
- Workspaces
- Storage
- Row Level Security

### Vercel Responsibilities

Server-side AI endpoints such as:

- `/api/scan`
- `/api/chat`
- `/api/explain`
- `/api/sow`

Sensitive credentials remain server-side.

### Claude Responsibilities

- Vision-based task extraction
- Scheme of Work extraction
- Contextual workload explanations
- Rebalancing suggestions
- SEALY conversational responses

---

## Prototype-Phase Technical Strategy

A more detailed full-stack blueprint was reviewed on 1 September 2026.

The blueprint proposed implementing a large portion of the final application during the Workshop & Prototype Phase.

The team adopted the strongest technical ideas but reduced the implementation scope to protect judging-critical ideation, impact, design, and mentor-feedback work.

### Adopted Technical Proofs

#### 1. Expo Application Scaffold

The mobile project should launch successfully on an emulator or physical device.

#### 2. Minimal Supabase Data Layer

Only the minimum data structures needed for the prototype should be implemented initially.

Priority entities:

- Profile
- Workspace
- Task

The complete production schema is deferred until it is validated and required.

#### 3. Camera Scan Technical Spike

Highest-priority technical proof:

> **Image → Vercel API → Claude Vision → Structured Task Data**

At least one realistic image should produce usable structured task information.

#### 4. Human Confirmation

Extracted tasks should be reviewed before they are saved.

#### 5. Deterministic Workload / Capacity Function

The application should calculate workload risk using known task information rather than asking the AI to invent a score.

#### 6. Explainable Workload Visualisation

Users should be able to understand why a day or workload category is overloaded.

#### 7. Constrained SEALY Explanation

If time allows, Claude should receive an existing workload result and explain it in SEALY's conversational style.

---

## Optional Prototype Technical Spikes

Optional if the core prototype is stable:

- Scheme of Work importer
- Mood and energy input
- Basic AI chat
- Realtime Kanban proof
- Basic focus timer

These are **not submission blockers**.

---

## Technical Security Decisions

### API Keys

Sensitive credentials must never be committed to GitHub.

Examples:

- `ANTHROPIC_API_KEY`
- `SUPABASE_SERVICE_ROLE_KEY`

These belong in Vercel/server environment variables.

### Expo Environment Variables

Only values designed to be exposed to the mobile application may use the `EXPO_PUBLIC_` prefix.

### Git Repository

Real `.env` files remain ignored.

A `.env.example` file may be committed with variable names but no real secret values.

---

## GitHub Documentation Strategy

The CodeNection prototype submission requires a public GitHub repository with a README containing the project overview and links to required assets.

The team will use GitHub as the central submission hub.

### Planned Repository Structure

```text
sealy-codenection-2026/
|
|-- README.md
|
|-- docs/
|   |
|   |-- ideation/
|   |   |-- SEALY_Ideation_and_Prototype_Evolution_Log.md
|   |   |-- idea-comparison.md
|   |   |-- problem-tree.png
|   |   `-- mindmap.png
|   |
|   |-- ucd/
|   |   |-- persona.md
|   |   |-- life-before-after.md
|   |   `-- user-flow.png
|   |
|   |-- mentor-feedback/
|   |   |-- mentor-01-sep10.md
|   |   `-- mentor-02-sep12.md
|   |
|   |-- architecture/
|   |   |-- system-architecture.png
|   |   |-- ai-responsibility.md
|   |   `-- technical-feasibility.md
|   |
|   `-- research/
|       `-- competitor-analysis.md
|
|-- prototype/
|   `-- README.md
|
|-- presentation/
|   `-- README.md
|
`-- app/
```

The root README remains a concise judge-facing overview. Detailed ideation evidence belongs in `/docs`.

---

## 1 September 2026 (later the same day) — Iteration 1b: Blueprint Reconciliation and Documentation Consolidation

### Previous State

Iteration 1 refined the problem statement, reduced prototype scope, separated AI responsibilities from application responsibilities, and established the prototype technical strategy.

At the start of Iteration 1b the repository contained:

- A rewritten root `README.md` (uncommitted, and truncated mid-code-block)
- A `docs/` skeleton in which nine of eleven Markdown files were empty placeholders
- This evolution log, which was the only document containing content
- No application code, no `package.json`, no Expo configuration, no Supabase files, no API layer, and no diagram assets

### New Observation

A detailed full-stack implementation blueprint carried over from the earlier planning conversation was reconciled against the Iteration 1 decisions and against the actual repository.

Two findings emerged:

1. Substantial parts of the blueprint remain valid and are the most complete technical reference the team has.
2. Several parts of the blueprint conflict with decisions the team made during Iteration 1, particularly around terminology, scope, and human confirmation.

### Decision

Reconcile the conflicts explicitly rather than silently discarding either source. Adopt what remains valid, record what was superseded and why, and keep superseded material visible as ideation evidence.

### Blueprint Elements Adopted

| Element | Status |
|---|---|
| Expo + Supabase + Vercel + Claude stack | Adopted unchanged |
| Server-side-only secrets; `EXPO_PUBLIC_` for intentionally public values | Adopted unchanged |
| Row Level Security on all user-owned tables | Adopted unchanged |
| Deterministic workload metric computed in application code, explained by AI | Adopted unchanged |
| Camera capture as the primary differentiating technical proof | Adopted unchanged |
| Seal mascot as emotional interface over a workload system | Adopted unchanged |
| Server endpoints for scan, explanation, conversation, and Scheme of Work | Adopted as target shape; none implemented |
| Full relational schema (profiles, workspaces, subjects, tasks, groups, comments, mood, habits, focus sessions, snapshots, notifications) | Retained as a future reference; prototype implements Profile / Workspace / Task only |

### Blueprint Elements Superseded by Iteration 1

| Superseded element | Replaced by | Reason |
|---|---|---|
| "Burnout score", "burnout prediction", "predicted crash day" | Workload capacity, workload risk, overloaded day, commitment collision | An application-generated number must not be presented as a medical prediction. See the Workload / Capacity Risk Decision above. |
| A product line promising to tell a student they are going to burn out | "SEALY turns scattered physical and digital responsibilities into one understandable workload picture" | The original line makes a clinical claim the team cannot support. |
| Scan results confirmed by a single bulk-accept action | Per-item review with edit / accept / reject | Conflicts with the Human-in-the-Loop Decision. Bulk acceptance reintroduces silent insertion of AI output. |
| Scheme of Work import described as the headline feature | Optional technical spike | The prototype-critical proof is generic physical-to-digital capture. Scheme of Work extraction is a strong instance of it, not a precondition. |
| Approximately thirty features scheduled for completion inside the prototype phase | Reduced prototype-critical list | Protects ideation, design, and mentor-feedback work, which carry the majority of prototype-phase judging weight. |
| Separate `sealy/` and `vercel-api/` repository roots | Single repository with `app/` alongside `docs/`, `prototype/`, `presentation/` | The submission requires one public repository serving as the central hub. |
| A specific pinned model identifier | Model selection deferred to implementation | The identifier carried in planning material does not correspond to a currently available model. No model has been pinned. |
| Academic-only persona framing | Persona spanning academic, career, social, physical, and personal load | The core insight depends on responsibilities combining across areas of life, not on academic load alone. |

### Consolidated Register of Explored and Rejected Directions

Recorded so the reasoning behind the current direction remains visible. These were genuinely considered.

| Direction explored | Outcome | Reason |
|---|---|---|
| Firebase as application backend | Rejected | Supabase covers authentication, database, storage, and access control in one service. Adding Firebase increases surface area for no gain. |
| Training a custom OCR or vision model for academic documents | Rejected | Not achievable at useful quality inside the prototype phase. Instruction design against an existing vision model reaches usable output far faster. |
| AI generating the workload score directly | Rejected | Non-deterministic and not explainable. A judge or user asking how the number was calculated must receive a concrete answer. |
| Augmented-reality workload overlay | Rejected | No problem in SEALY requires it. Camera capture already bridges the physical and digital gap. |
| Web application as the primary product | Rejected | The journey depends on the phone camera being available at the moment a physical note is seen. |
| Routing between multiple AI models by task type | Deferred | Unjustified complexity before a single-model baseline exists. |
| Broad initial feature list (Kanban, sprint views, dependencies, Pomodoro, ambient audio, habits, XP, badges, realtime collaboration) | Deferred | Retained in the product vision; outside the prototype-critical path. May be revisited in the Building Phase. |
| Presenting a workload number as a burnout probability or diagnosis | Rejected | Unsupported medical claim. |

### What Changed in the Repository

- The root `README.md` was rewritten as a judge-facing navigation hub and the truncated code block was repaired.
- The nine empty placeholder documents were written: idea comparison, persona, life before/after, AI responsibility, technical feasibility, two mentor templates, competitor positioning, and the prototype and presentation indexes.
- Every document was aligned to workload-capacity terminology.
- Feature status labels were set from repository inspection rather than from prior documentation.

### Evidence

Repository inspection on 1 September 2026 confirmed: thirteen files present, twelve Markdown plus `.gitignore`; no source files of any kind; no environment example file; no diagram assets. Every technical claim in the documentation set was written against that observation.

### Outcome

This became **Iteration 1b of SEALY**. Product direction is unchanged from Iteration 1. What changed is that the documentation now matches the repository, and the reasoning behind superseded decisions is recorded rather than lost.

### Open Questions Carried Forward

- **Competition timeline.** This log records a Building Phase of 21 September – 11 October 2026. Earlier planning material treats 13 September 2026 as the final submission deadline. These cannot both be correct and the difference materially changes prototype scope. To be confirmed against official CodeNection materials.
- **Workload metric definition.** Two formulations exist in project history and neither has been selected. See [technical-feasibility.md](../architecture/technical-feasibility.md).
- **Statistic sourcing.** Figures on Malaysian student burnout appear in earlier planning material without retrievable citations. They must be verified before use in any judge-facing document.

---


## Current Product Identity

SEALY is no longer defined as:

> A productivity app with many AI features.

The refined identity is:

> **SEALY is an intelligent workload-management companion that helps students capture, understand, visualise, and rebalance their total workload before it becomes unmanageable.**

The seal mascot provides the emotional interface.

The workload-management system provides the core value.

---

## Current Working Pitch

> **SEALY turns scattered physical and digital responsibilities into one understandable workload picture, then helps students rebalance their commitments before overload becomes unmanageable.**

This may continue evolving after mentor consultation.

---

## Current Prototype Success Criteria

Before Prototype Judging, the team should be able to demonstrate:

- [ ] Clear problem definition
- [ ] Specific target user
- [ ] Idea exploration and rejected alternatives
- [ ] Problem tree
- [ ] Ideation mindmap
- [ ] User flow
- [ ] Life-before / life-after comparison
- [ ] Complete clickable core prototype
- [ ] Workload visualisation concept
- [ ] Rebalancing flow
- [ ] Recovery flow
- [ ] Technical architecture
- [ ] AI-vs-application responsibility explanation
- [ ] Working camera-scan technical proof if feasible
- [ ] Deterministic workload/capacity proof if feasible
- [ ] Mentor #1 feedback documentation
- [ ] Visible post-mentor iteration
- [ ] Mentor #2 feedback documentation
- [ ] Final prototype iteration
- [ ] Public GitHub repository
- [ ] Viewable prototype links
- [ ] Final slides
- [ ] 3–5 minute unlisted demo video

---

## Next Step — 2 September 2026

The next documented iteration should focus on **breadth of exploration**.

Compare SEALY against several alternative solution approaches:

1. Stress diary
2. AI wellness chatbot
3. Smart task manager
4. Calendar optimisation assistant
5. Workload capacity manager

Evaluate:

- Challenge alignment
- Ability to trigger action
- Originality
- Technical feasibility
- Student usability
- Long-term usefulness

Document why the selected SEALY direction performs better than rejected alternatives.

---

## Iteration History

| Date | Iteration | Main Change |
|---|---|---|
| 31 Aug 2026 | Iteration 0 | Broad SEALY concept established |
| 1 Sep 2026 | Iteration 1 | Problem refined, scope reduced, AI/application responsibilities separated, technical prototype strategy established |
| 1 Sep 2026 | Iteration 1b | Earlier full-stack blueprint reconciled against Iteration 1 decisions; superseded directions recorded; repository documentation set written to match actual repository state |
| 2 Sep 2026 | Iteration 2 | To be documented |
| 10 Sep 2026 | Mentor Iteration | Mentor #1 consultation |
| 11 Sep 2026 | Post-Mentor Iteration | To be documented |
| 12 Sep 2026 | Mentor Iteration | Mentor #2 consultation |
| 13 Sep 2026 | Final Prototype Iteration | To be documented |

---

*This document should continue evolving throughout the Workshop & Prototype Phase. Changes, rejected ideas, failed experiments, mentor comments, and scope reductions are all part of the ideation evidence.*
