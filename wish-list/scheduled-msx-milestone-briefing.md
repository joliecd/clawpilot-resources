---
status: open
requested-by: Quinn Meagher, Benjamin Coughtry
date: 2026-05-07
tags: [msx, milestones, automation, briefing, scheduled]
---

# Wish: Scheduled MSX Milestone Briefing

> A scheduled Clawpilot automation that periodically reviews MSX and sends you a proactive brief — new milestones assigned to you, committed production milestones, overdue items, etc.

---

## The Problem

Keeping up with MSX milestone changes (new assignments, committed prod milestones, overdue items) requires manually checking MSX or waiting for an alert. There's no proactive push today.

## Desired Outcome

A scheduled automation (daily or weekly) that:
1. Reviews your MSX milestones
2. Identifies: newly assigned milestones, committed prod milestones, overdue or at-risk items
3. Sends a concise brief to you in Teams

## Context & Constraints

- Clawpilot supports scheduled/one-shot automations (see [monitor-meeting-update-document](../use-cases/monitor-meeting-update-document/))
- MSX access via browser control or CRM MCP
- Should be configurable: which milestone types to include, how often to run

## Related Use Cases

- [monitor-meeting-update-document](../use-cases/monitor-meeting-update-document/) — shows scheduled automation pattern

---

_If you build a solution, create a use case in `use-cases/` and update this file's status to `solved` with a link._
