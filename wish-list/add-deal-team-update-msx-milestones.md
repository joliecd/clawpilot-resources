---
status: open
requested-by: Jolie Delcambre
date: 2026-05-08
tags: [msx, deal-team, milestones, browser-control]
---

# Wish: Add Deal Team Members & Update MSX Milestones via Clawpilot

> Manage deal team membership and milestone updates in MSX directly through Clawpilot — without navigating the MSX UI.

---

## The Problem

Adding deal team members and updating milestone fields in MSX (beyond date changes) currently requires manual UI navigation. These are frequent, repetitive tasks that are good candidates for Clawpilot automation.

## Desired Outcome

Clawpilot should be able to:
1. Add a named person as a deal team member to a given opportunity in MSX
2. Update milestone fields (owner, status, workload, etc.) beyond just the date

## Context & Constraints

- Currently achievable via **Copilot CLI + mcaps-iq plugin** (not yet in Clawpilot proper)
- Clawpilot browser control may work as an alternative route — untested as of May 2026
- [update-msx-milestone-date](../use-cases/update-msx-milestone-date/) shows date updates work — this would extend that to other fields

## Workaround (Today)

If you use **Copilot CLI**, install the `mcaps-iq` plugin — it can find and update milestones and manage deal team members via CRM MCP directly.

---

_If you build a Clawpilot solution, create a use case in `use-cases/` and update this file's status to `solved` with a link._
