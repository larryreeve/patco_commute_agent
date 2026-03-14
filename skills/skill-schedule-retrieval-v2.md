# Skill: Schedule Retrieval

How to obtain the correct PATCO timetable for the current run.

---

## Caching Strategy

The standard timetable PDF changes infrequently (a few times per year). To avoid
re-downloading it on every run, a cached copy is stored in the project folder.
Travel alerts and special schedules **must always be checked live** — they change
frequently and override the standard timetable.

---

## Step 1 — Check for a cached timetable PDF

Look for a file matching this pattern in the project folder:

```
PATCO_Timetable_YYYY-MM-DD.pdf
```

Example: `PATCO_Timetable_2025-12-01.pdf`

If a cached file exists, **use it** — skip Step 2.

---

## Step 2 — Download the timetable (cache miss or forced refresh)

Only do this if:
- No cached PDF exists, **or**
- The alerts page announces a new timetable effective date that is newer than the cached file's date.

1. Fetch `https://www.ridepatco.org/schedules/schedules.asp`
2. Find the PDF link for the current standard timetable (e.g. `PATCO_Timetable_YYYY-MM-DD.pdf`)
3. Download it via WebFetch and save it to the project folder using the filename from the URL
4. Delete any older cached timetable files from the project folder

---

## Step 3 — Always check alerts live

Regardless of whether the timetable was cached or freshly downloaded, **always**
fetch the alerts page live:

```
https://www.ridepatco.org/schedules/schedules.asp
```

Look for:
- Any active travel alerts or service disruptions
- Special schedule PDFs listed for today's date (e.g. `TW_YYYY-MM-DD.pdf`)

---

## Step 4 — Determine which schedule to use for today

| Condition | Action |
|---|---|
| A special schedule PDF exists for today's date | Download and use the special schedule PDF instead of the standard timetable |
| No special schedule for today | Use the cached (or freshly downloaded) standard timetable PDF |

---

## Output

Return:
- The path to the PDF to use for train time extraction
- The schedule label to include in the iMessage (e.g. `"PATCO timetable effective 12/1/2025"` or `"Special schedule for 3/14/2026"`)
- Any alert text to include in the message
