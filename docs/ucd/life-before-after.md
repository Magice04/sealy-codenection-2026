# Life Before and After SEAL

> This is a **design hypothesis**, not an observed outcome. No student behaviour or health outcome is claimed from the prototype.

## Before SEAL

A student receives responsibilities through multiple channels:

```text
assignment PDF
class schedule
WhatsApp / Teams
email
calendar
portal
memory
```

To understand today, the student must manually reconstruct:

1. what work exists;
2. which deadline is first;
3. how long each item may take;
4. what fixed events already occupy the day;
5. whether the remaining work fits.

Even when every task is known, the student can still miss the **capacity problem**.

Example:

```text
Work to finish: 3h35
Time left:      2h40
Difference:       55m short
```

A normal list can show all three tasks while still leaving the student to discover that the plan is impossible.

## After SEAL — intended experience

### 1. Bring work in from where it already exists

The student imports a photo, screenshot, document, calendar item, email or intentionally shared content.

### 2. SEAL drafts the structure

Candidate task/event fields are extracted and, when useful, a large task can be broken into suggested subtasks.

### 3. Student confirms

The user edits/accepts/ignores the candidate. SEAL does not silently persist an uncertain interpretation.

### 4. SEAL shows the concrete situation

Instead of a vague score:

```text
ISP640 Project Plan              90m
ICT652 presentation prep         65m
ASC486 Group Project             60m
                                ----
Work to finish                  3h35
Time left                       2h40
55 min short
```

### 5. SEAL suggests the next action

- **Focus** when the plan fits.
- **Adjust My Plan** when it does not.
- **Take a Break** when recovery is appropriate and immediate urgency is manageable.

### 6. The student stays in control

For plan adjustment:

- Keep
- Add another arrangement
- Move
- Defer

The student confirms the change.

### 7. SEAL makes the week legible

Today/Week Plan and 7/30-day/Semester Insights show how work changes over time without requiring the student to interpret five separate “load scores”.

## Before vs after

| Before | Intended after |
|---|---|
| Manually copy tasks from several sources | Import from existing sources |
| Task list without effort context | Work items with estimates/deadlines |
| Calendar shows empty slots only | Compare work required with time left |
| Discover overload while already inside it | See shortfall before committing to the plan |
| Generic “you are busy” message | “You are 55 min short” + visible causes |
| Manually rebuild the whole plan | SEAL proposes alternatives |
| App blocker behaviour unclear | only selected distractions are paused |
| Period insights unavailable | 7 Days / 30 Days / Semester prototype views |

## What this does not prove

The prototype does **not** prove that:

- students will estimate task duration accurately;
- students will accept automated suggestions;
- SEAL reduces stress or burnout;
- students will keep using the app;
- OCR will be correct without edits.

Those require real user testing / implementation evidence.

## Validation questions

1. Can a student understand the 3h35 / 2h40 / 55m relationship without explanation?
2. Does importing a source feel easier than manually creating all tasks?
3. Do Keep / Add / Move / Defer cover the changes students actually want?
4. Does the Week view make scheduling easier or create more complexity?
5. Does the Island help comprehension or merely decorate the result?
