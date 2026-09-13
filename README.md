# 🦭 SEAL — Student Equilibrium & Load

> **A focus app that knows when you should not focus.**

SEAL is a student workload-understanding and intervention system for the CodeNection 2026 **Lifestyle & Personal Productivity** track. It helps a student bring scattered academic work into one place, understand whether the work still fits the time available, and decide what to do next.

The active product name is **SEAL**. **SEALY** refers only to an archived early chatbot-oriented iteration.

---

## CodeNection 2026

| | |
|---|---|
| **Problem statement** | Stress & Workload Manager |
| **Submission deadline** | 13 September 2026, 11:59 PM |
| **Current deliverable state** | Ideation + clickable Figma prototype + documentation |
| **Application code** | Not implemented in this repository |
| **Figma** | https://www.figma.com/design/Y2ce2KYSTXDkNBqLAMcfaF/ |

The prototype is intentionally a **simulated interaction design**. It demonstrates the product logic and flows but does not claim live OCR, calendar synchronization, app blocking, AI agents, or workload calculation are already implemented.

---

## The problem we narrowed to

Students often already have the information they need, but it is fragmented across calendars, assignment PDFs, screenshots, chat messages, course portals, email, and memory.

Before they can make a good decision, they first have to reconstruct:

- what work exists;
- how long it may take;
- which deadline matters first;
- how much usable time is actually left.

That creates the central SEAL question:

> **How much work do I still need to do, how much time do I realistically have, and what should I do next?**

The product therefore does not need five mysterious scores on the home screen. The core model is much simpler:

```text
WORK TO FINISH
      vs
TIME / CAPACITY LEFT
      ↓
Does the plan fit?
      ↓
FOCUS / ADJUST / TAKE A BREAK
```

Mental state, energy, social commitments, and errands can still provide context, but they are **supporting signals**, not separate user-facing engines.

---

## What SEAL does

### 1. Import your work

SEAL is designed around **low input, high output**. Instead of expecting students to rebuild their academic life manually, the concept accepts information from places where it already exists:

- camera / photo of a syllabus or assignment brief;
- gallery screenshot or saved document;
- explicit Share-to-SEAL from another app;
- Google Calendar;
- email;
- copied / pasted text as a fallback.

Future exploration includes Telegram-assisted intake and authorised headless-browser agents. These are **not MVP claims**.

### 2. Structure and confirm

Imported information is converted into candidate tasks/events with fields such as title, course, deadline, estimated effort, source and optional subtasks.

SEAL follows a **human-in-the-loop** rule:

> The system drafts the structure; the student confirms, edits or ignores it.

### 3. Compare workload with time left

The clearest prototype example is:

```text
Work to finish:  3h 35m
Time left today: 2h 40m
Shortfall:          55m
```

The `3h 35m` is not an unexplained score. In the current prototype it is made up from visible work items, such as:

- ISP640 Project Plan — 90 min
- ICT652 presentation preparation — 65 min
- ASC486 Group Project — 60 min

The prototype data is representative and uses uploaded course / assignment material as realistic demo context. It is not live-computed data.

### 4. Recommend the next action

Internally the project still uses the three-mode model:

- **FOCUS** — the work fits; start or continue.
- **REBALANCE** — the plan does not fit; change the plan.
- **RECOVER** — there is room to stop and recovery is more appropriate.

In the student-facing UI, Mentor #2 feedback led us to simpler language:

- **Focus** → **Focus / Focus Now**
- **Rebalance** → **Adjust My Plan**
- **Recover** → **Take a Break**

The internal logic can be sophisticated; the screen should be immediately understandable.

---

## Mentor-driven prototype changes

### Mentor #1 — low-input / high-output

Mentor #1 challenged the team to make the user do less work before SEAL becomes useful. That led to:

- OCR/photo capture being revisited as an **input mechanism**, not the whole product;
- task decomposition exploration;
- multi-source intake;
- Telegram / agentic / headless-browser exploration as future work;
- recommendations that the user confirms rather than forced mode switching.

### Mentor #2 — make the core obvious

Mentor #2 (Janelle) challenged the product to be understandable without the team standing beside the screen explaining it. The latest Figma revision therefore:

