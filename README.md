# PATCO Commute Agent

A Claude-Cowork-powered commute assistant that fetches the next 6 PATCO train departures for your daily route, checks for live service alerts, and delivers the results via iMessage.

---

## What It Does

Each time you run it, the agent:

1. Checks for a cached timetable PDF in the project folder (downloads a fresh one only if needed)
2. Fetches live alerts and special schedules from the PATCO website
3. Extracts the next 6 upcoming departures for your route
4. Sends the results as an iMessage to +1 (856) 236-9785

---

## Default Route

| Direction | Origin | Destination |
|---|---|---|
| Morning | Ashland | 15/16th & Locust |
| Evening | 15/16th & Locust | Ashland |

**Commute days:** Monday–Thursday. The agent infers direction from the current time of day. On Fridays, Saturdays, and Sundays it will not assume a work commute unless you explicitly request one.

---

## Setup

Before using this agent, make sure the following are configured in Claude Cowork.

**1. iMessage Connector**

The agent sends results via iMessage using the built-in iMessage connector in Cowork. This requires:

- Running Cowork on a Mac with the Messages app signed in to your Apple ID
- Granting Cowork access to Messages when prompted on first use

No additional installation is needed — the connector is built into Cowork.

**2. Project Folder**

Point Cowork at this project folder so the agent can read `claude.md`, the skill files, and the cached timetable PDF. Do this by clicking **Select Folder** in Cowork and choosing the `patco/` directory.

**3. Recipient Phone Number**

The recipient number is stored in `claude.md`. To change it, open `claude.md` and update the number in the Purpose section. 


**4. Claude Chrome Extension**

Not required. The agent fetches PATCO web pages using Cowork's built-in web tools, not browser automation. The Claude Chrome extension does not need to be installed.

**5. Timetable Cache (optional)**

A cached copy of the timetable PDF (`PATCO_Timetable_2025-12-01.pdf`) is included in the project folder. If it is missing or outdated, the agent will download a fresh copy automatically on the next run.

---

## How to Run

Open a Cowork session in this folder and say:

> "Return the next 6 PATCO trains and send an iMessage to {contact}"

The agent will handle the rest and send you an iMessage.

---

## Project Files

```
patco/
├── claude.md                          # Agent instructions and configuration
├── README.md                          # This file
├── PATCO_Timetable_YYYY-MM-DD.pdf     # Cached standard timetable
└── skills/
    ├── skill-schedule-retrieval-v2.md # How to retrieve and cache the timetable
    ├── skill-train-extraction.md      # How to extract the next 6 trains
    ├── skill-imessage-delivery.md     # How to format and send the iMessage
    └── skill-patco-alert-check.md     # How to check for service alerts
```

---

## Timetable Caching

The standard timetable PDF is cached locally to avoid re-downloading it on every run. The agent will automatically refresh the cache if PATCO publishes a new timetable with a later effective date.

**Live alerts and special schedules are always fetched fresh** — they are never cached, since they can change at any time and override the standard timetable.

---

## iMessage Format

```
Friday 3/13
PATCO Travel Alerts
Checked: 3/13/2026 7:59:27 PM
Status: Trains are operating on or close to schedule.
Special Schedule: Normal Schedule in Effect
Alert Active: No

PATCO next 6 trains from 15/16th & Locust to Ashland:
9:12 PM - arrives 9:36 PM
9:32 PM - arrives 9:56 PM
9:52 PM - arrives 10:16 PM
10:12 PM - arrives 10:36 PM
10:32 PM - arrives 10:56 PM
10:52 PM - arrives 11:16 PM
Using: PATCO timetable effective 12/1/2025.
```

---

## Data Sources

| Source | URL | Caching |
|---|---|---|
| Standard timetable PDF | `https://www.ridepatco.org/pdf/PATCO_Timetable_YYYY-MM-DD.pdf` | Cached locally |
| Alerts & special schedules | `https://www.ridepatco.org/schedules/schedules.asp` | Always live |
| Mobile alerts | `https://ridepatco.org/m/travel_alerts.asp` | Always live |
