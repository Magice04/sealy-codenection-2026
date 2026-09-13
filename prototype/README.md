# SEAL — Prototype

> **Current state: connected Figma prototype; no application implementation is claimed.**

Figma: https://www.figma.com/design/Y2ce2KYSTXDkNBqLAMcfaF/

## Prototype goal

The prototype should answer one question without the team narrating every screen:

> **What work do I still need to do, how much time do I have left, and what should I do next?**

## Main current flow

```text
Import your work
→ OCR / structure candidate
→ confirm / edit
→ Today / Week Plan
→ Work to finish 3h35
→ Time left 2h40
→ 55 min short
→ Adjust My Plan
→ Keep / Add / Move / Defer
→ Confirm plan
→ Focus
```

Take-a-Break/Recovery remains part of the intervention model and can be shown when immediate urgency is manageable.

## Major Mentor #2 changes now present

### Home / Island

Old emphasis:

- Time free today
- Work due today
- Schedule pressure: Very high

Current emphasis:

- **Work to finish — 3h35**
- **Time left today — 2h40**
- **55 min short**
- preview of the actual tasks making up the total

The Island remains a visual feedback layer below the actionable content.

### Today Plan

The current example shows academic context instead of generic “Lecture / Tutorial / Lab” rows. The demo includes course codes, class/task context, lecturer text and duration/deadline information.

### Week Plan

A clickable Google-Calendar-inspired Week view now exists. It includes:

- Monday–Friday columns;
- time grid;
- course blocks;
- selected task preview;
- link into task detail.

### Task detail

The main demo task is **ISP640 Project Plan**, with course context, deadline, estimated work, requirements and suggested breakdown.

### Adjust My Plan

The underlying Figma frame may still contain `Rebalance` in its internal name, but user-facing copy says **Adjust**.

The task menu contains exactly:

| Action | Prototype |
|---|---|
| Keep | confirmation + mascot; no change |
| Add | five alternative plan screens; confirm one |
| Move | week-calendar drag concept + overlap warning |
| Defer | choose “deadline changed” or “not urgent anymore” |

### Applied-plan example

Before:

```text
Work to finish  3h35
Time left       2h40
55m short
```

After moving a later-deadline item:

```text
Work after plan 2h35
Time left       2h40
5m spare
```

### Focus

The app rule is explicit:

> **Only apps you select are paused. Everything else stays available during Focus.**

This is a simulated UX rule. Native blocking is not implemented.

### Import / Capture

The source picker is now **Import your work**.

Visible sources include:

- Camera
- Gallery
- Share to SEAL
- Calendar
- Email
- shared-app options
- paste-text fallback

The OCR example uses an ISP640 assignment brief to demonstrate extracting a real-looking task/deadline/requirements/subtask structure.

### Insights

Distinct clickable views now exist for:

- 7 Days
- 30 Days
- Semester

Each has different example metrics/content. They are static demonstration data, not a live analytics engine.

## Academic demo content

The current prototype uses course/assignment PDFs supplied by the team to make the scenario coherent. For example, the ISP640 documents provide course/lecturer/assessment/deadline context used in the task preview.

These files serve as **prototype fixture data**. They are not user-research evidence and do not prove the app can parse arbitrary PDFs in production.

## Interactive vs simulated

| Feature | Figma interaction | Working implementation |
|---|---:|---:|
| Navigate Import flow | Yes | No |
| OCR result screen | Yes | No live OCR |
| Confirm/edit candidate | Simulated navigation | No persistence |
| Today / Week switch | Yes | No live calendar |
| Work/time arithmetic | Fixed example | No calculation service |
| Keep/Add/Move/Defer | Yes | No scheduling engine |
| Drag Move demo | Prototype interaction | No calendar write |
| App pause configuration | Yes | No native enforcement |
| 7/30/Semester Insights | Yes | No live analytics |
| Island state | Yes | No computed state |

## What judges should be able to understand

Without narration, the prototype should communicate:

1. what work creates the total;
2. that 3h35 > 2h40;
3. why that means 55 minutes are missing;
4. that SEAL offers plan options instead of only reporting the problem;
5. that the student confirms the action;
6. that the system becomes simpler once the plan fits.

## Known UX questions

- Is **Add** understood as “generate another plan”? The team requested this label, but it may still need validation.
- Does “Time left today” clearly mean usable time before relevant deadlines?
- Is the two-overlapping-items Move rule understandable and necessary?
- Does the Island communicate useful state or merely add atmosphere?
- Are 30-day/Semester insights valuable enough to show in the final 3–5 minute video?

## Related documents

- [Project README](../README.md)
- [Mentor #2](../docs/mentor-feedback/mentor-02-sep12.md)
- [Technical Feasibility](../docs/architecture/technical-feasibility.md)
- [Evolution Log](../docs/ideation/SEAL_Ideation_and_Prototype_Evolution_Log.md)