- places **Work to finish (3h35)** beside **Time left today (2h40)**;
- makes **55 min short** the urgent conclusion;
- shows the actual work creating the total;
- renames user-facing Rebalance language to **Adjust**;
- adds task/course/lecturer/duration context to Plan;
- adds a real **Today / Week** calendar view;
- reduces task adjustment choices to **Keep / Add / Move / Defer**;
- gives **Add** five generated plan alternatives;
- demonstrates drag-style **Move** with overlap warning;
- makes **Defer** ask whether the deadline changed or the task is simply no longer urgent;
- clarifies Focus app behaviour: **only explicitly selected apps are paused; everything else remains available**;
- creates real **7 Days / 30 Days / Semester** insight screens instead of a “coming later” note;
- simplifies the five-load terminology into direct student language.

Full record: [Mentor #2 feedback](docs/mentor-feedback/mentor-02-sep12.md).

---

## Current prototype journey

```text
IMPORT YOUR WORK
      ↓
EXTRACT + STRUCTURE
      ↓
USER CONFIRMS / EDITS
      ↓
TODAY / WEEK PLAN
      ↓
WORK TO FINISH vs TIME LEFT
      ↓
55 MIN SHORT?
      ↓ yes
ADJUST MY PLAN
      ↓
KEEP / ADD / MOVE / DEFER
      ↓
CONFIRM PLAN
      ↓
FOCUS
      ↓
TAKE A BREAK when appropriate
```

The Island and seal mascot are the **visual / emotional layer**. They support the decision; they are not the calculation itself.

---

## Adjustment actions

| Action | Current prototype behaviour |
|---|---|
| **Keep** | Leave the task unchanged; confirmation screen with mascot |
| **Add** | Ask SEAL for another arrangement; five prototype plan variants are available |
| **Move** | Drag the task into another calendar slot; overlap produces a warning / confirmation |
| **Defer** | Postpone because the deadline changed or the task is no longer urgent |

The system suggests. The student retains decision authority.

---

## Plan and Insights

The latest prototype includes:

- a **Today** academic timeline;
- a phone-style **Week** calendar;
- course, lecturer, duration and deadline context;
- a task-detail view linked from the plan;
- 7-day, 30-day and semester Insight views with different period-level data.

Academic PDFs uploaded during prototype development are used as realistic **demo content sources**, not as research evidence about student behaviour.

---

## Intended technical architecture

No application implementation is claimed. The current intended stack is:

| Layer | Intended technology |
|---|---|
| Mobile UI | React Native + Expo + TypeScript |
| Backend / database | Supabase + PostgreSQL |
| Auth / data protection | Supabase Auth + Row Level Security |
| Calendar source | Google Calendar API, read-only first |
| Local app state | Zustand |
| Server cache / fetching | TanStack Query |
| Notifications | Expo Notifications |
| OCR / extraction | OCR service / on-device or managed text recognition; exact provider still to be chosen |
| Recommendation engine | Deterministic rule-based MVP |
| Optional AI assistance | Task decomposition, ambiguous text structuring, explanation; never the sole authority |

```text
Camera / Gallery / Share / Calendar / Email
                    ↓
             Candidate Intake
                    ↓
        Normalize + optional decompose
                    ↓
            User confirmation
                    ↓
           Structured workload
                    ↓
       Workload / Capacity Engine
                    ↓
      Focus / Adjust / Take a Break
                    ↓
              Island / Insights
```

Future authorised browser agents and Telegram adapters sit **before Candidate Intake** and use the same normalized data model.

---

## AI and automation boundary

SEAL must not pretend that AI has perfect knowledge of the student's life.

**Application logic should own:**

- date/time arithmetic;
- effort totals;
- available-time calculation;
- overlap constraints;
- workload shortfall;
- rule-based recommendation state;
- permissions and persistence.

**AI may assist with:**

- interpreting OCR text;
- turning an ambiguous item into a candidate task;
- suggesting subtasks;
- explaining a deterministic result in plain language.

Everything inferred remains editable and confirmable.

See [AI responsibility](docs/architecture/ai-responsibility.md).

---

## Repository map

```text
sealy-codenection-2026/
├── README.md
├── README-1.md                  # extended submission-oriented technical notes
├── docs/
│   ├── PROGRESS.md
│   ├── architecture/
│   ├── ideation/
│   ├── mentor-feedback/
│   ├── research/
│   └── ucd/
├── prototype/
└── presentation/
```

The repository name is retained for continuity even though the active product name is **SEAL**.

---

## Important honesty rules

- SEAL does **not** diagnose stress, burnout or mental-health conditions.
- The current Figma values are **representative prototype data**, not live calculations.
- OCR, Calendar sync, app blocking and agentic collection are **not implemented** merely because the flow is designed.
- The five original load dimensions remain ideation context, not five scientifically validated scores.
- No imported academic document is proof that a user behaves a certain way; those documents only make the demo data realistic.
