# Prompt: Committed On Track Milestones

**Best for:** Quick check of committed milestones that are On Track for the current fiscal quarter — the milestones most likely to land.

---

## Prompt

```
Show me my committed, On Track milestones for the current fiscal quarter.

You will need the MSX CRM MCP server (`msx-crm`) tools for this. Verify access with `crm_whoami` first.

Query `msp_engagementmilestones` using the `crm_query` tool with:
- Owner = me (use `crm_whoami` to get my user ID)
- `msp_milestonedate` within current fiscal quarter (Microsoft FY: Q1=Jul-Sep, Q2=Oct-Dec, Q3=Jan-Mar, Q4=Apr-Jun)
- `msp_commitmentrecommendation` = 861980003 (Committed)
- `msp_milestonestatus` = 861980000 (On Track)

Return a table with: Milestone Name | Workload | $/mo | Account | TPID | Date | Recurring (Y/N) | Category

Also show the total committed $/mo at the bottom.

For TPID: use `crm_get_record` on the `accounts` entity to resolve each opportunity's parent account and get the `msp_tpid` field.
For Recurring: check `msp_nonrecurring` — if null or false → "Y", if true → "N".
```

---

## Notes

- This is the "clean" view — only milestones that are committed and on track
- Useful right before forecast calls to confirm your committed number
- To expand to At Risk or Blocked, change the status filter to include 861980001 and 861980002
