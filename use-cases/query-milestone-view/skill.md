---
status: draft
skill-name: query-milestone-view
owner: 
tags: [msx, milestones, crm, forecast, portfolio]
created: 2026-06-09
last-updated: 2026-06-09
notes: Based on personal saved milestone views in MSX. Uses CRM OData queries to replicate the FetchXML view logic.
---

# Skill Notes

Use this file to track the maturity of this use case toward becoming a Clawpilot skill.

## Validation Notes

_Once team members have tested this, document what worked, what didn't, and any refinements._

- Initial test on 2026-06-09: Successfully queried committed On Track milestones for FY26 Q4, returned 6 results with correct fields.
- TPID resolution requires an extra hop (opportunity → account → msp_tpid). Consider caching account lookups for large portfolios.
- `msp_nonrecurring` field may be null on most milestones — treat null as recurring (Y).

## Skill Readiness Checklist

- [x] README clearly describes the problem and how to use
- [x] At least one well-tested prompt in `prompts/`
- [x] At least one example output in `examples/`
- [ ] Tested by more than one person
- [ ] Status updated to `validated`
