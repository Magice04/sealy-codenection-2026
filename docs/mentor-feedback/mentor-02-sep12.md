# Mentor Consultation #2 — Janelle: Make the Core Obvious

> **Status: feedback recorded and applied to the Figma prototype.**
>
> The repository keeps the existing `mentor-02-sep12.md` filename for continuity. The latest follow-up prototype feedback with Janelle was captured on **13 September 2026**. If the team needs the exact date/time of the first Mentor #2 touchpoint for the official form, confirm it separately rather than guessing here.

## Mentor

**Janelle**

## What we showed

- Island / Home dashboard
- workload/time card
- Focus / Rebalance / Recover framing
- Plan screens
- Rebalance/adjustment flow
- Focus app allow/block configuration
- Insights
- latest prototype wording after Mentor #1

## Main feedback

### 1. The core was still too hard to understand

The five-load explanation (Mental, Time, Physical, Social, Errands) required too much explanation. Janelle pushed the team to make the product more directly related to the core decision.

**Decision:** five dimensions remain contextual signals, but the primary UI becomes:

```text
Work to finish
vs
Time left / realistic capacity
```

### 2. Simplify titles and wording

Terms such as Rebalance, schedule pressure and several load labels sounded like system terminology rather than student language.

**Decision:** use simple user-facing wording:

- Rebalance → **Adjust My Plan**
- Recovery → **Take a Break**
- Required workload → **Work to finish**
- Available capacity → **Time left today**
- unexplained “schedule pressure” → a concrete shortfall such as **55 min short**

### 3. Home should lead with urgency and explain the number

The old card showed “Time free today” and “Work due today”, but the relationship was not immediately obvious.

The mentor wanted the urgent shortfall to be prominent and the user to know **which work creates the number**.

**Applied change:** Home now shows:

```text
Work to finish     3h 35m
Time left today    2h 40m
55 min short
```

A work-preview card shows the tasks behind the 3h35 total.

### 4. The plan needs actual task context

If the screen says “3h35 of work”, the student should be able to see what that means: subject/work, duration and deadline, not a generic total.

**Applied change:** Plan/Task Detail now contains realistic course context and links to the calendar flow.

### 5. Adjustment options were too complicated

The earlier five-option task adjustment model was reduced to exactly four options:

| Option | Meaning |
|---|---|
| **Keep** | Do not change this task |
| **Add** | Ask SEAL for another generated arrangement |
| **Move** | Move the task to another slot |
| **Defer** | Postpone it / update changed urgency or deadline |

### 6. Keep should clearly mean “no change”

**Applied change:** Keep opens a confirmation state with the mascot and tells the student that nothing was changed, with a route back to the plan.

### 7. Add should reduce user work, not create more editing

The student should not have to manually rebuild the plan.

**Applied change:** Add now demonstrates **five alternative plan arrangements**. The student cycles through them and confirms one.

### 8. Move should look like a familiar calendar interaction

Janelle wanted a phone-calendar mental model rather than another abstract form.

**Applied change:** Move uses a Google-Calendar-inspired week grid with a drag interaction. If a placement overlaps another item, SEAL shows a warning and asks for confirmation. The current prototype rule allows at most two simultaneous items.

### 9. Defer needs a reason

“Defer” alone is ambiguous.

**Applied change:** the prototype asks whether:

- the deadline changed — then the user updates/places it again; or
- the task is no longer urgent — then it can move to a later acceptable slot.

### 10. App lock behaviour was confusing

The mentor asked: if only some apps are listed, are all the others blocked or allowed?

**Decision:** predictable allow-by-default behaviour.

> **Only apps explicitly selected by the student are paused during Focus. Everything else remains available.**

The wording “Lock out apps” was replaced by clearer focus setup copy.

### 11. Plan needs a Week view

The Today/Week toggle was present but Week was not demonstrable.

**Applied change:** a clickable phone-style Week calendar was created with course blocks, times, lecturer context and an urgent deadline preview.

### 12. Insights must be demonstrable across periods

The 30 Days and Semester tabs previously led to a note instead of real screens.

**Applied change:** separate **7 Days**, **30 Days** and **Semester** prototype views now exist with period-specific example metrics/content.

### 13. Use realistic academic information consistently

Janelle asked for Plan/Insights to feel like a real student's data rather than disconnected placeholders.

**Applied change:** the prototype uses information from course/assignment PDFs supplied by the team to make course names, lecturer context and assessment/deadline examples coherent.

Important: these PDFs are **demo content sources**, not user-research evidence.

### 14. Stronger input framing

The product should be easy to explain as:

> **Students can bring information in from where it already exists, and SEAL turns it into something actionable.**

**Applied change:** Capture is now framed as **Import your work**, including Camera, Gallery, Share to SEAL, Calendar, Email and pasted text.

## Before → after summary

| Before | After |
|---|---|
| five front-facing load dimensions | one clear workload/time relationship + contextual signals |
| Time free today / Work due today | Work to finish / Time left today |
| Schedule pressure · Very high | 55 min short |
| Rebalance your plan | Adjust your plan |
| generic work total | visible tasks that create the total |
| 5 adjustment choices | Keep / Add / Move / Defer |
| Add means more manual editing | Add = generate another arrangement |
| abstract Move | familiar week-calendar drag model |
| ambiguous blocking | only selected apps are paused |
| Today toggle with no Week demo | real Week prototype screen |
| 30 Days / Semester note | real period screens |

## Core design principle after Mentor #2

> **The intelligence can stay underneath. The screen must explain itself.**

Or, in product terms:

> **The student should not have to analyse SEAL's analysis.**

## Evidence of change

Latest Figma design:

https://www.figma.com/design/Y2ce2KYSTXDkNBqLAMcfaF/

Key updated frames include:

- `ISLAND / Dashboard`
- `PLAN / Today`
- `PLAN / Week`
- `PLAN / Rebalance` (internal frame name; UI says Adjust)
- `PLAN / Keep Confirmation`
- `PLAN / Add Option 1–5`
- `PLAN / Move Task`
- `PLAN / Defer Task`
- `FOCUS / Lock-In Setup`
- `CAPTURE / Source Picker`
- `CAPTURE / Extracted Result`
- `INSIGHTS / Dashboard`
- `INSIGHTS / 30 Days`
- `INSIGHTS / Semester`

## Comparison with Mentor #1

| Theme | Mentor #1 | Mentor #2 / Janelle | Combined direction |
|---|---|---|---|
| User effort | user should do less input work | user should do less interpretation work | **low input + low cognitive friction** |
| OCR | useful input mechanism | show what work it creates | import must lead to understandable action |
| Automation | system structures/proposes | system should generate useful options | automation does repetitive planning; user confirms |
| Core model | retain workload/capacity reasoning | make that reasoning visibly simple | work to finish vs time left |
| UI | simple confirmation | simpler wording and fewer choices | one obvious next action |
| Control | recommend, do not force | clarify Keep/Move/Defer and app rules | human-in-the-loop throughout |

## Remaining follow-up questions

- Does a first-time user understand **3h35 vs 2h40 → 55m short** without narration?
- Is “Add” the best final label for “generate another plan”, or should the team rename it before submission? The current prototype follows the team's requested four labels.
- Are the 30-day/semester examples enough for judges, or should only one period be shown in the final demo to save time?
- Which 4–8 screenshots best show the mentor-driven improvement?

## Related documents

- [Mentor #1](mentor-01-sep10.md)
- [Evolution Log](../ideation/SEAL_Ideation_and_Prototype_Evolution_Log.md)
- [Prototype Overview](../../prototype/README.md)
