# SEALY — Prototype

> **Status as of 3 September 2026: a clickable design prototype exists. No application code exists.**
>
> A Figma design file with a fully connected, clickable prototype of the core journey now exists and can be walked end to end. **Nothing is backed by working code** — there is no Expo application, no database, and no live AI extraction. Every flow in the prototype is *simulated* with representative data. That distinction is stated explicitly in [What Is Interactive vs Simulated](#what-is-interactive-vs-simulated) below and must be stated in the demo and pitch too.

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

All nine are now designed. Screens 1–8 are built and connected in the clickable prototype; screen 9 exists as a v2 concept only and is not part of the demo flow.

| # | Screen | Purpose | Status |
|---|---|---|---|
| 1 | Onboarding | Establish life areas and available capacity | **Designed — 3 screens, connected** |
| 2 | Home / workload overview | Total load across life areas; overloaded days visible | **Designed — Default + Overload states** |
| 3 | Capture | Camera with framing guidance | **Designed — Camera + Scanning** |
| 4 | Extraction review | Candidate items, each editable, acceptable, or rejectable | **Designed — per-item Accept / Reject shown**¹ |
| 5 | Workload detail for a day | Estimated effort against available capacity | **Designed — Thursday, 7h vs 4h, +3h** |
| 6 | Explanation | Which commitments produce the overload | **Designed** |
| 7 | Rebalancing proposals | Suggested changes with trade-offs; per-item approval | **Designed — Proposal + Approved** |
| 8 | Recovery | Protected rest and recovery time | **Designed** |
| 9 | SEALY conversation | Explains computed results in SEALY's voice | Concept only — not in demo flow |

¹ The Accept / Reject controls are *visual affordances*. They communicate the confirmation model but do not change state on click, because per-row state toggling is not achievable in a flat click-through prototype. The reviewing step itself is present and unavoidable in the flow.

**Additional screens designed beyond the original set** (concept / next-iteration, in the `IDEAS / v2 CONCEPTS` section): Week View, Stats, Settings, Life Areas Breakdown, Edit Candidate Task, Capture Failed, Home Empty State, SEALY Conversation.

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

**No component is implemented, partially implemented, or tested.** The technical proofs above are unaffected by the design prototype — a connected Figma flow is not evidence that any of them work.

---

## Prototype Links

| Artefact | Link |
|---|---|
| Design file / clickable prototype | `https://www.figma.com/design/Y2ce2KYSTXDkNBqLAMcfaF/` |
| Hosted or installable build | Coming soon — no application code exists |
| Demo video | Coming soon |

**Before submission:** the Figma link above must have sharing set to *Anyone with the link → can view*, and must then be opened from a signed-out browser to confirm it is genuinely reachable. Until that check is done, treat the link as unverified.

**Prototype structure:** three pages — `Foundations & Components` (colour, type, spacing, radius, stroke, component library, mascot semantic library), `Prototype` (AUTH · ONBOARDING · CORE · IDEAS/v2 CONCEPTS), and `UX / Iterations` (design-process evidence).

## Screenshots

Not yet exported. Screens now exist in the Figma file; PNG exports of the key journey should be added to this directory before submission so the repository stands on its own without requiring Figma access.

---

## What Is Interactive vs Simulated

Stating this plainly is more credible than implying everything works. It must be accurate at the point of judging.

| Category | What it covers | Present in SEALY today |
|---|---|---|
| **Interactive** — real behaviour backed by working code | Live camera capture, real AI extraction, real workload calculation, persistence | **None.** No application code exists. |
| **Simulated** — designed flows with representative data, no live processing | The entire clickable journey: login, onboarding, capture, scanning, extraction review, confirmation, workload detail, explanation, rebalancing, approval, recovery | **All of it.** Every screen is a designed frame with fixed representative data; taps navigate between frames. |
| **Static** — visual only | Foundations, component library, mascot semantic library, UX / Iterations evidence page | Yes. |

**The figures shown in the prototype (7h estimated workload, 4h capacity, +3h difference) are representative example data, not computed output.** Say so during any demonstration.

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
