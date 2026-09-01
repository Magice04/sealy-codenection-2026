# 🦭 SEALY

> **See your load. Rebalance before overload.**

SEALY is an intelligent workload-management companion that helps university
students capture, understand, visualise, and rebalance their total workload
before it becomes unmanageable.

---

## CodeNection 2026

| | |
|---|---|
| **Track** | Lifestyle & Personal Productivity |
| **Problem Statement** | Stress & Workload Manager |
| **Phase** | Workshop & Prototype Phase |
| **Prototype period** | 31 August – 13 September 2026 |
| **Current status** | Ideation and documentation established; application development not yet started |

---

## The Problem

University students carry responsibilities across many areas of life at once —
academic work, career preparation, extracurricular commitments, personal
errands, physical wellbeing, and rest.

These commitments are fragmented across calendars, messaging apps, task
managers, sticky notes, printed academic material, and memory. No single one of
those sources holds the complete picture, and none of them are connected.

The result is that students keep accepting commitments without a clear view of
what they have already taken on.

**The core insight:**

> No individual responsibility necessarily looks unmanageable.
> The problem only becomes visible when all responsibilities are considered together.

---

## Our Hypothesis

> If students can see their total workload across different areas of life and
> receive actionable rebalancing suggestions before major commitments collide,
> they can make better workload decisions and reduce the risk of becoming
> severely overloaded.

---

## What SEALY Does

SEALY is a workload system, not a task list. It:

1. **Captures** responsibilities from physical and digital sources
2. **Extracts** candidate tasks from photographed notes and academic material using AI
3. **Confirms** every extracted item with the user before saving anything
4. **Aggregates** commitments across all areas of life into one view
5. **Compares** estimated effort against available capacity
6. **Identifies** overloaded days and commitment collisions
7. **Explains** which commitments produce the pressure
8. **Proposes** specific rebalancing the user approves
9. **Protects** time for recovery

SEALY reports **workload**, not health. It does not diagnose or predict burnout.

---

## Core Journey

```text
Capture  →  Understand  →  Visualise  →  Rebalance  →  Recover
```

---

## Key Differentiator

**Physical-to-digital workload capture.**

```text
Physical notes / whiteboards / academic documents
        ↓
     Camera
        ↓
   AI extraction
        ↓
Structured candidate tasks
        ↓
  Human confirmation
        ↓
  Workload system
```

Most productivity tools require the workload to already be digital, then display
it as a list of dates. Neither assumption holds for this user. A significant part
of a student's real load exists only on paper or in messages, and a date without
an effort estimate cannot show whether a week is actually feasible.

SEALY closes both gaps: it reduces the cost of capturing physical commitments,
and it reasons about effort against available capacity.

The seal mascot is the emotional and conversational interface.
The workload-management system is the product.

---

## Target User

**Haziq**, 21, a final-year Computer Science student balancing a Final Year
Project, assignments, midterm revision, internship preparation, club
responsibilities, errands, exercise, social commitments, and rest — spread
across WhatsApp, Google Calendar, Notion, sticky notes, printed material, and
memory.

📄 [Read the full persona](docs/ucd/persona.md) ·
📄 [Life before and after SEALY](docs/ucd/life-before-after.md)

---

## Prototype

**Status: not yet built.** No application code, design file, or clickable
prototype exists in this repository at present.

| Artefact | Status |
|---|---|
| Clickable prototype | Coming soon |
| Demo video | Coming soon |
| Screenshots | Coming soon |

📄 [Prototype scope, planned screens, and technical proof status](prototype/README.md)

---

## Architecture & Technology

Intended stack. **No implementation exists yet** — see the feasibility document
for verified status.

| Layer | Technology |
|---|---|
| Mobile | React Native + Expo |
| Database, auth, storage | Supabase (PostgreSQL, Row Level Security) |
| Server / AI gateway | Vercel serverless functions |
| AI | Claude API |
| Notifications | Expo Notifications |

```text
React Native / Expo
        │
        ├──────────────►  Supabase
        │                 Auth · PostgreSQL · Storage · Row Level Security
        │
        └──────────────►  Vercel serverless API
                                │
                                └──────►  Claude API
```

