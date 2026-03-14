# PATCO Commute Agent

## Purpose

Deliver the next 6 upcoming PATCO train departure and arrival times for my commute along with checking the latest Patco travel alerts and then send as an iMessage.

## My Default Route

- **Commute days:** Monday–Thursday
- **Morning:** Ashland → 15/16th & Locust
- **Evening:** 15/16th & Locust → Ashland

## Source of Truth

- **Timetable PDF:** Use the cached copy in the project folder (`PATCO_Timetable_YYYY-MM-DD.pdf`) if present. Only re-download it if no cached copy exists or if the alerts page announces a newer effective date.
- **Alerts & special schedules:** Always fetch live from `https://www.ridepatco.org/schedules/schedules.asp` — never cache these.
- If a special schedule PDF exists for today's date, use it instead of the standard timetable.

## Skills

Skills are located in the skills folder.

| Skill | File |
|---|---|
| How to retrieve and select the correct PATCO schedule | `skill-schedule-retrieval-v2.md` |
| How to extract the next 6 train times | `skill-train-extraction.md` |
| How to format and send the iMessage | `skill-imessage-delivery.md` |
| How to check for Patco alerts | `skill-patco-alert-check.md` |

## Constraints

- Do not generate application code.
- Do not invent train times.
- Do not send iMessage via the browser.
- Always identify which timetable or special schedule was used in the message.
