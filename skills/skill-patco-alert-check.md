---
name: patco-alert-check
description: Check the PATCO mobile Travel Alerts page and return current service alert status.
---

# PATCO Travel Alert Check

## Source
https://ridepatco.org/m/travel_alerts.asp

## Objective
Determine whether PATCO currently reports an operational service alert.

## Procedure

1. Open the PATCO mobile Travel Alerts page.

2. Locate the **Travel Alerts** section.

3. Extract the following fields:

- page timestamp
- operating status message
- special schedule text

4. Ignore the following sections:

- Elevator & Escalator Information
- Email Notification Service
- page navigation
- footer

## Decision Rules

Return **Alert Active: No** only when BOTH conditions are true:

- status text says trains are operating on or close to schedule
- special schedule says normal schedule is in effect

Return **Alert Active: Yes** when either condition occurs:

- status text contains words indicating disruption such as  
  delay, signal issue, equipment issue, power issue, suspended service, trains held
- special schedule is anything other than normal schedule

Do not infer problems that are not explicitly stated.

## Output Format

Return exactly:

PATCO Travel Alerts  
Checked: {timestamp}  
Status: {status text}  
Special Schedule: {special schedule text}  
Alert Active: {Yes|No}

## Failure Output

If the page cannot be loaded:

PATCO Travel Alerts  
Checked: unavailable  
Status: PATCO travel alerts page unavailable  
Special Schedule: unknown  
Alert Active: Unknown

## Example

PATCO Travel Alerts  
Checked: 3/13/2026 6:57:56 PM  
Status: Trains are operating on or close to schedule. Check below for any special schedule in effect.  
Special Schedule: Normal Schedule in Effect  
Alert Active: No