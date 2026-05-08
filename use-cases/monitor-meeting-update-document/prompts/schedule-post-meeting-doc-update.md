# Prompt: Schedule Post-Meeting Document Update

**Best for:** Scheduling a one-shot automation before a meeting that will auto-update a document from the transcript after the meeting ends.

_Credit: Ryan Otis_

---

## Prompt

```
Monitor the meeting transcript for my upcoming meeting: [MEETING NAME]
and make any needed updates to [DOCUMENT NAME OR SHAREPOINT URL].
Save a dated change log entry to the end of the document.
Schedule this to run [TIME — approximately 15 min after meeting end, e.g. "1:45 PM CDT"] today as a one-shot automation.
Ping me in Teams when the update is complete with a summary of what changed.
```

---

## Notes

- Replace `[MEETING NAME]` with the full meeting title as it appears in your calendar
- Replace `[DOCUMENT NAME OR SHAREPOINT URL]` with the exact doc name or SharePoint link
- Set the time ~15 minutes after the meeting ends to allow the transcript to publish
- The automation fires once and disables itself — you can re-run manually for follow-up meetings
- Clawpilot will message you in Teams with a summary when it's done
