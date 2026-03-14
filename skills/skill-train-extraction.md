# Skill: Train Time Extraction

How to determine the correct route direction and extract the next 6 upcoming departures from the active schedule.

---

## Step 1 — Determine the commute direction

Use the default route from `claude.md` unless the user specifies otherwise.

| Time of day | Origin | Destination |
|---|---|---|
| Morning | Ashland | 15/16th & Locust |
| Evening | 15/16th & Locust | Ashland |

**Direction inference rules:**

- If the request clearly indicates morning, use the morning route.
- If the request clearly indicates evening, use the evening route.
- If neither is specified, infer from the current time and commuting context.
- If the day is Friday, Saturday, or Sunday, do not assume a work commute unless the user explicitly requests it.
- If direction cannot be confidently inferred and it matters, state what is missing rather than guessing.

---

## Step 2 — Locate the correct station and direction in the timetable

- Find the row or column corresponding to the origin station.
- Confirm the direction of travel matches the intended destination.
- Use only departure times — not arrival times at intermediate stops — as the basis for selection.

---

## Step 3 — Filter to upcoming departures only

- Exclude any departure times that have already passed relative to the current time.
- Sort remaining departures chronologically.
- Select the next 6 upcoming departures.

---

## Step 4 — Collect arrival times

- For each selected departure, also record the arrival time at the destination station from the same timetable.

---

## Output rules

- Return exactly 6 departure+arrival pairs when available.
- If fewer than 6 trains remain in the service window, return what is available and note that fewer than 6 were found.
- Preserve AM/PM clearly on every time.
- Do not fabricate any times not explicitly shown in the active timetable.
