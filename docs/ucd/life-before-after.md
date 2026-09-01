# Life Before and After SEALY

> **Status:** Design narrative, Iteration 1b (1 September 2026).
>
> **Evidence note:** This document describes the *intended* change in how a student makes workload decisions. It is a design target, not a measured outcome. SEALY has not been used by any student, and no outcome has been observed. Claims are limited to decision quality and workload visibility. No health, wellbeing, or academic-performance outcome is claimed.

---

## What This Document Compares

The comparison is not "disorganised student" versus "organised student". Haziq is already reasonably organised — he uses a calendar, he keeps notes, he does not forget deadlines outright.

The comparison is **the quality of the information available at the moment a decision is made.**

---

## Before SEALY

### The information state

Haziq's workload exists across six locations — WhatsApp, Google Calendar, Notion, sticky notes, printed material, and memory. Each holds a fragment. None holds the total.

Consolidating them is possible but expensive: fifteen to twenty minutes of manual cross-referencing, repeated whenever anything changes. Under pressure, it does not happen.

### What he can and cannot see

| He can see | He cannot see |
|---|---|
| Individual deadlines | Total effort required in a given week |
| Scheduled events with times | How much time is actually left after those events |
| That he is busy | Which specific day the commitments collide on |
| That the week feels heavy | Which commitments are producing the pressure |
| That something must give | Which option costs least to move |

### The decision he makes

Commitments are evaluated one at a time, against the nearest empty slot. "Can I do this on Wednesday evening?" is answerable. "Given everything else, should I?" is not.

### The failure pattern

1. Commitments are accepted separately, each one reasonable in isolation
2. Load accumulates without ever being visible in aggregate
3. Overload is recognised from *inside* the overloaded period
4. Remaining options are all poor — late submission, reduced quality, or a compressed night
5. Recovery time absorbs the shortfall, because it is the only category with no external deadline
6. The pattern is not analysed afterwards, so it repeats

### The characteristic moment

Wednesday, late. He realises Thursday is not survivable as planned. Everything that could have been moved cheaply on Monday can now only be moved expensively.

---

## After SEALY

### The information state

Responsibilities from physical and digital sources are captured into one system. Printed material enters through the camera rather than through typing. Each item carries an estimated effort, not only a date.

One view represents the total.

### What changes in what he can see

| Before | After |
|---|---|
| Six fragmented sources | One consolidated workload view |
| Dates without effort | Estimated effort against available capacity |
| "This week feels heavy" | "Thursday holds ~7 hours of estimated work against ~4 hours of available capacity" |
| Overload discovered inside the week | Overloaded days visible in advance |
| Unexplained pressure | Named contributing commitments |
| Undifferentiated options | Specific proposals, with the cost of each |
| Recovery as leftover time | Recovery as a protected commitment |

### The decision he makes

At the moment he is asked to take on something new, he can see what he has already committed to. The question shifts from *"is there a free slot?"* to *"given the full picture, is this a good commitment to make?"*

### The changed pattern

1. Commitments are captured cheaply, including the ones that only exist on paper
2. Total load is continuously visible rather than reconstructed on demand
3. Collisions surface before the affected day arrives
4. The cause is explained in concrete terms — hours of work against hours of capacity
5. Rebalancing options are proposed with their trade-offs stated
6. **Haziq approves or rejects each change.** SEALY proposes; it does not act
7. Recovery is represented in the plan rather than being what is left over

### The characteristic moment

Monday. Asked for slides by Thursday, he sees Thursday is already over capacity, sees which commitments cause it, sees that the slides fit on Saturday at no cost, and answers accordingly.

The decision was always his. What changed is that he made it with complete information, three days earlier, when moving things was still cheap.

---

## Side by Side

| Dimension | Before | After |
|---|---|---|
| Sources of truth | Six, disconnected | One consolidated view |
| Physical material | Never digitised | Captured via camera, confirmed by the user |
| Unit of planning | Dates | Effort against capacity |
| Overload detected | Inside the overloaded period | Before it arrives |
| Explanation | None | Named contributing commitments |
| Options at the point of decision | Improvised | Proposed with trade-offs |
| Who decides | Haziq, with partial information | Haziq, with the full picture |
| Recovery | Absorbs the shortfall | Represented and protected |
| Effort to see the whole picture | 15–20 minutes of manual work | Opening the app |

---

## What Is Deliberately Not Claimed

This section exists to keep the document defensible.

- **Not claimed:** that SEALY prevents or reduces burnout. That is a clinical outcome requiring clinical evidence.
- **Not claimed:** any effect on grades, wellbeing, or academic performance.
- **Not claimed:** that students will use SEALY consistently. Adoption is unproven.
- **Not claimed:** that AI extraction is accurate enough to trust unreviewed. This is precisely why human confirmation is mandatory.
- **Not claimed:** that this transformation has been observed. It has not. No student has used SEALY.

**What is claimed:** a student making a commitment decision with a consolidated view of effort against capacity is making a better-informed decision than one working from six disconnected sources. That is a claim about information quality, and it is the claim SEALY is built on.

---

## How This Would Be Validated

Currently unvalidated. The realistic test within the prototype phase:

1. Give a student a real printed academic document and ask them to reconstruct their week from their existing tools. Time it.
2. Do the same through SEALY's capture flow. Time it.
3. Ask whether the resulting view showed them anything they had not already known.

Step 3 is the one that matters. If a student learns nothing from the consolidated view, the core hypothesis is wrong.

**Status: not yet attempted.**

---

## Related Documents

- [Persona — Haziq](persona.md)
- [Alternative Solution Directions](../ideation/idea-comparison.md)
- [Ideation and Prototype Evolution Log](../ideation/SEALY_Ideation_and_Prototype_Evolution_Log.md)
