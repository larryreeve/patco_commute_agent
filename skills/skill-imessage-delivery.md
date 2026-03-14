# Skill: iMessage Delivery

How to format the train times as a commuter-ready message and send it via iMessage.

---

## Message Format

```text
{Day-of-week} {month}/{day}
PATCO Travel Alerts
Checked: {timestamp}  
Status: {status text}  
Alert Active: {Yes|No}

PATCO next 6 trains from {origin} to {destination}:
{departure1} - arrives {arrival1}
{departure2} - arrives {arrival2}
{departure3} - arrives {arrival3}
{departure4} - arrives {arrival4}
{departure5} - arrives {arrival5}
{departure6} - arrives {arrival6}
Using: {schedule name or effective date}.
```

- If a special schedule is active, the "Using:" line must say so explicitly.
- If fewer than 6 trains were available, append a note: `(Only {n} trains remaining in service window.)`

---

## Examples

**Standard timetable:**
```
Monday 3/10
PATCO Travel Alerts  
Checked: 3/13/2026 6:57:56 PM  
Status: Trains are operating on or close to schedule. Check below for any special schedule in effect.  
Special Schedule: Normal Schedule in Effect  
Alert Active: No

PATCO next 6 trains from Ashland to 15/16th & Locust:
7:42 AM - arrives 8:15 AM
7:57 AM - arrives 8:30 AM
8:12 AM - arrives 8:45 AM
8:27 AM - arrives 9:00 AM
8:42 AM - arrives 9:15 AM
8:57 AM - arrives 9:30 AM
Using: PATCO timetable effective 12/1/2025.
```

**Special schedule:**
```
Monday 3/10
PATCO Travel Alerts  
Checked: 3/13/2026 6:57:56 PM  
Status: Trains are operating on or close to schedule. Check below for any special schedule in effect.  
Special Schedule: Normal Schedule in Effect  
Alert Active: No

PATCO next 6 trains from 15/16th & Locust to Ashland:
5:18 PM - arrives 5:55 PM
5:33 PM - arrives 6:10 PM
5:48 PM - arrives 6:25 PM
6:03 PM - arrives 6:40 PM
6:18 PM - arrives 6:55 PM
6:33 PM - arrives 7:10 PM
Using: Special schedule in effect for today.
```

---

## Sending the Message

- Use the **iMessage connector** to send the message.
- Do **not** use the browser to send iMessage.
- The recipient is the default contact configured for this project.

---

## Formatting Rules

- Keep the message concise — it is read on a phone.
- Do not add explanations, caveats, or extra context in the message body itself.
- All times must include AM/PM.
- The "Using:" line is required in every message without exception.
