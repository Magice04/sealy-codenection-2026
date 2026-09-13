# SEAL — Presentation Materials

This directory tracks presentation work. The official CodeNection deliverable includes a **3–5 minute** unlisted video plus submission links.

## Current presentation story

Do not lead with the five loads. Lead with the concrete capacity problem.

### 1. Problem

> Students' work is scattered across PDFs, calendars, messages, screenshots and memory. Even when they know the tasks, they still have to reconstruct whether everything fits.

### 2. Concrete example

```text
Work to finish: 3h35
Time left:      2h40
Shortfall:        55m
```

### 3. SEAL's answer

> **Focus if it fits. Adjust if it does not. Take a Break when continuing is not the right next action.**

### 4. Low-input direction

Show **Import your work**:

Camera / Gallery / Share / Calendar / Email / Paste → structured candidate → user confirmation.

### 5. Adjustment demo

Show exactly four options:

- Keep
- Add (another SEAL-generated plan)
- Move
- Defer

### 6. Plan

Show Today and Week. Do not explain generic architecture while the judge is trying to understand the user flow.

### 7. Insights

Briefly prove 7 Days / 30 Days / Semester exist. Do not spend a full minute reading every metric.

## Recommended 3–5 minute video timing

| Time | Content |
|---|---|
| 0:00–0:30 | problem + scattered sources |
| 0:30–0:55 | 3h35 vs 2h40 → 55m short |
| 0:55–1:30 | Import your work + confirmation |
| 1:30–2:30 | Adjust My Plan + Keep/Add/Move/Defer |
| 2:30–3:05 | Focus + selected-app pause rule |
| 3:05–3:30 | Week + Insights |
| 3:30–4:00 | differentiation + mentor evolution + honest feasibility |

If the final video is closer to 3 minutes, shorten Week/Insights before shortening the core 55-minute example.

## Mentor-facing short script

> “SEAL helps students bring scattered work into one place and answer a simple question: does the work I still need to do actually fit the time I have left? In this example, there are 3 hours 35 minutes of work but only 2 hours 40 minutes left, so SEAL shows a 55-minute shortfall. Instead of telling the student to focus harder, it suggests Adjust My Plan. The student can Keep, ask for another arrangement, Move, or Defer a task. Once the plan fits, SEAL can recommend Focus. We keep the intelligence underneath, but the UI uses simple language.”

## Technical answer if asked

> “React Native and Expo with TypeScript for mobile, Supabase/PostgreSQL for backend and auth, Google Calendar API for schedule context, OCR for low-input import, and a deterministic workload-capacity engine for the recommendation. AI can assist extraction or decomposition, but the core arithmetic does not depend on AI.”

## Language rules

### Prefer

- work to finish
- time left today
- 55 min short
- adjust my plan
- focus
- take a break
- imported work
- candidate task
- user confirmation

### Avoid in the UI

- mental load percentage
- schedule pressure percentage
- intervention engine
- rebalance mode
- cognitive load score

These terms may appear in internal architecture/ideation history where they are explained.

### Never claim

- burnout diagnosis/prediction
- medical stress detection
- scientifically validated five-load score
- working autonomous portal agent
- working app blocking just because Figma demonstrates it

## Assets

| Asset | Status |
|---|---|
| Figma prototype | Updated after Mentor #2 |
| Slide deck | Team to confirm |
| Demo video | Team to confirm |
| Pitch notes | This file now contains the recommended spine |
| Key screenshots | Still need export into repository if not already done |

## Final pre-submission checks

- [ ] Figma accessible while signed out
- [ ] public GitHub repository current
- [ ] README matches latest Figma wording
- [ ] mentor #1 and #2 records included
- [ ] Word submission draft intentionally handled separately from this repo update
- [ ] slide/video links real, not placeholders
- [ ] no “feature works” claim based only on prototype navigation
- [ ] 3–5 minute video within time
