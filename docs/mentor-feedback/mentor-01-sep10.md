# Mentor Consultation #1 — First Feedback Record

> ## STATUS: FEEDBACK RECORDED
>
> The first mentor feedback has now been recorded from the team's notes. The exact mentor identity, session format, and actual consultation date were **not included in the notes supplied for this update**, so those fields remain explicitly unconfirmed rather than being guessed.
>
> This document separates **what the mentor said** from **what the team plans to do next**. Planned actions must not be presented as implemented features until there is repository or prototype evidence.

---

## Session Details

| Field | Value |
|---|---|
| Session | Mentor Consultation #1 |
| Originally scheduled | 10 September 2026 |
| Actual date held | **To confirm** |
| Mentor | **To confirm** |
| Format | **To confirm** |
| SEAL attendees | **To complete** |
| Prototype / ideation state shown | SEAL ideation around low-friction workload capture, Focus / Rebalance / Recover, Calendar input, OCR, and workload-capacity reasoning |
| Record status | Feedback captured from team notes; identifying/session details still need confirmation |

> **Repository consistency note:** another draft document currently contains a different mentor date/name placeholder. Confirm the real consultation details before submission and make all files consistent.

---

## Core Mentor Message

The strongest theme across the session was **input-to-output efficiency**:

> A student should do as little work as possible to give SEAL enough information, while SEAL should return as much useful structure and action as possible.

The mentor challenged the team not to stop at a conventional task-entry interface. If a student must already remember every task, understand it, estimate it, and manually type it into SEAL, then the product is still asking the user to perform much of the difficult work themselves.

This reframes the input problem from:

> “How can the student enter a task quickly?”

into:

> **“How can SEAL discover, compile, structure, and clarify a student's responsibilities with minimal deliberate input from the student?”**

---

## Feedback Received

| # | Theme | Mentor feedback captured from the session |
|---|---|---|
| 1 | **Be more creative than manual input** | Do not rely on a simple input form as the main capture idea. Explore more creative ways for SEAL to receive responsibilities and commitments. |
| 2 | **Reduce memory burden** | The user should not need to remember every task upfront before the app becomes useful. The product should help discover or collect what needs to be done. |
| 3 | **Keep OCR as a strong capture path** | OCR was positively received: the user can send/take a photo and SEAL can extract what is written instead of requiring full manual transcription. |
| 4 | **Break work into subtasks** | A captured responsibility may still be too large or vague. SEAL should be able to split a task into smaller, more actionable subtasks. |
| 5 | **Explore agentic / headless-browser collection** | The mentor referenced an OpenClaw / Claude-computer style direction: a programmatically controlled browser running headlessly (without a normal GUI) could visit web pages that the user authorises, collect responsibilities from different sites, and compile them. |
| 6 | **Aggregate across the student's digital life** | Rather than making the student visit every source and manually copy information, explore whether SEAL can compound tasks from multiple sources into one workload picture. |
| 7 | **Telegram / service integrations** | Telegram has APIs/bots that could become another low-friction source. A bot could receive messages or structured commands and pass events/tasks toward Calendar / SEAL after confirmation. |
| 8 | **Narrow the broad problem** | “Stress & workload” is extremely broad. Choose a sharper problem inside the challenge instead of trying to solve every possible student-life problem at once. |
| 9 | **Maximise creative exploration** | The challenge gives room for many possible solution shapes. Demonstrate that the team explored more than the obvious task-manager / form-input approach. |
| 10 | **Agentic framing** | The mentor encouraged the team to think in an agentic direction: SEAL should not merely store information; it can actively gather, structure, compile, and propose actions. |
| 11 | **Auto-switching should remain user-controlled** | Automatically determining a likely Focus / Rebalance / Recover state is useful, but the product should give a suggestion and ask the user rather than forcing a mode change. |
| 12 | **Simple confirmations are good** | When SEAL has already done the difficult interpretation work, the user's interaction can be as small as Yes / No / Edit / Confirm. |
| 13 | **Minimise learning cost** | Ask how difficult the UI is to learn. A powerful system still fails if students must understand a complicated workflow before receiving value. |
| 14 | **Pitch the technical ambition clearly** | The mentor encouraged using current technical language such as “agentic” where it is accurate and helps communicate the direction. Do not let the project sound like only a basic CRUD task app. |

---

## Direct Notes Preserved From the Session

The following phrases are preserved from the team's raw notes so the original intent is not lost:

> “More creative ways to do the feature.”  
> “Not just input simple.”  
> “Input need to know the task upfront.”  
> “How do u remember what to do.”  
> “Can be split down into different sub task.”  
> “Can u help me compound all the tasks and the browser will compile it for you.”  
> “Ocr is good send photo and u get everything written out.”  
> “Telegram had api that u can use, can connect telegram bot into calendar.”  
> “Thousand ways that can solve.”  
> “Problem statement is too broad, one problem.”  
> “Auto switching is a good idea or should the app let the user? (Can give suggestions, ask user about it).”  
> “If u ask yes no its simple.”  
> “How much u need them to do the tasks vs how much output.”  
> “How hard the user to learn to user your UI.”

