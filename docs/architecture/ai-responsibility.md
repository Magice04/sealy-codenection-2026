# SEAL — AI & Automation Responsibility Model

SEAL is not designed as an AI wrapper. Its core value is the **workload-capacity decision layer**: what needs to be done, how much time remains, and what action is appropriate.

## Core rule

> **AI may interpret and propose. Deterministic application logic owns arithmetic, constraints and final state. The user owns consequential decisions.**

## What application logic should own

| Responsibility | Why |
|---|---|
| Dates, times and deadline arithmetic | Must be reproducible |
| Work-duration totals | The user must be able to trace the number |
| Available-time calculation | Calendar arithmetic, not language-model inference |
| 55-minute shortfall / spare-time calculation | Simple deterministic difference |
| Calendar overlap rules | Must be predictable |
| Task status and persistence | Database/business logic |
| Permissions and access control | Security boundary |
| Recommendation state | Rule-based MVP is explainable and testable |

The prototype example is intentionally transparent:

```text
required_work = 90 + 65 + 60 = 215 minutes
available_time = 160 minutes
shortfall = 215 - 160 = 55 minutes
```

The model should never invent `55` from prose. Application code computes it.

## Where AI can help

| AI-assisted area | Output must remain |
|---|---|
| OCR/text interpretation | editable candidate data |
| Natural-language extraction | editable candidate task/event |
| Task decomposition | suggested subtasks |
| Ambiguous classification | suggestion with confidence / confirmation |
| Plain-language explanation | explanation of a deterministic result |
| Future agentic intake | proposed items from explicitly authorised sources |

## Human-in-the-loop checkpoints

SEAL's automation is intentionally interruptible at consequential points:

```text
Source
  ↓
Extract candidate
  ↓
[USER CONFIRMS / EDITS / IGNORES]
  ↓
Structured workload
  ↓
SEAL calculates plan state
  ↓
SEAL suggests Focus / Adjust / Take a Break
  ↓
[USER ACCEPTS / CHANGES / DISMISSES]
```

The current adjustment actions are:

- **Keep** — no change;
- **Add** — generate another plan arrangement;
- **Move** — user chooses a different slot;
- **Defer** — postpone because the deadline changed or the item is not urgent.

SEAL does not silently rewrite the student's calendar.

## OCR is an input mechanism, not the product

The team originally explored OCR as a standalone product direction and dropped it because OCR-to-task alone did not solve the workload problem. Mentor #1 later prompted the team to revisit OCR as a **low-friction intake mechanism**.

That distinction is important:

```text
OCR only                SEAL
--------                ----
extract text      →      structure workload
                        calculate fit
                        explain shortfall
                        suggest action
```

## Agentic / browser automation boundary

A future authorised browser adapter could visit a supported student portal and extract candidate deadlines. That does **not** mean unrestricted autonomous browsing.

Requirements for any future browser agent:

1. explicit user authorisation;
2. supported sites only;
3. no bypass of authentication, MFA or access controls;
4. credentials handled by a secure integration boundary, not exposed to an LLM prompt;
5. extracted data treated as a candidate until confirmed;
6. site policy / terms considered;
7. failures and uncertainty surfaced to the user.

Headless-browser work is a **future research direction**, not a current prototype implementation.

## Telegram / messaging boundary

A future Telegram bot could accept information that the student intentionally forwards or sends. SEAL must not imply it silently reads all private conversations.

Same principle for WhatsApp, Teams, Discord or email: **explicit share/import only** unless an authorised integration exists.

## Five-load / wellbeing boundary

Earlier ideation used Mental, Time, Physical, Social and Errand load as five dimensions. Mentor #2 identified that presenting these as five calculated scores is difficult to understand and risks false precision.

Current position:

- **Time/workload fit** is the concrete primary signal.
- mental state, energy, social commitments and errands are contextual inputs.
- SEAL does not combine them into a clinically meaningful “stress score”.
- SEAL does not diagnose burnout, depression, fatigue disorders or any other health condition.

## Recovery boundary

A Take-a-Break recommendation can use non-clinical signals such as:

- time since last break;
- recent focus-session history;
- user-reported energy/check-in;
- whether an urgent deadline is still imminent.

It should not claim to detect mental illness or physiological exhaustion.

## App blocking boundary

The Figma prototype now states:

> **Only apps explicitly selected by the user are paused. Everything else remains available during Focus.**

This is a UX rule, not proof that OS-level blocking is implemented. Native Screen Time / Digital Wellbeing-style enforcement is platform-dependent and remains future work.

## Data minimisation

For any real implementation:

- process only data needed for the requested import;
- avoid retaining raw photos/documents after structured extraction unless the user deliberately saves them;
- store source metadata only where useful for audit/editing;
- use Supabase RLS for user-owned records;
- keep provider/service credentials server-side;
- make deletion and re-import predictable.

## What SEAL deliberately does not claim

- medical diagnosis;
- burnout prediction;
- perfect OCR;
- perfect task-duration estimation;
- autonomous schedule modification without approval;
- unrestricted access to websites or messaging accounts;
- technically working app blocking from a Figma screen.

## Related documents

- [Technical Feasibility](technical-feasibility.md)
- [Prototype Overview](../../prototype/README.md)
- [Ideation Evolution Log](../ideation/SEAL_Ideation_and_Prototype_Evolution_Log.md)
