# SEALY — Alternative Solution Directions and Decision Rationale

> **Purpose:** Record the solution directions the team considered for the Stress & Workload Manager challenge, how they were compared, and why SEALY's current direction was selected.
>
> **Status:** Iteration 1b, 1 September 2026.
>
> **Method note:** The scoring below is structured team judgement recorded during ideation. It is not user research, not survey data, and not benchmark measurement. It is included to show reasoning, not to claim empirical validation.

---

## Why This Document Exists

The challenge — *Stress & Workload Manager* — can be answered in several genuinely different ways. Choosing one without examining the others would leave the team unable to explain why the chosen direction is better than the obvious alternatives.

Five directions were identified during Iteration 0 and Iteration 1. All five are legitimate responses to the challenge. Four were not selected.

---

## The Five Directions Considered

### Direction A — Stress Diary

A journalling application. The student logs mood, energy, and stress level daily. The app charts trends over time and surfaces patterns.

**Strength:** Simple to build. Emotionally honest. Low technical risk.

**Why it was not selected:** It records a problem without changing it. A student who has already accepted too many commitments learns from the chart that they are under strain, which they already knew. The application holds no information about deadlines, estimated effort, or available time, so it cannot suggest any concrete change. It observes; it cannot act.

---

### Direction B — AI Wellness Chatbot

A conversational agent offering support, coping strategies, and encouragement.

**Strength:** Warm, accessible, immediately understandable to a judge.

**Why it was not selected:** Two independent reasons.

First, it has no model of the student's actual workload. Advice given without knowing what is due on Thursday is generic advice, and generic advice is already freely available.

Second, this direction drifts toward mental-health support, which carries a duty of care the team is not positioned to meet. SEALY should help a student make better workload decisions. It should not position itself as a wellbeing intervention.

This direction was rejected as a *product*, but its conversational quality was retained as SEALY's interface layer.

---

### Direction C — Smart Task Manager

A task manager with AI assistance — better capture, smarter sorting, automatic prioritisation.

**Strength:** Clear utility. Familiar mental model. Straightforward to demonstrate.

**Why it was not selected:** The category is saturated and the team could not identify a defensible reason for a student to switch. More importantly, a task manager answers *"what do I have to do?"* — a question students can usually already answer. The question they cannot answer is *"is all of this actually possible in the time I have?"* A task list of twenty items and a task list of six items look structurally identical; the difference between them is invisible in a list view.

Task management is a necessary substrate for SEALY, but it is not the product.

---

### Direction D — Calendar Optimisation Assistant

An assistant that ingests calendar data and automatically rearranges commitments into optimal time blocks.

**Strength:** Genuinely useful. Addresses scheduling directly.

**Why it was not selected:** It assumes the calendar is already complete and accurate. For the target user it is not — a substantial part of the real load lives on printed handouts, sticky notes, group chats, and memory, and never reaches the calendar at all. Optimising an incomplete calendar produces a confident schedule built on partial information, which is arguably worse than no schedule.

The gap this direction exposed — *the calendar does not contain the real workload* — is what led directly to the physical-to-digital capture idea.

---

### Direction E — Workload Capacity Manager (selected)

A system that consolidates commitments from both physical and digital sources, estimates total load against available capacity, identifies where commitments collide, explains the cause, and proposes specific rebalancing.

**Why it was selected:** It is the only direction that addresses the insight the team kept returning to — that no individual responsibility looks unmanageable, and overload only becomes visible when everything is considered together. It also subsumes the useful parts of the rejected directions: it needs task management (C), it produces schedule change proposals (D), and it speaks conversationally (B).

---

## Comparison Matrix

Rated 1–5 against the team's reading of the challenge and the target user. Higher is better.

| Criterion | A. Stress diary | B. Wellness chatbot | C. Smart task manager | D. Calendar optimiser | E. Workload capacity manager |
|---|---|---|---|---|---|
| Alignment with "Stress & Workload Manager" | 3 | 2 | 3 | 3 | 5 |
| Actionability — can the user do something specific with the output? | 1 | 2 | 3 | 4 | 5 |
| Originality relative to existing tools | 2 | 1 | 1 | 3 | 4 |
| Differentiation — is there a reason to switch? | 1 | 1 | 1 | 3 | 4 |
| Technical feasibility within the prototype phase | 5 | 4 | 4 | 3 | 3 |
| Usefulness to the target user | 2 | 2 | 3 | 3 | 5 |
| Long-term product potential | 2 | 2 | 3 | 4 | 4 |
| **Total (max 35)** | **16** | **14** | **18** | **23** | **30** |

The selected direction is deliberately *not* the easiest to build. It scores lowest but one on feasibility. That trade-off is accepted and is the reason prototype scope was reduced during Iteration 1 — the ambition sits in the concept, and the scope discipline sits in the implementation plan.

---

## What Carried Forward From Rejected Directions

Rejecting a direction did not mean discarding everything in it.

| From | Retained in SEALY |
|---|---|
| A. Stress diary | Optional mood and energy input as one signal among several — never as the product itself |
| B. Wellness chatbot | The conversational interface and the seal mascot as the emotional layer over a workload system |
| C. Smart task manager | Task capture, structure, and state as the data substrate the workload metric reads from |
| D. Calendar optimiser | Time-based visualisation and the rebalancing proposal flow |

---

## The Decision

> SEALY is a **workload capacity manager**. It consolidates responsibilities from physical and digital sources, shows total load against available capacity, explains why a day or category is overloaded, and proposes specific rebalancing the student approves.

The conversational seal is how SEALY communicates. It is not what SEALY is.

---

## Open Questions

- The comparison reflects team judgement only. Testing the core assumption with even a small number of real students would materially strengthen it. **TODO** — not yet done.
- Direction D's failure mode (optimising an incomplete calendar) is an assumption, not an observation. Worth raising with a mentor.

---

## Related Documents

- [Ideation and Prototype Evolution Log](SEALY_Ideation_and_Prototype_Evolution_Log.md)
- [Competitor and Positioning Analysis](../research/competitor-analysis.md)
- [Persona — Haziq](../ucd/persona.md)