Server credentials never enter the mobile bundle. The application calls SEALY's
own endpoints, which verify the user's session before any AI call.

📄 [Technical feasibility, verified status, and risks](docs/architecture/technical-feasibility.md)

---

## AI Responsibility

SEALY uses AI narrowly and deliberately.

| AI handles | Application logic handles |
|---|---|
| Image understanding | Authentication and permissions |
| Candidate task extraction | Database persistence and access control |
| Natural-language interpretation | Deadlines and date arithmetic |
| Explaining a computed result | **Workload and capacity calculation** |
| Rebalancing suggestions | Scheduling constraints and validation |
| SEALY's conversational voice | Task state and business rules |

**The critical line:** AI never computes the workload figure. Application code
computes it; AI is given the result and asked to explain it. Extracted items are
never saved without per-item human confirmation.

📄 [Full AI responsibility model](docs/architecture/ai-responsibility.md)

---

## Ideation & Evolution

The evolution log is the primary record of how SEALY's direction developed,
including directions that were explored and rejected.

- 📄 [Ideation and Prototype Evolution Log](docs/ideation/SEALY_Ideation_and_Prototype_Evolution_Log.md)
- 📄 [Alternative solution directions and decision rationale](docs/ideation/idea-comparison.md)
- Problem tree diagram — Coming soon
- Mind map — Coming soon
- User flow diagram — Coming soon
- System architecture diagram — Coming soon

| Date | Iteration | Main change |
|---|---|---|
| 31 Aug 2026 | Iteration 0 | Broad SEALY concept established |
| 1 Sep 2026 | Iteration 1 | Problem refined; scope reduced; AI and application responsibilities separated |
| 1 Sep 2026 | Iteration 1b | Earlier blueprint reconciled; superseded directions recorded; documentation aligned to repository reality |

---

## User-Centred Design

- 📄 [Persona — Haziq](docs/ucd/persona.md)
- 📄 [Life before and after SEALY](docs/ucd/life-before-after.md)
- 📄 [Competitor and positioning analysis](docs/research/competitor-analysis.md)

---

## Mentor Feedback

**No mentor session has taken place yet.** Two consultations are scheduled; the
documents below are prepared templates containing questions, not feedback.

- 📄 [Mentor #1 — 10 September 2026](docs/mentor-feedback/mentor-01-sep10.md) — *not yet held*
- 📄 [Mentor #2 — 12 September 2026](docs/mentor-feedback/mentor-02-sep12.md) — *not yet held*

---

## Presentation

**Not started.** Slide deck, demo video, and pitch notes are pending.

📄 [Presentation index](presentation/README.md)

---

## Repository Structure

```text
sealy-codenection-2026/
├── README.md                    ← you are here
├── docs/
│   ├── ideation/                ← evolution log, alternative directions
│   ├── ucd/                     ← persona, before/after
│   ├── architecture/            ← AI responsibility, technical feasibility
│   ├── mentor-feedback/         ← consultation records (templates)
│   └── research/                ← competitor positioning
├── prototype/                   ← prototype scope and status
└── presentation/                ← slides, video, pitch notes (pending)
```

An `app/` directory will be added when application development begins.

---

## Current Status

Honest summary as of **1 September 2026**:

| Area | Status |
|---|---|
| Problem definition | Established |
| Target user / persona | Documented (design persona; not validated with real students) |
| Idea exploration and rejected alternatives | Documented |
| Architecture and AI responsibility model | Specified |
| Technical feasibility assessment | Documented |
| Visual diagrams (problem tree, mind map, user flow) | Not started |
| Application code | **Not started** |
| Clickable prototype | Not started |
| Mentor consultations | Scheduled, not yet held |
| Presentation materials | Not started |

**Nothing in this repository is implemented.** Every technical claim above
describes intended design and is labelled accordingly.

---

## Terminology

SEALY uses **workload capacity**, **workload risk**, **overloaded day**,
**commitment collision**, and **load imbalance**.

It deliberately avoids burnout prediction, burnout scores, and crash prediction.
An application-generated figure must not be presented as a medical assessment.

A representative SEALY explanation:

> "Thursday contains approximately 7 hours of estimated work while you have
> around 4 hours of available capacity."

Rather than:

> "You will burn out on Thursday."
