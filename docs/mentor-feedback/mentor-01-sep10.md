# Mentor Consultation #1 — Low-Input / High-Output Pivot

> This file records the first mentor session and the resulting product direction. Exact identity/date fields not confirmed by the team remain intentionally unfilled rather than invented.

## Session details

| Field | Value |
|---|---|
| Session | Mentor Consultation #1 |
| Mentor | *To confirm* |
| Actual date | *To confirm* |
| Product state shown | SEAL ideation: Focus / Rebalance / Recover, Calendar input, OCR exploration, workload-capacity reasoning |

## Main feedback received

The strongest thread was **input-to-output efficiency**: the student should do as little manual organization as possible before SEAL becomes useful.

The mentor challenged the team to explore:

- more creative input methods instead of simple/manual forms;
- OCR/photo because one image can contain several responsibilities;
- understanding the task before asking the student to organise it;
- splitting a vague task into smaller subtasks;
- Telegram/API-assisted intake;
- authorised headless-browser / “computer use” style exploration;
- narrower problem framing;
- an agentic direction where the system collects/structures/proposes rather than waiting for perfect input;
- simple confirmation and user control rather than forced automatic mode switching;
- a low learning curve.

## Product decision

The team translated the feedback into one principle:

> **How much useful workload understanding can SEAL create from the smallest possible amount of student effort?**

## Changes made

### OCR revisited

The original Idea 02 decision remains historically true:

> OCR as the entire product was dropped.

After Mentor #1 it was revisited as an **input layer**:

```text
Photo / screenshot
→ OCR
→ extract candidates
→ structure
→ optional decomposition
→ user confirmation
→ workload engine
```

### Manual entry demoted

Manual entry remains a fallback, not the centre of the product.

### Task decomposition added as an exploration

Example:

```text
“Finish project plan”
→ review brief
→ finalise summary
→ check schedule/budget
→ check risks/resources
→ final review/submit
```

Suggestions remain editable.

### Multi-source intake

The architecture was reframed so every source converges into the same normalized model:

```text
Camera / Gallery / Calendar / Share / Email / Future Telegram / Future browser agent
                              ↓
                       Candidate Intake
                              ↓
                     Structured task/event
```

### Human-in-the-loop autonomy

SEAL may infer a recommended action, but the user keeps authority.

```text
SEAL recommends
FOCUS / REBALANCE / RECOVER
        ↓
User accepts / edits / dismisses
```

## Future agentic direction — constraints

Headless-browser / portal automation is a **future research direction only**.

It requires:

- explicit authorization;
- supported sites;
- no bypass of login or MFA;
- privacy/security review;
- uncertainty handling;
- candidate confirmation.

Similarly, Telegram means user-forwarded / bot-submitted information, not silent reading of private conversations.

## What Mentor #1 did not change

The core product is still the workload-capacity decision layer. Agentic intake is a way of feeding it, not a replacement for it.

## Later Mentor #2 relationship

Mentor #1 reduced **input effort**. Mentor #2 then reduced **interpretation effort** by simplifying what the user sees on screen.

See [Mentor #2](mentor-02-sep12.md).

## Related documents

- [Evolution Log](../ideation/SEAL_Ideation_and_Prototype_Evolution_Log.md)
- [Technical Feasibility](../architecture/technical-feasibility.md)
- [Prototype Overview](../../prototype/README.md)
