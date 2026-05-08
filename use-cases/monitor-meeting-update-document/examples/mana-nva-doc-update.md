# Example: MANA NVA Meeting Doc Update

**Prompt used:** [schedule-post-meeting-doc-update.md](../prompts/schedule-post-meeting-doc-update.md)
**Shared by:** Ryan Otis

---

## Prompt Used

```
Monitor the meeting transcript for my upcoming meeting: HLS Open Q&A for MANA NVA changes
and make any needed updates to the MANA Customer Communication document.
Save a dated change log entry to the end of the document.
Schedule this to run at 1:45 PM CDT today as a one-shot automation.
Ping me in Teams when the update is complete with a summary of what changed.
```

## What Clawpilot Confirmed Before Running

```
Scheduled: "MANA NVA Meeting Doc Update" — fires today at 1:45 PM CDT
(15 min after the meeting ends, allowing transcript to publish). One-shot.

What it will do automatically:
- Pull the transcript via the Teams join URL (with retry if not yet available)
- Load the /docx skill and read MANA Customer Communication - HLS.docx
- Identify substantive changes warranted by the discussion (NVA behavior,
  timelines, messaging, FAQ, technical details)
- Apply edits in-place, preserving formatting
- Append a dated Change Log entry at the end (creates the section if missing)
- Ping you on Teams with a summary of what was updated
```

## Result

Clawpilot messaged in Teams ~1:45 PM CDT with a summary of the document changes. No manual review of the transcript required.

## Notes

- Clawpilot used retry logic when the transcript wasn't immediately available
- The change log was appended cleanly to the end of the document
- Confirmed working via Teams chat (no need to be in the Clawpilot app)
