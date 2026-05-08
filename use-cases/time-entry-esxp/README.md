# Use Case: Time Entry via ESXP

> Ask Clawpilot to add your labor hours directly to the ESXP CSA dashboard — handy for end-of-week time entry.

_Credit: Ryan Otis — shared in The A-Team 💪🥇🤓 chat, May 8, 2026_

---

## Problem

Time entry in ESXP requires navigating the weekly view, finding the right customer row, and entering hours. When you're in a flow, breaking out to the browser is disruptive.

## When to Use This

- End-of-week (or end-of-day) time entry
- You need to log hours for one or more customers without leaving your current context
- Works from Teams chat — just share the ESXP URL and give it your details

## How to Use

1. Go to your ESXP weekly view: https://esxp.microsoft.com/#/time/weekview
2. Copy the full URL from your browser
3. Paste the prompt into Clawpilot with your details filled in
4. Clawpilot will navigate to the page and enter the hours as a **draft** — it will not submit
5. Verify visually and submit yourself when ready

## Available Prompts

| Prompt | Best for |
|---|---|
| [log-hours-esxp.md](prompts/log-hours-esxp.md) | Adding hours for one customer on a specific day |

## Tips & Gotchas

- Clawpilot saves entries as **draft** — you still need to submit via "Agree & Submit All" yourself
- Confirm the row total and day-header hours match what you expect before submitting
- You can ask it to add hours for multiple customers in one prompt
