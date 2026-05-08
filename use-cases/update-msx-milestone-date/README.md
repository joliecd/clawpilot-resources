# Use Case: Update MSX Milestone Date

> Ask Clawpilot to navigate to MSX and update a milestone's target date via browser control — no manual clicking required.

_Credit: Ryan Otis — shared in The A-Team 💪🥇🤓 chat, May 7, 2026_

---

## Problem

Updating milestone dates in MSX requires navigating through several screens. When you have multiple milestones to update, it's repetitive and time-consuming.

## When to Use This

- You need to push out one or more milestone dates
- MSX is being slow or uncooperative — Clawpilot will try multiple routes to get the save to work
- You're context-switching and want to stay in your current tool (Teams or Clawpilot app)

## How to Use

1. Open MSX and navigate to your milestone (or have the full URL ready)
2. Paste the prompt into Clawpilot with the milestone ID and new date filled in
3. Clawpilot will use browser control to find and update the milestone — it may try a couple of routes before it succeeds
4. Confirm the update when Clawpilot asks for approval

## Available Prompts

| Prompt | Best for |
|---|---|
| [update-single-milestone-date.md](prompts/update-single-milestone-date.md) | Moving one milestone to a new date |

## Tips & Gotchas

- Provide the **full MSX URL** for the milestone — Edge can display a vanity URL in the address bar that won't resolve for Clawpilot
- Clawpilot may try multiple approaches before it finds the right way to save — this is normal, let it work
- Always confirm the date change visually in MSX after Clawpilot reports success
