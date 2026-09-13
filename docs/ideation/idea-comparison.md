# SEAL — Idea Comparison and Decision Rationale

This file summarizes the ideation path. The full chronology is in the [evolution log](SEAL_Ideation_and_Prototype_Evolution_Log.md).

## Ideas considered

| # | Direction | What worked | Why it was not enough alone | Current status |
|---|---|---|---|---|
| 01 | SEALY chatbot companion | emotional support / conversational character | chat-first workflow adds friction and is not the workload solution | **Dropped as core; mascot kept** |
| 02 | Photo / OCR task capture | extremely low input friction | OCR-to-task is an input feature, not the decision layer | **Revisited after Mentor #1 as primary import path** |
| 03 | Holistic five-load score | acknowledged life outside academics | single composite score is arbitrary and difficult to explain | **No composite score; context kept** |
| 04 | Pomodoro | helps starting work | assumes working harder is the answer | **Focus mechanic kept** |
| 05 | Strict lock-in | reduces selected distractions | can be punitive; native enforcement is complex | **Simplified “pause selected apps” concept** |
| 06 | Behaviour-aware focus | recognises start/distraction patterns | surfaced the bigger capacity problem | **Insight kept** |
| 07 | Capacity + Rebalance Engine | detects when work does not fit time | terminology was too technical for users | **Core engine; UI now says Adjust My Plan** |
| 08 | Recovery + Balance | makes rest a first-class action | needs non-clinical signals and clear boundaries | **Kept as Take a Break** |
| 09 | Island + Seal | understandable visual/emotional layer | can become decoration if disconnected from the decision | **Kept as supporting experience** |

## Why Idea 07 became the core

The key scenario is not “a student has many tasks”. Every task manager can show that.

The key scenario is:

```text
Work to finish = 3h35
Time left      = 2h40
Shortfall      = 55m
```

That creates a decision problem: a focus timer cannot manufacture the missing 55 minutes.

SEAL therefore acts as a **decision layer**:

- if the plan fits → Focus;
- if the plan does not fit → Adjust;
- if immediate urgency is manageable and recovery need is high → Take a Break.

## Mentor #1 changed the input side

Before Mentor #1, the concept still assumed too much deliberate task entry.

Mentor #1 pushed the team toward:

- OCR/photo as low-friction capture;
- extraction/structuring before the user manually organizes anything;
- optional task decomposition;
- future Telegram / agentic / headless-browser source exploration;
- user confirmation after system interpretation.

This did **not** replace the capacity engine. It improved how data reaches it.

## Mentor #2 changed the communication side

Mentor #2 / Janelle identified that the system still required too much explanation.

The five-load framing and terms such as “schedule pressure” / “rebalance” obscured the simple core. The response was:

```text
Earlier UI                Current UI
----------                ----------
Time free today      →    Work to finish / Time left today
Schedule pressure    →    55 min short
Rebalance            →    Adjust My Plan
Five load scores     →    direct context + one clear recommendation
Generic plan entries →    course/task/lecturer/duration context
```

The design principle is now:

> **The user should understand the conclusion before they understand the engine.**

## Current final concept

```text
Import from existing sources
        ↓
Structure / optional decomposition
        ↓
Human confirmation
        ↓
Workload-capacity calculation
        ↓
Focus / Adjust / Take a Break
        ↓
Plan + Island + Insights
```

## What is specifically novel in our concept

The claim is intentionally narrow. SEAL does not claim OCR, calendars, Pomodoro or mascots are individually novel.

The product hypothesis is that the useful combination is:

1. low-friction multi-source intake;
2. explicit effort + deadline structure;
3. transparent **work-to-finish vs time-left** reasoning;
4. action selection rather than passive reporting;
5. human-approved plan changes;
6. recovery as a valid outcome.

This is a product-positioning hypothesis, not a claim that no product anywhere has ever implemented similar capabilities.
