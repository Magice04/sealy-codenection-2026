# Persona — Haziq

> **Status:** Design persona, Iteration 1b (1 September 2026).
>
> **Evidence note:** Haziq is a composite design persona constructed by the team to keep design decisions anchored to a specific person. He is **not** derived from interviews, surveys, or field research, and no such research has been conducted. Scenarios and dialogue below are labelled as illustrative. Where a detail has not been established by the team, it is marked *undetermined* rather than invented.

---

## Snapshot

| Field | Value |
|---|---|
| Name | Haziq |
| Age | 21 |
| Stage | Final-year Computer Science student |
| Institution | *Undetermined* — deliberately unspecified |
| Living situation | *Undetermined* |
| Primary device | Smartphone |

The institution is left unspecified on purpose. The problem SEALY addresses is not specific to one university, and naming one would imply research the team has not done.

---

## What Haziq Is Actually Carrying

His responsibilities span five areas of life. This spread is the point of the persona.

**Academic**
- Final Year Project — long-running, self-directed, no weekly external deadline forcing progress
- Course assignments with fixed submission dates
- Midterm revision

**Career**
- Internship preparation — applications, technical practice, interviews

**Extracurricular**
- Club responsibilities and the coordination they generate

**Personal and domestic**
- Groceries
- Laundry
- Errands

**Physical and recovery**
- Exercise
- Social commitments
- Rest

---

## The Core Insight

> No single item on this list is unmanageable. Any one of them, in isolation, is an ordinary week.
>
> The problem is that they are never in isolation.

This is the single most important thing about Haziq, and it is what separates SEALY from a task manager. A task manager shows him a list where every row looks equally survivable. Nothing in that view tells him that this particular Thursday is the one where four of these collide.

His Final Year Project deserves particular attention. It has no weekly deadline, so it is always the thing that can be postponed — which means it is always postponed, until it cannot be.

---

## How He Manages It Today

| Tool | What lives there | Failure mode |
|---|---|---|
| WhatsApp | Group project coordination, club logistics, informal deadline changes | Commitments arrive as messages and are never transcribed anywhere |
| Google Calendar | Fixed, scheduled events — classes, meetings | Contains scheduled time, not effort. An entry does not say how long the work takes |
| Notion | Structured notes, sometimes task lists | Requires deliberate maintenance; goes stale under pressure, exactly when needed most |
| Sticky notes | Short-term reminders at the desk | Physically bounded — visible only when he is at the desk |
| Printed academic material | Assessment schedules, handouts, briefs | Never enters any digital system at all |
| Memory | Everything not captured above | Degrades under load |

**The structural problem:** no single one of these holds the complete picture, and none of them talk to each other. Building an accurate view of his own workload would require Haziq to manually consolidate six sources — an effort he is least likely to make during the weeks he most needs it.

---

## Frustrations

1. **No aggregate view.** He can see any individual commitment. He cannot see the sum.
2. **Effort is invisible.** His calendar shows a free Wednesday afternoon. It does not show that the assignment due Thursday needs six hours.
3. **Capture friction.** Turning a printed assessment schedule into calendar entries is fifteen minutes of typing. It rarely happens.
4. **Overload is recognised late.** He typically discovers a week is unmanageable while inside it, when the remaining options are all bad.
5. **Commitments accepted in isolation.** Agreeing to a club task on Monday is easy, because at that moment he is not thinking about Thursday.
6. **Recovery is unprotected.** Rest, exercise, and social time are the first things sacrificed, because they are the only items with no external deadline.

---

## Needs

| Need | What it implies for SEALY |
|---|---|
| Capture without friction | Camera-based capture from physical sources |
| One consolidated picture | A single workload view across all five life areas |
| See effort, not just events | Estimated effort as a first-class property of a task |
| Advance visibility of collisions | Identify overloaded days before they arrive |
| Understand the cause | Explain which commitments produce the overload |
| Concrete options | Specific rebalancing proposals, not general advice |
| Retain control | Nothing changes without his approval |
| Protect recovery | Treat rest as a commitment, not as leftover time |

---

## Goals

- **Immediate:** get through the current week without a collision he did not see coming
- **Semester:** complete the Final Year Project without it consuming everything else at the end
- **Ongoing:** keep exercise, rest, and social contact from being permanently displaced
- **Underlying:** make commitment decisions with knowledge of what he has already committed to

---

## Behaviour Relevant to Design

- **Phone-first.** Decisions are made away from a desk. The physical-to-digital capture step must work with one hand while standing.
- **Low tolerance for setup.** He has abandoned productivity tools before because the configuration cost exceeded the benefit. SEALY must be useful before it is fully populated.
- **Sceptical of automation acting on his behalf.** He will not accept an app silently rearranging his week. This is why human confirmation is a hard requirement rather than a nicety.
- **Under load, he stops maintaining tools.** Any design that requires diligent upkeep fails at exactly the moment it matters.

---

## Illustrative Scenario

> *The following is a constructed scenario written by the team to communicate the problem. It is not a transcript and not a real quote.*

It is Monday. A club member asks Haziq to prepare slides by Thursday. He checks his calendar, sees Wednesday evening is free, and agrees.

He is not wrong about Wednesday evening. He is wrong about Thursday — his database assignment is due, his Final Year Project supervisor meeting was moved earlier in a WhatsApp message he read but did not record, and the internship technical interview he has been postponing preparation for is Friday morning.

None of these facts were available to him in one place at the moment he said yes.

He finds out on Wednesday night.

---

## The SEALY Opportunity

At the moment Haziq is asked to take on the slides, SEALY can show him that Thursday already holds roughly seven hours of estimated work against roughly four hours of available capacity, that the collision is driven by the assignment and the moved supervisor meeting, and that the slides could move to Saturday without affecting anything else.

The decision stays his. What changes is that he makes it with the full picture, on Monday, rather than discovering it on Wednesday night.

That is the entire product, stated as one moment in one person's week.

---

## Deliberately Not Claimed

To keep this document honest:

- No claim that SEALY prevents burnout or produces a health outcome
- No statistics about student stress or burnout are asserted here; figures appearing in earlier planning material have not been source-verified
- No claim that Haziq's tool list reflects measured usage patterns
- No interview data, because none exists

---

## Related Documents

- [Life Before and After SEALY](life-before-after.md)
- [Alternative Solution Directions](../ideation/idea-comparison.md)
- [Ideation and Prototype Evolution Log](../ideation/SEALY_Ideation_and_Prototype_Evolution_Log.md)

---

## TODO

- Validate the persona against at least a few real final-year students. Currently unvalidated.
- Raise the persona with Mentor #1 (10 September) and record whether it holds up.
