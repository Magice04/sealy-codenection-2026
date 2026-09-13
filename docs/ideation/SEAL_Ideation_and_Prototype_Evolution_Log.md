# SEAL — Ideation and Prototype Evolution Log

This is the durable chronology of how SEAL evolved. It intentionally preserves ideas that were later dropped so the final concept does not look reverse-engineered.

## Naming

- **SEALY** = archived early chatbot-oriented concept.
- **SEAL — Student Equilibrium & Load** = active product direction.

## Challenge brief

Track: Lifestyle & Personal Productivity

Problem statement: Stress & Workload Manager

The challenge asks for more than tracking/reporting: the product should help students rebalance what they carry and push them toward recovery before overload becomes severe.

## Iteration 0 — broad student-load exploration

Initial exploration treated student stress as a broad productivity/wellbeing problem. This was too wide to produce a clear mechanism.

### Idea 01 — SEALY chatbot companion

**Hypothesis:** a conversational companion can help students reflect and manage workload.

**Dropped as core because:** the student has to talk/type before receiving basic workload information, and a chatbot is not itself a workload solution.

**Kept:** the seal character as an emotional interface.

## Idea 02 — Photo / OCR task capture

**Hypothesis:** photograph a syllabus/whiteboard/assignment and convert it to tasks.

**Initial decision:** dropped as the whole product because OCR-to-task solves capture, not workload feasibility.

**Important later change:** Mentor #1 caused this idea to be revisited as a **low-friction input layer**.

## Idea 03 — holistic five-load score

Five areas were explored:

- Mental
- Time
- Physical
- Social
- Errands

**Useful discovery:** academic load is not the whole student experience.

**Problem:** a single weighted score across unrelated dimensions has no defensible shared unit and is difficult for a student to interpret.

**Decision:** do not build a universal composite stress/load score. Keep the dimensions only as context.

This decision became even stronger after Mentor #2.

## Idea 04 — Focus / Pomodoro

**Useful:** helps a student begin and continue work.

**Limitation:** assumes doing more work is always the answer.

## Idea 05 — Strict Lock-In

**Useful:** reduce selected distractions.

**Limitation:** punitive if overused; native blocking is platform-specific; still does not solve an impossible schedule.

**Later simplification:** the Focus UI now follows a clear rule — only apps explicitly selected by the student are paused; everything else stays available.

## Idea 06 — Behaviour-Aware Focus

The team explored start delays, interruptions and focus patterns.

This created the key turning point:

> **Even perfect focus cannot fix an impossible schedule.**

## Idea 07 — Capacity + Rebalance Engine

This became the core reasoning model.

Instead of asking “is the student focused?”, first ask:

> **Does the work actually fit?**

Prototype example:

```text
Work to finish = 3h35
Time left = 2h40
Shortfall = 55m
```

If the student is missing 55 minutes, another Pomodoro timer cannot solve it.

## Idea 08 — Recovery + Balance

The team then found a second assumption: even when work fits, “keep working” may not be the best answer.

This produced three internal interventions:

```text
FOCUS
REBALANCE
RECOVER
```

Later UI simplification:

```text
FOCUS
ADJUST MY PLAN
TAKE A BREAK
```

## Idea 09 — Island + Seal

The Island became the visual expression of the current plan/state, while the seal remained the companion.

**Design rule:** gamification must reward sustainable balance, not endless task grinding.

## First convergence — SEAL

The initial final concept became:

```text
Tasks + Calendar + context
        ↓
Load / Capacity Engine
        ↓
Focus / Rebalance / Recover
        ↓
Island + Seal
```

At this stage, the engine was stronger than the input experience.

---

# Mentor Iteration 1 — Reduce user input effort

## Mentor #1 challenge

The student still had to do too much before the capacity engine had useful data.

The mentor pushed the team toward:

- OCR/photo;
- task understanding before manual organization;
- task decomposition;
- Telegram/API possibilities;
- headless-browser/agentic exploration;
- narrow scope;
- suggest, do not force;
- low learning cost.

## New design question

> **How much useful workload understanding can SEAL create from the smallest possible amount of student effort?**

## Post-Mentor #1 flow

```text
LOW-FRICTION SOURCES
Camera / Gallery / Calendar / Share / Email
               ↓
        Candidate Intake
               ↓
      Extract + Structure
               ↓
 Optional Task Decomposition
               ↓
       User Confirmation
               ↓
        Load / Capacity Engine
               ↓
 Focus / Rebalance / Recover
```

