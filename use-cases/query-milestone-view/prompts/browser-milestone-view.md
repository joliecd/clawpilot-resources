# Prompt: Browser Milestone View

**Best for:** Pulling milestone data when the MSX CRM MCP server is not connected. Uses Clawpilot's built-in Playwright browser automation to navigate the MSX web UI.

---

## Prompt

```
I need to pull my milestone data from MSX using the browser. The msx-crm MCP server is not connected, so use Playwright browser automation.

Steps:
1. Navigate to the MSX milestone grid:
   https://microsoftsales.crm.dynamics.com/main.aspx?appid=fe0e1b46-20e5-ec11-b5cf-00224828e5a0&pagetype=entitylist&etn=msp_engagementmilestone

2. Wait for the page to fully load. Take a screenshot to verify.

3. Look for the view selector dropdown (usually near the top of the grid). Click it and switch to my saved view: "[VIEW_NAME]"
   - If you can't find the view, look for "My Views" or "Personal Views" in the dropdown
   - Common view names: "[YourAlias] Milestones This Q", "[YourAlias] Milestones This FY"

4. Wait for the grid to reload with the filtered view.

5. Take a snapshot of the page and extract the table data. I need these columns:
   - Milestone Name
   - Workload
   - Monthly Use ($)
   - Account (parent account name)
   - Milestone Date
   - Status (On Track / At Risk / Blocked / Completed)
   - Commitment (Committed / Uncommitted / Pipeline)
   - Recurring (Y/N)
   - Category (POC / Pre-Prod / Production)

6. If the grid has multiple pages, navigate through all pages and collect all rows.

7. Format the results as a clean table and include a total $/mo at the bottom.

If MSX requires authentication, pause and let me log in via the browser before continuing.
```

---

## Notes

- Replace `[VIEW_NAME]` with your actual saved view name (e.g., "[YourAlias] Milestones This Q")
- Browser automation is slower (~30-60 seconds) and more fragile than the MCP approach
- The MSX grid may not show all columns by default — you may need to tell Clawpilot to scroll right or look for hidden columns
- If the grid truncates milestone names, Clawpilot can click into individual rows for full details
- **Recommended:** If you plan to do this regularly, set up the MSX MCP server instead (see README.md for setup instructions)
- TPID may not be visible in the default grid columns — Clawpilot may need to click into the opportunity and then the account to find it
