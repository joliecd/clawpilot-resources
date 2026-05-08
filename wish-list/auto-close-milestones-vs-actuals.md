---
status: open
requested-by: Ahmed Bham
date: 2026-05-08
tags: [msx, milestones, acr, actuals, automation]
---

# Wish: Auto-Close Milestones When ACR Actuals Meet Estimated

> A prompt or automation that compares On Track milestone estimates against ACR actual consumption, then either reports the gap or auto-closes milestones where actuals meet the estimate.

---

## The Problem

Manually cross-referencing On Track milestones against ACR actuals is tedious. You have to look at the Est Change in MSX, pull the ACR actuals report, and compare them — then decide which milestones can be closed. There's currently no documented prompt to automate this workflow in Clawpilot.

## Desired Outcome

Clawpilot should be able to:
1. Look at **Est Change** values for On Track milestones
2. Look at **ACR actuals** report
3. Either:
   - Report the details (milestone name, est vs actual) for human review
   - Auto-close milestones where actuals have met the estimate

## Context & Constraints

- MSX and ACR data need to be accessible via browser control or CRM MCP
- Auto-close should require confirmation before executing
- A reporting-only mode would be a good first step before building auto-close

## Related Use Cases

- [update-msx-milestone-date](../use-cases/update-msx-milestone-date/) — shows Clawpilot can interact with MSX milestones via browser

---

_If you build a solution, create a use case in `use-cases/` and update this file's status to `solved` with a link._
