# Persona — Haziq

> **Status: provisional design persona.** This persona is not based on a completed interview study and must not be presented as measured user research.

## Snapshot

**Haziq**, 21, university student, phone-first, managing classes, assignments, group work, deadlines, personal errands, social commitments and rest through several disconnected tools.

The Figma prototype currently uses **Alex** as a demo account name. Haziq remains the documentation persona; this is a presentation-data distinction, not two different target users.

## Core behaviour

Haziq can usually tell you each individual thing he needs to do. His problem is reconstructing the **combined picture** quickly enough to make a good decision.

His information may live in:

- course/assignment PDFs;
- screenshots;
- Google Calendar;
- WhatsApp / Teams / Telegram messages;
- email;
- course portals;
- notes;
- memory.

Under pressure he is least likely to maintain a complex productivity system, which makes manual setup a poor assumption.

## Primary needs

| Need | Product implication |
|---|---|
| Minimal setup | Import from existing sources |
| Understand today's real workload | show tasks behind the total |
| Know whether work fits | compare work-to-finish vs time-left |
| See urgency | show concrete shortfall/deadline |
| Get options, not lectures | propose Keep / Add / Move / Defer |
| Retain control | confirm/edit/dismiss system proposals |
| Familiar schedule model | Today/Week calendar |
| Avoid confusing terminology | simple titles and direct actions |
| Preserve access during Focus | only selected distractions are paused |

## Main frustration

A list can look manageable because every item is shown separately.

What he needs to know is:

> **Can I realistically complete all of this in the time I have?**

## Illustrative scenario

This is a constructed scenario, not a real quote.

Haziq has three academic work items left:

- ISP640 Project Plan — 90 min
- ICT652 presentation preparation — 65 min
- ASC486 Group Project — 60 min

That is **3h35** of estimated work. His calendar leaves **2h40** before the relevant deadlines.

Without a capacity view, he may simply start the first task and discover the problem later.

With SEAL, the home screen immediately says **55 min short** and lets him inspect the tasks creating the total.

If he chooses **Adjust My Plan**, SEAL can show alternatives. He can keep urgent work, move later-deadline work, defer something whose deadline changed, or ask for another arrangement.

## Why low-input matters

A student who is already overloaded is unlikely to spend twenty minutes configuring a new productivity system.

That is why Mentor #1 changed the design goal from:

> “How quickly can Haziq type a task?”

into:

> **“How much useful structure can SEAL produce from information Haziq already has?”**

## Why simple wording matters

Mentor #2 changed a second assumption: even if the engine is correct, it fails if Haziq must learn what “Schedule Pressure”, “Mental Load 72%” or “Rebalance Mode” means.

The UI therefore prefers:

- Work to finish
- Time left today
- 55 min short
- Adjust My Plan
- Focus
- Take a Break

## Research gaps

- Persona not yet validated with a formal interview sample.
- Effort-estimation behaviour not validated.
- Acceptance of generated schedule alternatives not validated.
- Whether “Add” is understood as “generate another plan” needs testing.
- Whether the Island improves comprehension needs testing.

## Related documents

- [Life Before and After SEAL](life-before-after.md)
- [Idea Comparison](../ideation/idea-comparison.md)
- [Evolution Log](../ideation/SEAL_Ideation_and_Prototype_Evolution_Log.md)
