# Use Case: Monitor Meeting Transcript & Auto-Update Document

> Ask Clawpilot to watch a scheduled Teams meeting, pull the transcript after it ends, and automatically update a customer-facing document with a dated change log.

_Credit: Ryan Otis — shared in The A-Team 💪🥇🤓 chat, May 7, 2026_

---

## Problem

After a customer meeting, someone has to manually review the transcript and update relevant documents (comms docs, FAQ, NVA docs, etc.). This is time-consuming and easy to forget when you're back-to-back.

## When to Use This

- You have an upcoming meeting where the outcome will require updating a document
- You want the update to happen automatically ~15 minutes after the meeting ends
- Works great for recurring customer meetings where a doc is the living source of truth

## How to Use

1. **Before the meeting**, paste the prompt into Clawpilot (in Teams chat or the app) with your meeting details filled in
2. Clawpilot will schedule a one-shot automation to fire ~15 min after the meeting ends
3. It pulls the Teams transcript, identifies changes, updates the document, and appends a dated change log entry
4. It pings you in Teams when done with a summary of what changed

## Available Prompts

| Prompt | Best for |
|---|---|
| [schedule-post-meeting-doc-update.md](prompts/schedule-post-meeting-doc-update.md) | Scheduling the automation before the meeting |

## Tips & Gotchas

- Set the fire time ~15 min after the meeting ends to give the transcript time to publish
- Give Clawpilot the **full Teams URL** — Edge sometimes uses a vanity/shortened URL that won't resolve correctly
- The automation is one-shot by default (runs once, then disables itself)
- Clawpilot will ping you in Teams when it's done — check the change log summary before sharing the doc
- Works from Teams chat — you don't have to be in the Clawpilot app
