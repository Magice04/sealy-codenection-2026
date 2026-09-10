# SEALY / SEAL — Progress & Outstanding Work

*Written 2026-09-10 after auditing the whole `sealy-codenection-2026` repo,
the loose files beside it, and this project's Figma work (design prototype
+ FigJam ideation board). This file is meant to be the one place that says
honestly what exists, what's missing, and what needs a decision before
anyone builds further.*

---

## ⚠️ Read this first — there are two different product directions in this folder

The repo currently contains **two versions of the same hackathon entry that
disagree with each other**, and only one of them is actually committed.

| | **Track A — "SEALY"** (what's in `git` right now) | **Track B — "SEAL"** (drafted, not committed) |
|---|---|---|
| Where it lives | `README.md` (repo root, tracked), everything in `docs/`, `prototype/README.md`, `presentation/README.md` | `README-1.md` (sitting in the repo folder but **not** the tracked README) and `Claude outputs/README.md` (outside the repo entirely) |
| App name | SEALY | SEAL |
| Core mechanic | Camera/photo → AI (OCR) task capture is the headline differentiator; workload capacity is computed from captured tasks | Island/mascot + a **Capacity + Rebalance Engine** is the headline differentiator; OCR capture was explored and explicitly *dropped* (see Idea 02 in the ideation log) |
| Tech stack | React Native + Expo (mobile), Vercel serverless, Claude API | React + Vite + Tailwind (**web**, not mobile), Zustand, Supabase client SDK directly, one Supabase Edge Function |
| Ideation record | `docs/ideation/SEALY_Ideation_and_Prototype_Evolution_Log.md`, `docs/ideation/idea-comparison.md` — 5 broad directions compared, SEALY (capacity manager) selected | 9-idea FigJam network — SEAL (Capacity+Rebalance Engine) selected via a different, later exploration |
| Design file | Same underlying Figma file (`Y2ce2KYSTXDkNBqLAMcfaF`) — this file *is* the pivot: it started as "Sealy" and is being redesigned in place as "SEAL: Student Equilibrium & Load" | same file |
| Mentor log | Templates say **no mentor session has been held** | README §2.3 implies a mentor session happened 2026-09-09 but the actual feedback was never filled in — still a placeholder |

**What this means:** the design prototype (Figma) has already pivoted from
SEALY to SEAL, and a rewritten README for that pivot exists — but it was
never committed as the repo's actual `README.md`, so anyone opening the
GitHub repo today sees the *old*, pre-pivot SEALY story (camera capture,
mobile app, no mentor session), which no longer matches the Figma file or
the more recent ideation work.

**This has to be resolved by the team, not guessed at** — the two tracks
imply different app names, different core mechanics, and different tech
stacks (mobile vs. web). Nothing below assumes one or the other; it lists
what's true for each.

There's a second, related open question already flagged inside the repo
itself (`SEALY_Ideation_and_Prototype_Evolution_Log.md`, "Open Questions
Carried Forward"): the evolution log names a Building Phase of **21
September – 11 October**, while other planning material treats **13
September 23:59** as the final submission deadline. These can't both be
right, and if the real deadline is 13 September, that's 3 days away with
**no application code written in either track.**

---

## What's actually done

**Documentation / ideation (Track A, committed):**
- Problem statement, persona (Haziq), life-before/after, competitor
  analysis — all written (`docs/ucd/`, `docs/research/`)
- 5-direction comparison matrix with scoring and rationale
  (`docs/ideation/idea-comparison.md`)
- Full iteration history (Iteration 0 → 2) in the evolution log
- AI-responsibility split and technical-feasibility docs
  (`docs/architecture/`)
- Mentor consultation templates prepared (not filled in)

**Ideation (Track B, drafted but not committed to the repo):**
- 9-idea "what we tried and dropped" story with a kept/dropped table
  (README-1.md §2.1)
- An 11-file FigJam network: 1 Main Hub + 9 per-idea boards + 1 Final
  Concept board, all cross-linked
- **As of today**, the Main Hub board was rebuilt into the Sealy team's
  actual **figjam project folder** (it previously lived in personal
  Drafts) and had a full layout cleanup pass: deduplicated a legacy
  section, reorganized into a left-to-right story (Problem → 4 early
  ideas → evolution/merge column → Capacity(chosen) → Recovery → Final,
  with Gamification feeding in), fixed every connector and overlap found
  during a full visual audit. Current links:

  | File | URL |
  |---|---|
  | Main Hub | https://www.figma.com/board/IzgiS7JIiu6L6mi7dsSoga |
  | 01 Chatbot Companion | https://www.figma.com/board/kODR5FXZe6ln27mRbUDIkV |
  | 02 Photo/OCR Task Capture | https://www.figma.com/board/xyq1xbZWRMeaQlR0LZz5ch |
  | 03 Holistic Life Balance | https://www.figma.com/board/fliaUZm9Grb6hiEr6ozEXk |
  | 04 Focus/Pomodoro | https://www.figma.com/board/UyevwwpsSdYu2r1CfXgP9c |
  | 05 Strict Lock-In | https://www.figma.com/board/D0w8RgpbVAI2qRIxfWkhkS |
  | 06 Behaviour-Aware Focus | https://www.figma.com/board/Vbq3HT39GnVxr34mDfXDLG |
  | 07 Capacity + Rebalance Engine | https://www.figma.com/board/LHiaomOlQUwuqjxvVENWhV |
  | 08 Recovery + Balance | https://www.figma.com/board/ZEALlyR7lwnBjdHgGahZNu |
  | 09 Island + Seal Gamification | https://www.figma.com/board/z3zfW7O2rg0UYnW5ZAFilV |
  | Final SEAL Concept | https://www.figma.com/board/iBVX4pAcKUPuNpuEijOWuM |

  **`README-1.md` and `Claude outputs/README.md` still link to the OLD,
  superseded Drafts-folder copies of these files, not the links above —
  they need updating regardless of which track ships.**
- A rewritten README (README-1.md) including a full technical-design
  appendix: use case diagram, class diagram, two sequence diagrams, ER
  diagram + data dictionary, package structure — all written against the
  Track B (web/Supabase) stack

**Design prototype (shared by both tracks — same Figma file):**
- A clickable design prototype exists: 28 connected screens across
  AUTH/ONBOARDING/CORE, plus concept/v2 screens, a design system
  (foundations + component library), and a 13-section UX/iteration
  evidence page
- A full 13-pose mascot library, rebuilt as native Figma vectors to fix a
  transparency bug, with all ~44 mascot placements re-swapped to
  mood-appropriate poses
- The "Judge Demo" flow (Island → Rebalance → Focus Lock-In → Distraction
  → Recovery) is fully wired end-to-end; a broader "Full Experience" flow
  (Login/Signup → Onboarding → Island) is also wired with a few known gaps
  (no Splash screen, no Connect-Calendar screen, no Island-Intro screen)
- Figma link: `https://www.figma.com/design/Y2ce2KYSTXDkNBqLAMcfaF/`
  — **sharing has not been verified as public** in either track

**Application code:** none, in either track. No `app/` or `src/`
directory exists. This is the single biggest gap regardless of which
track is chosen.

---

## What's NOT done yet (everything outstanding, deduplicated across both tracks' TODO lists)

**Decisions that block everything else:**
- [ ] **Resolve SEALY vs. SEAL** — confirm which product direction, name,
      and tech stack (mobile/Expo vs. web/Vite) is actually shipping, then
      make the repo's `README.md` and `docs/` match it. Whichever one
      loses should either be deleted or clearly marked superseded, not
      left as a second live-looking README.
- [ ] **Confirm the real submission deadline** — 13 September vs. the
      21 September–11 October Building Phase mentioned in the evolution
      log. This changes everything about urgency and scope.

**Team / people:**
- [ ] Real member names (both READMEs still have `[Member 1]` / `[Member 2]` placeholders)
- [ ] Confirm the actual assigned mentors for both consultation slots (both mentor docs say "to be confirmed")
- [ ] Hold Mentor Consultation #1 and #2, and actually fill in what was said (both currently 100% template, "NOT YET HELD")
- [ ] Add a post-mentor iteration entry to the evolution log after each session
- [ ] If Track B's README §2.3 mentor note (2026-09-09, Lim Zi Yang) is real, fill in what was actually said and what changed as a result — it's currently a `[TODO]`

**Figma / design:**
- [ ] Set all Figma links (the design prototype file **and** all 11 FigJam files) to "Anyone with the link can view," and verify each opens in an incognito/signed-out window
- [ ] Delete the 11 superseded FigJam files still sitting in Drafts (duplicates of the current folder-based set)
- [ ] Export prototype screenshots into the repo (`prototype/README.md` says none exist yet) so the repo stands on its own without requiring Figma access
- [ ] Close the remaining prototype gaps: Splash screen, Connect-Calendar screen, Island-Intro screen; duration-chip selected-state on Lock-In Setup doesn't visually update; Insights secondary cards aren't clickable; Settings/Profile/Privacy screens aren't built at all
- [ ] Track A also still lists as not started: problem tree diagram, mind map image, user-flow diagram (Track B substitutes Mermaid diagrams inline in the README for some of these — worth confirming that's an accepted substitute)

**Application build — nothing exists yet in either track:**
- [ ] Auth (email/password) + onboarding
- [ ] Core dashboard (Island load view, in Track B's language) with its different load states
- [ ] The Rebalance flow, backed by real logic (Edge Function in Track B's plan)
- [ ] Focus Lock-In with the mocked distraction simulator
- [ ] Recovery flow
- [ ] Mascot mood system driven by real app state (not just static Figma poses)
- [ ] Camera capture → AI extraction → human confirmation pipeline — **only relevant if Track A (SEALY) ships**; Track B dropped this at the ideation stage
- [ ] Whichever stack is chosen: repo scaffold, database schema, deployment (Vercel + Supabase in both tracks' plans)

**Presentation / submission materials — not started in either track:**
- [ ] Slide deck
- [ ] ≤5-minute unlisted demo video (problem → solution → why novel → how it'll be built → why it deserves to be built)
- [ ] Pitch notes / rehearsed answers to likely judge questions
- [ ] Make the GitHub repo public with the correct README at the root
- [ ] Every statistic used anywhere must be sourced or removed — both tracks flag that early planning material contains unsourced burnout/stress statistics

**Validation (nice-to-have, explicitly flagged as not done in Track A):**
- [ ] Test the core assumption ("students can't see their aggregate workload") with real students — currently based only on team judgement
- [ ] Verify whether effort self-estimation by students is reliable enough for the capacity calculation to mean anything — flagged as the largest open risk to the concept in both tracks

---

## Suggested immediate next steps

1. Get the team in a room (or a call) and settle SEALY vs. SEAL and the
   deadline question above — everything else is downstream of these two
   decisions.
2. Once settled, replace/update the root `README.md` so there is exactly
   one canonical story, and archive or delete the losing track's files
   rather than leaving both in the repo.
3. Fix the FigJam links inside whichever README survives (see the table
   above — the current, correct links are already listed here).
4. Set every Figma/FigJam sharing setting to public and verify in an
   incognito window.
5. Start the actual build — even a thin, honestly-labelled working slice
   beats a design-only submission on the feasibility/technical criteria,
   per both tracks' own notes.

---

*Sources reviewed for this file: `README.md`, `README-1.md`, `Claude
outputs/README.md`, everything under `docs/`, `prototype/README.md`,
`presentation/README.md`, this project's `hackathon-submission-progress.md`
and `seal-pivot-progress.md` records, and the current state of the Figma
design file and FigJam ideation board.*
