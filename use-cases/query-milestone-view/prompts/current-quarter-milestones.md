# Prompt: Current Quarter Milestones

**Best for:** Full milestone review for the current fiscal quarter with all key fields — workload, $, account/TPID, date, status, commitment, and recurring flag.

---

## Prompt

```
Pull my milestones for the current fiscal quarter from MSX.

You will need the MSX CRM MCP server (`msx-crm`) tools for this. Verify access with `crm_whoami` first.

Steps to follow:
1. Identify my CRM user ID using `crm_whoami`.
2. Calculate the current Microsoft fiscal quarter date range (FY runs Jul–Jun: Q1=Jul–Sep, Q2=Oct–Dec, Q3=Jan–Mar, Q4=Apr–Jun).
3. Query `msp_engagementmilestones` using the `crm_query` tool with these filters:
   - `_ownerid_value` = my user ID
   - `msp_milestonedate` within the current fiscal quarter date range
   - `msp_milestonestatus` in (861980000=On Track, 861980001=At Risk, 861980002=Blocked, 861980003=Completed)
   - Commitment filter: [ALL | or specify: 861980003=Committed, 861980000=Uncommitted, 861980002=Pipeline]
4. Select these fields:
   - `msp_name` (milestone name)
   - `msp_milestonedate` (date)
   - `msp_monthlyuse` ($ monthly revenue)
   - `msp_milestonestatus` (status)
   - `msp_commitmentrecommendation` (commitment)
   - `msp_milestonecategory` (POC/Pre-Prod/Production)
   - `_msp_workloadlkid_value` (workload)
   - `_msp_opportunityid_value` (opportunity name)
   - `msp_nonrecurring` (recurring Y/N — null or false = recurring, true = non-recurring)
   - `msp_engagementmilestoneid` (milestone ID)
   - `msp_milestonenumber` (milestone number)
5. For each milestone, resolve the parent account and TPID using `crm_get_record`:
   - Get the opportunity's `parentaccountid` (available in the formatted value from step 3, or query `opportunities`)
   - Query the `accounts` entity for `name` and `msp_tpid`
6. Return results as a table with columns:
   Milestone Name | Workload | $/mo | Account | TPID | Date | Status | Commitment | Recurring | Category

Order by milestone date ascending.
```

---

## Notes

- Replace `[ALL | or specify: ...]` with your desired commitment filter, or remove the commitment condition entirely to get all milestones
- The TPID lookup requires an extra query per unique account — for large portfolios this may take a moment
- To also include milestones from past periods that are still active (not completed/cancelled), add a second filter group: `msp_milestonestatus in (On Track, At Risk, Blocked) AND msp_milestonedate in last 4 fiscal periods` — this mirrors a typical "My Milestones This Q" saved view logic
- Formatted values from OData (e.g., `@OData.Community.Display.V1.FormattedValue`) give human-readable labels for status, workload, commitment, etc.
