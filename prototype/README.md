# SEALY — Prototype

> **Status as of 1 September 2026: no prototype has been built yet.**
>
> No design file, no clickable prototype, no screens, no application code, and no screenshots exist in this repository. This document defines what the prototype must demonstrate and records its status honestly. Every status field is updated only when the corresponding artefact actually exists.

---

## Purpose of the Prototype

The prototype exists to demonstrate one thing:

> **That a student's scattered responsibilities — including those that exist only on paper — can be consolidated into a single view that shows whether a week is actually feasible, explains why it is not, and proposes specific changes the student approves.**

It is not intended to be a complete application. Breadth is not the goal; one coherent journey is.

---

## The Core Journey Being Tested

```text
Capture  →  Understand  →  Visualise  →  Rebalance  →  Recover
```

In interaction terms:

```text
1. Capture a physical source with the camera
2. AI extracts candidate tasks
3. User reviews each candidate: edit / accept / reject
4. Confirmed items enter the workload
5. Workload shown across life areas and across days
6. Overloaded day identified
7. Cause explained in concrete terms
8. Rebalancing proposed
9. User approves or rejects each proposal
10. Recovery time protected
```

Step 3 is deliberate and must be visible in the prototype. Extracted items are **candidates**, not tasks, until a person confirms them. See [AI Responsibility](../docs/architecture/ai-responsibility.md).

---

## Planned Screens

None of these exist yet. This is the intended minimum set for the journey to be demonstrable end to end.

| # | Screen | Purpose | Status |
|---|---|---|---|
| 1 | Onboarding | Establish life areas and available capacity | Not started |
| 2 | Home / workload overview | Total load across life areas; overloaded days visible | Not started |
| 3 | Capture | Camera with framing guidance | Not started |
| 4 | Extraction review | Candidate items, each editable, acceptable, or rejectable | Not started |
| 5 | Workload detail for a day | Estimated effort against available capacity | Not started |
| 6 | Explanation | Which commitments produce the overload | Not started |
| 7 | Rebalancing proposals | Suggested changes with trade-offs; per-item approval | Not started |
| 8 | Recovery | Protected rest and recovery time | Not started |
| 9 | SEALY conversation | Explains computed results in SEALY's voice | Not started |

Screens 3, 4, 5, and 7 carry the differentiator. If the set must be reduced, those are the ones to keep.

---

## Expected Interaction

- **Capture** — one-handed, phone-first, usable while standing away from a desk
- **Review** — every extracted field editable before acceptance; rejection available per item; no bulk-accept that skips review
- **Workload view** — feasibility legible at a glance, not requiring interpretation
- **Explanation** — concrete and quantitative, in the form *"Thursday holds approximately 7 hours of estimated work against approximately 4 hours of available capacity"*
- **Rebalancing** — SEALY proposes; the user approves. Nothing moves on its own

---

## Technical Proof Status

The prototype phase targets specific technical proofs. Current status is determined by repository inspection.

| Technical proof | Status | Notes |
|---|---|---|
| Expo application launches on a device | **Not started** | No application code exists |
| Minimal Supabase layer (Profile / Workspace / Task) | **Not started** | No schema created |
| Image → server → AI → structured task data | **Not started** | Highest priority |
| Human confirmation before persistence | **Not started** | |
| Deterministic workload / capacity calculation | **Not started** | Formulation not yet decided — see [technical feasibility](../docs/architecture/technical-feasibility.md) |
| Explainable workload visualisation | **Not started** | |
| Constrained AI explanation of a computed result | **Not started** | Optional if time is short |

**No component is implemented, partially implemented, or tested.**

---

## Prototype Links

| Artefact | Link |
|---|---|
| Design file / clickable prototype | Coming soon |
| Hosted or installable build | Coming soon |
| Demo video | Coming soon |

No links are recorded because none exist. Links are added here only once real and reachable.

---

## Screenshots

None available. Screenshots will be added to this directory once screens exist.

---

## What Will Be Interactive vs Simulated

To be completed once the prototype exists. This section must clearly separate:

- **Interactive** — real behaviour backed by working code
- **Simulated** — designed flows with representative data, no live processing
- **Static** — visual only

Stating this distinction plainly is more credible than implying everything works. It must be accurate at the point of judging.

*Currently: nothing is interactive, simulated, or static, because nothing has been built.*

---

## Known Limitations

Anticipated, and to be confirmed against the built prototype:

- Extraction quality will vary with photograph quality; poor lighting and difficult handwriting will produce errors. Human review is the intended safeguard.
- The capacity calculation depends on effort estimates, which students may find difficult to give accurately. This is the largest open risk to the concept.
- Ambiguous academic date formats may resolve incorrectly and require explicit confirmation.
- Free-tier service limits constrain demonstration volume.
- Live network calls introduce latency risk during any live demonstration.
- The prototype covers one journey. Deferred capabilities — collaboration, dependencies, gamification, habits, ambient audio — are not present and must not be described as present.

---

## Related Documents

- [Project README](../README.md)
- [Technical Feasibility](../docs/architecture/technical-feasibility.md)
- [AI Responsibility Model](../docs/architecture/ai-responsibility.md)
- [Persona — Haziq](../docs/ucd/persona.md)
- [Ideation and Prototype Evolution Log](../docs/ideation/SEALY_Ideation_and_Prototype_Evolution_Log.md)
