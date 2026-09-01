# AI Responsibility Model

> **Status:** Architectural decision, Iteration 1b (1 September 2026).
>
> **Implementation status:** **Not implemented.** No AI integration exists in this repository. This document specifies the intended division of responsibility and the constraints any implementation must satisfy. Everything below is a design contract, not a description of running code.

---

## The Principle

> **AI is used where language and images must be interpreted. Everything that determines application state is deterministic code.**

SEALY uses AI deliberately and narrowly. The test applied to every feature is:

> *Does this require interpreting something ambiguous — an image, or a sentence a person wrote?*

If yes, AI is appropriate. If no, it is application logic. A date comparison is not an AI problem. Reading a student's handwriting is.

---

## Why This Boundary Matters

Three reasons, in order of importance.

**1. Explainability.** A student is told their Thursday is overloaded. They are entitled to ask why. If a model produced the number, the honest answer is "the model said so", which is not an answer. If deterministic code produced it, the answer is a specific sum of specific commitments against specific available time.

**2. Consistency.** The same inputs must produce the same workload figure every time. A number that varies between runs cannot be trusted, cannot be compared week to week, and cannot be debugged.

**3. Safety.** A workload figure that influences how a student manages their week must not be a guess. Generating such a number by inference and presenting it as a measurement would be the most serious failure SEALY could make.

There is also a product reason. SEALY's value is the workload system. Building it as a wrapper around a language model would make the model the product, and the model is not the differentiator.

---

## Division of Responsibility

### AI is responsible for

| Responsibility | Input | Output |
|---|---|---|
| Image understanding | Photograph of notes, whiteboard, or academic document | Text and structure identified in the image |
| Candidate task extraction | Image content | Structured candidate items — title, possible date, possible effort estimate |
| Scheme of Work interpretation | Photograph or text of an academic schedule | Structured subjects, assessments, and dates |
| Natural-language interpretation | A sentence the user typed | Structured intent |
| Workload explanation | A workload result **already computed** by application code | A plain-language explanation of that result |
| Rebalancing suggestions | Current tasks plus a computed workload result | Proposed changes, each with a stated reason |
| Conversational responses | Conversation context | SEALY's replies in its established voice |

### Application logic is responsible for

| Responsibility | Why it is not AI |
|---|---|
| Authentication and session management | Security boundary; must be deterministic |
| Database persistence | Correctness requirement |
| Access control and permissions | Enforced by Row Level Security, never by a model |
| Deadline and date arithmetic | Ordinary computation |
| Task state transitions | Defined state machine |
| **Workload and capacity calculation** | Must be deterministic, explainable, reproducible |
| Overloaded-day identification | Follows directly from the workload calculation |
| Scheduling constraints and feasibility validation | Rule evaluation |
| Input validation | Security requirement |
| Streak and progress counters | Arithmetic |

### The critical line

> **AI never computes the workload figure. Application code computes it; AI is given the result and asked to explain it.**

The explanation endpoint receives an already-computed result. It does not receive the raw task list with an instruction to assess it. This is not a stylistic preference — it is the constraint that makes the number defensible.

---

## Human-in-the-Loop Requirement

AI-extracted content must never enter the workload system without explicit per-item confirmation.

```text
Image captured
      ↓
AI extraction
      ↓
Candidate structured tasks  ← not persisted; held in review state
      ↓
User review
      ↓
Edit / Accept / Reject  ← per item, individually
      ↓
Persistence  ← only confirmed items
```

**Requirements this places on any implementation:**

- Candidate items are held in a review state and are not written to the tasks table
- Every field the model produced must be editable before acceptance
- Rejection must be available per item, not only for the batch
- A single bulk-accept control that skips per-item review does **not** satisfy this requirement

An earlier planning blueprint proposed a single bulk-accept action after scanning. That was superseded during Iteration 1 for exactly this reason, and the decision is recorded in the [evolution log](../ideation/SEALY_Ideation_and_Prototype_Evolution_Log.md).

Rebalancing proposals are subject to the same rule. SEALY proposes changes to a week; it does not apply them. The user approves each one.

---

## Structured Output and Validation

Model output crossing into the application is untrusted input and must be validated like any other external data.

**Intended contract:**

- The server requests structured output against a defined schema
- The server validates the response against that schema before use
- Type, range, and format checks are applied — dates must parse, effort estimates must be positive and within plausible bounds, required fields must be present
- Items failing validation are surfaced to the user for correction, not silently dropped and not silently repaired
- Malformed responses never reach the database

**Status: specified, not implemented.** No schema has been written.

---

## AI Failure Modes and Handling

Anticipated failure modes, and the intended response to each.

| Failure mode | Consequence if unhandled | Intended handling |
|---|---|---|
| Misread text — poor lighting, blur, difficult handwriting | Wrong task title or date enters the workload | User review catches it; capture guidance reduces frequency |
| Fabricated detail — a plausible date the document does not contain | User accepts a commitment that does not exist | Per-item review; source context shown alongside each candidate |
| Ambiguous date — "week 9", "next Friday" | Item lands on the wrong day | Present as uncertain and require user confirmation of the date |
| Schema violation | Malformed data reaches the database | Server-side validation rejects before persistence |
| Model unavailable or rate limited | Capture flow fails | Explicit error state and retry; manual entry remains available |
| Latency | Capture appears broken | Visible progress state; capture must never block other use of the app |
| Nothing extractable in the image | Empty result confuses the user | Explicit empty state explaining what was not found |

**The general defence:** every one of these is caught by the same mechanism — nothing the model produces becomes real until a person confirms it. Human confirmation is the primary safety control, not a UX preference.

---

## What SEALY Deliberately Does Not Do

Stated explicitly, because these are the failure modes of AI-first products:

- **AI does not modify application state.** It has no write access to the database. It returns data to the application, which validates it and presents it for confirmation.
- **AI does not decide priority or urgency.** Those follow from deadlines, effort estimates, and user input.
- **AI does not produce the workload number.**
- **AI does not silently reschedule anything.**
- **AI does not make clinical or health assessments.** SEALY reports workload, not wellbeing. See the terminology decision in the [evolution log](../ideation/SEALY_Ideation_and_Prototype_Evolution_Log.md).

---

## Security Boundary

The AI provider is reached **only** from the server layer.

- The `ANTHROPIC_API_KEY` is a server-side environment variable and must never be present in the mobile bundle
- The mobile application calls SEALY's own API endpoints, never the AI provider directly
- Each endpoint verifies the caller's Supabase session before any AI call
- Only intentionally public values may use the `EXPO_PUBLIC_` prefix

See [technical-feasibility.md](technical-feasibility.md) for the full security and environment model.

---

## Implementation Status

| Component | Status |
|---|---|
| AI responsibility boundary | **Specified** — this document |
| Human-in-the-loop flow | **Specified**, not built |
| Structured output schemas | **Planned** — not written |
| Validation layer | **Planned** — not written |
| Scan endpoint | **Planned** — not written |
| Explanation endpoint | **Planned** — not written |
| Conversation endpoint | **Planned** — not written |
| Scheme of Work endpoint | **Deferred** — optional spike |
| AI model selection | **Not decided.** No model has been pinned. An identifier appearing in earlier planning material does not correspond to a currently available model and must not be treated as a decision. |

---

## Related Documents

- [Technical Feasibility](technical-feasibility.md)
- [Ideation and Prototype Evolution Log](../ideation/SEALY_Ideation_and_Prototype_Evolution_Log.md)
- [Prototype Overview](../../prototype/README.md)