Manual input was demoted to fallback.

## Human-in-the-loop principle

SEAL does repetitive interpretation/planning; the student keeps authority.

Examples:

- extracted task → confirm/edit/ignore;
- suggested subtasks → edit;
- plan change → accept/change/dismiss;
- mode recommendation → user can override.

## Agentic exploration boundary

Telegram and authorised headless-browser sources were recorded as **future** directions. They are not MVP implementation claims.

---

# Mentor Iteration 2 — Reduce interpretation effort

Mentor #2 / Janelle reviewed the prototype and identified a different problem:

> The engine may make sense internally, but the user still has to learn too much terminology before the screen makes sense.

## Feedback theme 1 — five loads were too prominent

The user should not need to understand Mental Load, Physical Load, Social Load, Errand Load and Time Load as five separate calculated scores.

### Decision

Use a concrete core:

```text
Work to finish
vs
Time left today
```

Mental state, energy, commitments and errands remain context.

## Feedback theme 2 — explain the number

The old top card did not make the relationship between time/work obvious.

### Applied prototype change

```text
Work to finish     3h35
Time left today    2h40
55 min short
```

A visible list explains which tasks create the 3h35 total.

## Feedback theme 3 — simpler actions

“Rebalance” was replaced in the user-facing interface with **Adjust My Plan**.

Task actions were reduced to:

1. Keep
2. Add
3. Move
4. Defer

### Keep

Confirmation that nothing changed.

### Add

Generate another arrangement. Five fixed prototype variants demonstrate the intended experience.

### Move

Phone-calendar drag model + overlap warning.

### Defer

Ask whether the deadline changed or the item is not urgent anymore.

## Feedback theme 4 — Plan needs realistic context

The Plan now shows course/task names, lecturer/duration/deadline context and a Week calendar.

Academic PDFs supplied by the team were used as **prototype fixtures**, not user research.

## Feedback theme 5 — Focus app behaviour must be predictable

Current UX rule:

> Only selected apps are paused. Everything else remains available.

## Feedback theme 6 — Insights must actually show 30 Days / Semester

Separate prototype screens were created for:

- 7 Days
- 30 Days
- Semester

## New design principle

Mentor #1 reduced **input effort**.

Mentor #2 reduced **interpretation effort**.

Together:

> **Low input. Clear output. Human control.**

---

# Current final SEAL model

```text
IMPORT YOUR WORK
        ↓
STRUCTURE / OPTIONAL DECOMPOSE
        ↓
CONFIRM
        ↓
PLAN (TODAY / WEEK)
        ↓
WORK TO FINISH vs TIME LEFT
        ↓
RECOMMEND
        ↓
FOCUS / ADJUST / TAKE A BREAK
        ↓
ISLAND + INSIGHTS
```

## Current product boundaries

### Core

- workload effort
- deadline/urgency
- time available
- visible shortfall
- user-approved plan adjustment

### Context

- energy
- mental overwhelm/check-in
- social commitments
- errands
- focus history

### Experience layer

- seal mascot
- island
- insights

### Future source adapters

- Telegram
- authorised supported-site browser agent
- richer sharing integrations

## Current demo data

```text
ISP640 Project Plan             90m
ICT652 presentation prep        65m
ASC486 Group Project            60m
                               ----
Work to finish                3h35
Time left today               2h40
Shortfall                       55m
```

The values are fixed prototype examples.

## Current MVP / stretch / future framing

### MVP concept

- photo/OCR import
- Calendar read-only
- candidate confirmation
- structured task/event model
- transparent workload/time arithmetic
- Focus / Adjust / Take-a-Break recommendation
- Today / Week Plan
- basic Island / Insights

### Stretch

- richer decomposition
- Share-to-SEAL
- Telegram bot/API
- behaviour insights
- Desk Presence

### Future

- supported-site browser agent
- native app blocking
- system-wide usage
- wearables
- advanced personal agent

## What has been rejected or constrained

- chat-first app as the core;
- OCR as the entire product;
- universal five-load composite score;
- “AI calculates stress” framing;
- silent automatic schedule rewriting;
- unrestricted web/message access;
- hard dependency on native app blocking.

## Final product statement

> **SEAL helps a student bring scattered work into one understandable plan, see when the work no longer fits the time available, and take the next appropriate action before simply pushing harder.**