---

## Team Interpretation

### 1. The main UX metric becomes **input effort vs. useful output**

A useful way to evaluate every capture mechanism is:

```text
User effort required
        ↓
Information SEAL receives
        ↓
Structure SEAL can create
        ↓
Useful action returned to the user
```

A strong feature should move as much work as possible from the student to the system **without removing user control**.

Example:

```text
Student takes one photo
        ↓
OCR extracts five responsibilities
        ↓
SEAL identifies possible tasks / events / deadlines
        ↓
SEAL proposes subtasks and estimated schedule impact
        ↓
Student only reviews: Yes / No / Edit
```

This is much stronger than asking the student to create five tasks manually.

### 2. “Manual task entry” should not be the product's creative centre

Manual entry may still exist as a fallback, but it should not be presented as SEAL's main innovation.

The more interesting capture directions are:

- **OCR / image capture** — photo of timetable, assignment sheet, whiteboard, handwritten list, notice, or screenshot.
- **Intentional share-to-SEAL** — user explicitly shares text/messages/screenshots into SEAL rather than SEAL silently reading private chats.
- **Calendar integration** — structured commitments already in the student's calendar.
- **Telegram bot / API integration** — user forwards or sends content to a bot, which proposes an event/task for confirmation.
- **Agentic browser collection** — with explicit user authorisation, a headless browser could inspect supported portals/websites and compile candidate responsibilities.

### 3. The sharper core problem to validate

The mentor's “one problem” challenge suggests narrowing from generic student stress to something closer to:

> **Students' responsibilities are fragmented across calendars, portals, messages, screenshots, documents, and memory, so they expend too much effort reconstructing what they need to do before they can even decide whether their workload fits.**

SEAL's proposed response becomes:

> **Collect → Structure → Decompose → Compare Capacity → Recommend**

This narrower framing still supports Focus / Rebalance / Recover, but gives the product a clearer entry problem to solve.

**This refined problem statement is a team interpretation of the mentor feedback and still needs validation.**

---

## Proposed Product Evolution After Mentor #1

### Previous simplified flow

```text
User enters tasks
      ↓
SEAL reads Calendar
      ↓
Load Engine
      ↓
Focus / Rebalance / Recover
```

### Mentor-informed direction

```text
                 LOW-FRICTION SOURCES

 OCR / Photo      Calendar       Telegram / Share
      \              |               /
       \             |              /
        \            |             /
         └────── Candidate Intake ─┘
                      |
                      v
             Extract + Structure
                      |
                      v
               Task Decomposition
                      |
                      v
                User Confirmation
              Yes / No / Edit
                      |
                      v
                 Load Engine
        Workload vs Available Capacity
                      |
            ┌─────────┼─────────┐
            v         v         v
          FOCUS   REBALANCE   RECOVER
                      |
                      v
             Suggest, don't force
```

### Agentic extension / exploration

```text
Authorised student portal / website
              ↓
      Headless browser agent
              ↓
 Navigate / inspect supported pages
              ↓
 Extract candidate deadlines / tasks
              ↓
 Normalise + deduplicate
              ↓
 Ask user to confirm
              ↓
 Feed confirmed items to Load Engine
```

This is an **exploration direction**, not a claim that unrestricted browser automation is already implemented.

---

## Technical Notes From the Mentor Direction

### Headless browser / “mini computer” concept

A headless browser is a browser process controlled programmatically without requiring the normal visible Chrome UI. A service can issue commands to navigate pages, click, read text, or extract structured information.

Potential SEAL use:

1. The student explicitly connects or authorises a supported portal.
2. An agent opens the site in a controlled browser environment.
3. It navigates to relevant pages such as assignments, announcements, or schedules.
4. It extracts **candidate** tasks/events/deadlines.
5. SEAL normalises and deduplicates those candidates.
6. The student confirms them before they affect the workload model.

Important constraints that must be acknowledged:

- Authentication and session handling.
- MFA / CAPTCHA and sites that block automation.
- Privacy and credential security.
- Website terms / permission boundaries.
- Website UI changes can break automation.
- Prompt-injection or malicious page content if an LLM-driven browser is used.
- Cost and reliability of running browser agents.

Therefore, a full agentic browser should be treated as a **technical spike / stretch direction** unless the team proves a small reliable path before submission.

### Telegram integration

A Telegram bot can provide a lower-friction capture channel:

```text
Telegram message / forwarded content
              ↓
          SEAL Bot
              ↓
 Parse event / task / deadline candidate
              ↓
       Ask user to confirm
              ↓
       SEAL / Calendar
```

The important product principle is still **confirmation before action**.

### Task decomposition

After a task is captured, SEAL can transform a vague item such as:

> “Finish database assignment by Friday”

into candidate subtasks such as:

```text
1. Review assignment requirements
2. Design schema
3. Implement queries
4. Test results
5. Write report
6. Final review / submission
```

For MVP, decomposition can be rule/template-assisted or AI-assisted, but the student should be able to edit the proposed breakdown.

---

## Proposed Decisions Taken in Response

> These are the **current proposed team responses** based on the mentor notes. Confirm them as a team before describing them as final product decisions.

