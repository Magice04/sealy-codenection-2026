# Competitor and Positioning Analysis

> ## Scope and Evidence Status
>
> **This is product-positioning exploration, not verified market research.**
>
> The team has not conducted market research, user surveys, competitive usage studies, or structured feature audits. The comparisons below reflect the team's general understanding of well-known tools, assessed against the specific capabilities SEALY is being built around.
>
> **No market-size figures, adoption statistics, user counts, or revenue data appear in this document**, because the team has no sourced data for any of them. Statements about competitor products describe broad product categories and should be verified before being used as factual claims in a pitch.
>
> **Status:** Iteration 1b, 1 September 2026.

---

## Why This Analysis Exists

SEALY sits in a crowded space. Task managers, calendars, and wellbeing applications are abundant and mature. The question this document answers is narrow:

> **Is there a capability gap that justifies building SEALY, rather than a student using an existing tool better?**

---

## The Capabilities That Define SEALY

Six capabilities distinguish SEALY's intended direction. They are the dimensions the comparison uses.

1. **Physical-to-digital capture** — bringing commitments that exist only on paper, whiteboards, or handouts into the system without manual transcription
2. **Cross-life-area aggregation** — treating academic, career, social, physical, and personal load as one total, not separate lists
3. **Capacity reasoning** — comparing required effort against available time, rather than listing dates
4. **Overload identification with explanation** — naming which commitments cause a specific day's pressure
5. **Rebalancing proposals under human approval** — proposing specific changes the user approves
6. **Recovery as a protected commitment** — representing rest as something scheduled rather than as leftover time

---

## Category Comparison

Assessed by product category rather than by naming specific version numbers or feature sets, since the team has not audited current releases.

| Capability | Task managers (e.g. Todoist-style) | Notion-style workspaces | Calendar tools | Scheduling assistants | Wellbeing / meditation apps | **SEALY (intended)** |
|---|---|---|---|---|---|---|
| Capture from physical sources via camera | No | Limited — image attachment, not structured extraction | No | No | No | **Yes — core** |
| Aggregates across life areas | Partially, if manually configured | Yes, if manually built | Only what is entered | Only what is entered | No | **Yes — by design** |
| Models effort against available capacity | No | No | No | Partially | No | **Yes — core** |
| Explains *why* a day is overloaded | No | No | No | Rarely | No | **Yes — core** |
| Proposes rebalancing with user approval | No | No | No | Yes, often automatic | No | **Yes — approval required** |
| Treats recovery as a commitment | No | No | Only if manually blocked | Sometimes | Indirectly | **Yes — intended** |
| Manual entry burden | High | Very high | High | High | Low (no workload data) | **Reduced — the point of capture** |
| Addresses workload management | Yes | Yes | Partially | Yes | No | **Yes** |

---

## Where Each Category Falls Short for This User

**Task managers.** Strong at capture, structure, and completion. They answer *"what do I have to do?"* — a question the target user can usually already answer. They do not answer *"is this week possible?"* A list of twenty items and a list of six look structurally identical.

**Workspace tools.** Highly flexible, and a student can build almost anything in one. That flexibility is the cost: the workload view has to be constructed and then maintained by hand. Under load, maintenance stops — precisely when the view is most needed.

**Calendar tools.** Excellent for scheduled events. But a calendar entry represents *time occupied*, not *effort required*. A free Wednesday afternoon looks identical whether the assignment due Thursday needs one hour or eight. Calendars also only contain what was entered, and a meaningful share of the target user's load never gets entered.

**Scheduling assistants.** The closest category, and genuinely useful. Two gaps remain. They assume the calendar is already complete, which for this user it is not — optimising an incomplete picture produces confident but partial results. And they tend toward automatic rearrangement, whereas the team's position is that a student must approve changes to their own week.

**Wellbeing applications.** Valuable, but a different product. They address how a student feels, not what they have committed to. They hold no deadline or effort data and therefore cannot change the workload that produced the stress. SEALY deliberately does not compete here — it does not make health claims and does not position itself as a wellbeing intervention.

---

## The Gap SEALY Targets

Stated as a single claim:

> Existing tools require the workload to already be digital, and then show it as a list of dates. Neither assumption holds for this user. A substantial part of the load exists only on paper or in messages, and dates without effort estimates cannot reveal whether a week is feasible.

SEALY's bet is that **capture friction** and **the absence of capacity reasoning** are the two gaps, and that closing both together produces something none of the categories above offers.

---

## Honest Assessment of Defensibility

Presented plainly, because a mentor or judge will ask.

**What is genuinely difficult to copy:**
- The combination of physical capture, cross-life aggregation, capacity reasoning, and human-approved rebalancing as one coherent journey
- The product decision to make confirmation mandatory, which is a positioning choice as much as a safety one

**What is not defensible on its own:**
- Camera capture as a feature. Any established tool could add image extraction. The differentiator is not the camera — it is what the extracted data feeds into.
- AI extraction. Widely available.

**The realistic position:** SEALY's advantage is coherence and focus on a specific user, not a technical moat. An established product could build these capabilities. The relevant question for a prototype is whether the combination is valuable and well-executed, not whether it is impossible to replicate.

**Risks to the positioning:**
- If students find effort estimation too burdensome, capacity reasoning degrades and SEALY converges toward a task manager
- If capture and review together cost as much effort as typing, the friction advantage disappears
- Scheduling assistants adding image capture would close the most visible gap

These are stated as risks rather than dismissed.

---

## What Would Strengthen This Analysis

Currently unverified. In order of value:

- [ ] Hands-on audit of two or three named products against the six capabilities, with dates and versions recorded
- [ ] Confirmation that no mainstream tool already offers structured extraction from photographed academic documents
- [ ] Sourced figures on student tool fragmentation, if any credible ones exist
- [ ] Any statistic used in the pitch traced to a retrievable citation

**Note:** figures on Malaysian student burnout appear in earlier project planning material without retrievable citations. They are deliberately **not** reproduced here and must be source-verified before appearing in any judge-facing document.

---

## Related Documents

- [Alternative Solution Directions](../ideation/idea-comparison.md)
- [Persona — Haziq](../ucd/persona.md)
- [Life Before and After SEALY](../ucd/life-before-after.md)
