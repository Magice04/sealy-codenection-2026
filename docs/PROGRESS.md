# SEAL — Progress & Outstanding Work

*Updated 13 September 2026 after Mentor #2 / Janelle follow-up and the latest Figma revision.*

## Current truth

There is no longer a product-direction split: **SEAL — Student Equilibrium & Load** is the active concept. The repository name still contains `sealy` for continuity. SEALY is only an archived early chatbot-oriented iteration.

The current deliverable is **documentation + ideation + a connected Figma prototype**. No application implementation is claimed.

## What is done

### Product direction

- [x] Core problem narrowed from broad “student stress” to workload understanding and intervention.
- [x] Core model simplified to **Work to finish vs Time / capacity left**.
- [x] Three internal interventions retained: Focus / Rebalance / Recover.
- [x] Student-facing wording simplified to **Focus / Adjust My Plan / Take a Break**.
- [x] Five original load dimensions demoted from primary UI model to supporting context.
- [x] “Low input, high output” principle adopted after Mentor #1.
- [x] “Complex underneath, simple on screen” principle adopted after Mentor #2.

### Latest Figma prototype

- [x] Home card shows **3h35 work to finish**, **2h40 time left**, **55m short**.
- [x] Home shows the specific tasks behind the 3h35 total.
- [x] User-facing Rebalance language changed to **Adjust**.
- [x] Urgent work preview added before adjustment actions.
- [x] Adjustment menu reduced to **Keep / Add / Move / Defer**.
- [x] Keep confirmation screen with mascot.
- [x] Add flow with five alternative SEAL-generated prototype arrangements.
- [x] Move flow with phone-calendar layout, drag interaction and overlap warning.
- [x] Defer flow asks whether deadline changed or task is no longer urgent.
- [x] Today Plan uses course/lecturer/duration/deadline context.
- [x] Week calendar screen added and linked from Today.
- [x] Task detail updated to ISP640 Project Plan sample.
- [x] Focus copy clarifies: only selected apps are paused; all other apps remain available.
- [x] Capture renamed to **Import your work** and framed around information already living elsewhere.
- [x] OCR/import example updated to ISP640 assignment brief.
- [x] Distinct 7 Days / 30 Days / Semester Insight screens created.
- [x] Stale Database Assignment / generic demo data removed from the main flow where found.

### Mentor evidence

- [x] Mentor #1 feedback recorded.
- [x] Mentor #1 product changes represented in ideation/prototype direction.
- [x] Mentor #2 feedback from Janelle recorded.
- [x] Mentor #2 changes applied to the Figma prototype.
- [x] Evolution log updated with the second mentor pivot.

## Current demo arithmetic

```text
ISP640 Project Plan             90m
ICT652 presentation prep        65m
ASC486 Group Project            60m
                               ----
Work to finish                3h35m
Time left today               2h40m
Shortfall                       55m
```

An adjusted example moves the later-deadline ASC486 work:

```text
Work after plan               2h35m
Time left today               2h40m
Spare                            5m
```

These are fixed prototype examples, not live calculations.

## What is not implemented

- [ ] React Native / Expo application
- [ ] Supabase schema / RLS
- [ ] real Google Calendar OAuth/API integration
- [ ] real OCR pipeline
- [ ] persistence of extracted tasks
- [ ] deterministic calculation running in code
- [ ] native app-blocking integration
- [ ] real drag-and-drop scheduler
- [ ] live Insights history
- [ ] Telegram intake
- [ ] headless-browser agent

The absence of implementation must remain explicit in the README, prototype notes and presentation.

## Priority before final submission

1. **Verify Figma sharing** from a signed-out browser.
2. **Walk the prototype from beginning to end** and repair any dead interaction that affects the demo spine.
3. **Export 4–8 key screenshots** for the repository/submission.
4. **Finish pitch/slides/video** and keep them consistent with the revised UI language.
5. **Do not update the Word submission draft in this pass** — the user explicitly excluded it.
6. Replace remaining stale “SEALY” or unexplained “Rebalance” wording only when it is not intentional archived-history evidence.
7. Confirm team names and any remaining submission placeholders.

## Recommended demonstration spine

```text
Import your work
→ Confirm structured item
→ Today / Week Plan
→ 3h35 work vs 2h40 left
→ 55m short
→ Adjust My Plan
→ Keep / Add / Move / Defer
→ Confirm an arrangement
→ Focus
→ Insights (7 Days / 30 Days / Semester)
```

## Open decisions

- Exact OCR provider for a build.
- Whether task decomposition is rule-based, AI-assisted, or both.
- Whether the final presentation uses the internal term “Rebalance” at all; recommended approach is to explain it once, then use “Adjust My Plan” for the user experience.
- Which 4–8 Figma screenshots become official submission evidence.

## Documents updated in this pass

- `README.md`
- `README-1.md`
- `docs/PROGRESS.md`
- `docs/architecture/ai-responsibility.md`
- `docs/architecture/technical-feasibility.md`
- `docs/ideation/SEAL_Ideation_and_Prototype_Evolution_Log.md`
- `docs/ideation/idea-comparison.md`
- `docs/mentor-feedback/mentor-01-sep10.md`
- `docs/mentor-feedback/mentor-02-sep12.md`
- `docs/research/competitor-analysis.md`
- `docs/ucd/life-before-after.md`
- `docs/ucd/persona.md`
- `presentation/README.md`
- `prototype/README.md`