| # | Feedback | Proposed decision | Reason | Proposed action | Status |
|---|---|---|---|---|---|
| 1 | Manual input is too conventional | **Accept** | High manual effort weakens the product's ease-of-use argument | De-emphasise manual entry in the pitch; keep it only as fallback | Pending implementation |
| 2 | Keep OCR | **Accept** | One photo can produce multiple structured candidate items | Keep OCR as a primary low-friction capture concept | Pending implementation |
| 3 | User should not need to remember every task upfront | **Accept** | This directly addresses input friction | Explore Calendar + shared content + supported-source aggregation | In design / feasibility |
| 4 | Split tasks into subtasks | **Accept** | Makes vague responsibilities actionable and improves effort estimation | Add editable subtask proposal after capture | In design |
| 5 | Agentic / headless-browser collection | **Partial** | Highly creative and powerful, but technically/security sensitive | Treat as technical spike / stretch unless a narrow supported portal can be proven | Feasibility investigation |
| 6 | Telegram integration | **Partial** | API/bot model is feasible and lowers input friction, but not required to prove the core engine | Prototype architecture / optional spike | Stretch |
| 7 | Narrow to one problem | **Accept** | “Student stress” is too broad to defend deeply | Refine the core problem around fragmented responsibilities and low-effort consolidation into an actionable workload picture | Needs team validation |
| 8 | Auto mode switching | **Partial** | Automatic recommendation is useful; forced switching removes agency | SEAL computes a recommended mode, then asks the student to accept / edit / dismiss | Product rule |
| 9 | Minimise user effort | **Accept** | Lower interaction cost improves adoption | Prefer confirmation interactions such as Yes / No / Edit after system-generated proposals | Product rule |
| 10 | Use “agentic” framing | **Partial** | Communicates the system's active role, but only if technically accurate | Use terms such as “agentic capture” / “headless browser automation” only for flows that match those definitions | Pitch/documentation |

---

## Evidence of Change

### Completed by this documentation update

- Mentor #1 is no longer represented as an empty / not-yet-held template.
- The raw feedback has been converted into explicit product and technical themes.
- The proposed post-mentor direction is documented without claiming that the features already exist.

### Still required before claiming implementation

- [ ] Confirm actual mentor name, date, attendees, and format.
- [ ] Team confirms Accept / Partial / Reject decisions.
- [ ] Update the final problem framing in judge-facing documentation if the team accepts it.
- [ ] Update FigJam to show the mentor-driven input-friction branch.
- [ ] Decide whether OCR is MVP, prototype-only, or technical spike.
- [ ] Decide whether to build a Telegram bot proof.
- [ ] Decide whether to build a narrow headless-browser proof against one supported source.
- [ ] Add task-decomposition interaction to prototype if selected.
- [ ] Update architecture and scope docs after those decisions.
- [ ] Capture screenshots / commits as evidence of actual post-mentor changes.

---

## Questions Created by This Feedback

These are useful for the team's next mentor session or internal decision meeting:

1. What **single source-fragmentation problem** should SEAL own first?
2. Which low-friction source gives the best proof-to-effort ratio: OCR, Calendar, Telegram, or one headless-browser portal?
3. Can one photo realistically create several useful candidate tasks without making confirmation tedious?
4. How should SEAL estimate effort when a newly captured task has no duration?
5. When should task decomposition happen automatically, and when should the student request it?
6. How much autonomy can an agent have before the product becomes uncomfortable or unsafe?
7. What is the minimum confirmation interaction that still gives the student control?
8. Can a new student understand the core flow without a tutorial?

---

## Impact on the Evolution Log

This session changes the direction of the next iteration from “add more task-entry methods” to a deeper product question:

> **How much useful workload understanding can SEAL create from the smallest possible amount of student effort?**

The main post-mentor exploration is therefore:

**Low-friction capture → automatic structuring → task decomposition → human confirmation → capacity reasoning → recommended Focus / Rebalance / Recover mode.**

See the [Ideation and Prototype Evolution Log](../ideation/SEALY_Ideation_and_Prototype_Evolution_Log.md) for the durable iteration summary.

---

## Follow-Up

| Item | Owner | Due | Status |
|---|---|---|---|
| Confirm mentor identity / actual session date | Team | Before submission | Pending |
| Confirm final narrow problem framing | Team | Before next prototype change | Pending |
| Decide OCR MVP status | Team | Before next prototype change | Pending |
| Evaluate one agentic/headless-browser proof | Engineering | Before scope freeze | Pending |
| Evaluate Telegram bot feasibility | Engineering | Before scope freeze | Pending |
| Add task-decomposition UX concept | Design | Before final prototype | Pending |
| Update FigJam with mentor-driven iteration | Design / Ideation | Before submission | Pending |
| Record real implementation evidence | Team | Before submission | Pending |

---

## Related Documents

- [Mentor Consultation #2 — 12 September 2026](mentor-02-sep12.md)
- [Ideation and Prototype Evolution Log](../ideation/SEALY_Ideation_and_Prototype_Evolution_Log.md)
- [Technical Feasibility](../architecture/technical-feasibility.md)

