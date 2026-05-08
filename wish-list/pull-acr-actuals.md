---
status: open
requested-by: Jolie Delcambre
date: 2026-05-08
tags: [acr, actuals, browser-control, reporting]
---

# Wish: Pull ACR Actuals via Clawpilot

> Use Clawpilot to navigate to the ACR actuals report and pull consumption data — eliminating the manual browser work of pulling actuals each cycle.

---

## The Problem

Pulling ACR actuals requires navigating to a specific report, filtering by account/customer, and extracting the data. It's repetitive and one of the biggest manual time drains in the CSA workflow.

## Desired Outcome

Clawpilot should be able to:
1. Navigate to the ACR actuals report (via browser control or MCP)
2. Pull actuals for one or more customers/accounts
3. Return the data in a readable format, or feed it into a comparison against milestone estimates

## Context & Constraints

- Would pair naturally with the [auto-close milestones wish](auto-close-milestones-vs-actuals.md)
- Browser control route likely needed unless ACR data is accessible via an MCP connector
- Ideal output: table of customer, est, actual, variance

## Related Wish List Items

- [auto-close-milestones-vs-actuals.md](auto-close-milestones-vs-actuals.md)

---

_If you build a solution, create a use case in `use-cases/` and update this file's status to `solved` with a link._
