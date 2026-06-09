# Use Case: Query Milestone View

> Pull milestone data from your personal Dynamics MSX views for the current fiscal quarter, including workload, revenue, account, status, and commitment details.

---

## Problem

CSAs need to quickly review their milestone portfolio for the current quarter — filtering by commitment status (committed, uncommitted, pipeline), seeing monthly revenue, workload, account (TPID), and whether revenue is recurring. Navigating the MSX UI to open views and export data is slow. Clawpilot can query these views directly via CRM OData and return a formatted table.

## When to Use This

- Morning prep or weekly review of your milestone portfolio
- Checking committed vs. uncommitted milestones for the current fiscal quarter
- Building a quick report of milestone dates, $, and statuses for a manager or team sync
- Verifying milestone hygiene before MOP or forecast calls

## Two Approaches

This use case supports two paths. **Option A (MCP) is recommended** — it's faster, more reliable, and supports write operations. Option B (Browser) works without additional setup.

| | Option A: MCP Server (Recommended) | Option B: Browser Automation |
|---|---|---|
| **Speed** | ~2-5 seconds (direct API) | ~30-60 seconds (page loads, rendering) |
| **Reliability** | Structured JSON, exact fields | Fragile — UI changes can break selectors |
| **Write support** | Yes (update dates, status, comments) | Possible but error-prone |
| **Setup** | One-time MCP server install | None — uses Playwright (built-in) |
| **Filtering** | Precise OData filters, any field | Limited to saved views in the UI |

---

### Option A: MSX CRM MCP Server (Recommended)

**One-time setup:** Add the MSX MCP server to Clawpilot's MCP configuration.

In your Clawpilot MCP settings (e.g., `~/.copilot/m-mcp-servers.json` or VS Code `mcp.json`), add:

```json
{
  "msx": {
    "type": "stdio",
    "command": "npx",
    "args": ["-y", "@microsoft/msx-mcp-server@latest"],
    "env": {
      "npm_config_@microsoft:registry": "https://npm.pkg.github.com"
    }
  }
}
```

> **Note:** This package is on the GitHub npm registry (`npm.pkg.github.com`). You may need to authenticate with `npm login --registry=https://npm.pkg.github.com` using a GitHub PAT with `read:packages` scope if you haven't already.

After adding, restart Clawpilot and verify with `crm_whoami`.

#### Required Tools (from `msx-crm` MCP)

| Tool | Purpose |
|---|---|
| `crm_whoami` | Get your CRM user ID (GUID) |
| `crm_query` | OData query against `msp_engagementmilestones`, `accounts`, `opportunities` |
| `crm_get_record` | Fetch a single record (e.g., account by ID to get TPID) |
| `get_milestones` | Composite tool — can scope by customer, opportunity, or owner. Supports `mine=true` for your milestones |

#### Optional Tools

| Tool | Purpose |
|---|---|
| `update_milestone` | Update milestone date, status, commitment, or forecast comments |
| `get_milestone_activities` | List tasks linked to milestones |

#### How to Use (MCP)

1. Open Clawpilot
2. Ensure the **MSX CRM MCP server** is connected (check with `crm_whoami`)
3. Copy a prompt from the `prompts/` folder
4. Adjust `[BRACKETED PLACEHOLDERS]` for your context (e.g., commitment filter, quarter)
5. Run it — Clawpilot will query CRM via OData and return a formatted table

---

### Option B: Browser Automation (Fallback)

**No setup required** — uses Clawpilot's built-in Playwright browser tools.

This approach navigates to the MSX web UI, opens your saved milestone view, and scrapes the table data. It's slower and less precise but works without any MCP server configuration.

#### Required Tools (built-in)

| Tool | Purpose |
|---|---|
| `browser_navigate` | Open the MSX milestone grid |
| `browser_snapshot` | Read page content and find UI elements |
| `browser_click` | Switch views, interact with filters |
| `browser_take_screenshot` | Visual verification |

#### How to Use (Browser)

1. Open Clawpilot
2. Use the browser prompt from `prompts/browser-milestone-view.md`
3. Clawpilot will navigate to MSX, open your saved view, and scrape the results
4. Results may need manual verification — browser scraping can miss columns or truncate data

## Available Prompts

| Prompt | Best for | Approach |
|---|---|---|
| [current-quarter-milestones.md](prompts/current-quarter-milestones.md) | Full milestone view for current fiscal quarter with all key fields | MCP |
| [committed-on-track.md](prompts/committed-on-track.md) | Quick filter to committed + On Track milestones only | MCP |
| [browser-milestone-view.md](prompts/browser-milestone-view.md) | Same data via browser when MCP is not available | Browser |

## Tips & Gotchas

- **Fiscal quarter mapping** — Microsoft FY runs Jul–Jun. Q1=Jul–Sep, Q2=Oct–Dec, Q3=Jan–Mar, Q4=Apr–Jun. Clawpilot should calculate date ranges from the current date.
- **User query views** — Your personal views are stored in the `userqueries` entity set in CRM. You can ask Clawpilot to list them with `crm_query` on `userqueries` filtered by `_ownerid_value`.
- **OData doesn't support fiscal period operators** — Unlike FetchXML, OData `$filter` can't use `this-fiscal-period`. Clawpilot must calculate explicit date ranges (e.g., `msp_milestonedate ge 2026-04-01 and msp_milestonedate le 2026-06-30`).
- **Workload field** — Use `_msp_workloadlkid_value` (lookup), not `msp_workloadlkid` (will error).
- **Recurring** — The `msp_nonrecurring` field indicates whether revenue is non-recurring. If `null` or `false`, the milestone is recurring; if `true`, it is non-recurring.
- **TPID / Account** — The opportunity links to the parent account. To get TPID, you need the account's `msp_tpid` field. Clawpilot can resolve this by reading the opportunity's `parentaccountid` and then querying the account.
