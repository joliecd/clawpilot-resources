# Example Output

**Prompt used:** [committed-on-track.md](../prompts/committed-on-track.md)
**Context:** Queried committed + On Track milestones for FY26 Q4 (Apr–Jun 2026) on June 9, 2026.

---

## Input

```
Show me my committed, On Track milestones for the current fiscal quarter.
```

## Output

```
You have 6 committed, On Track milestones this quarter (FY26 Q4):

| # | Milestone                                    | Workload                      | $/mo    | Account | TPID     | Date | Recurring | Category   |
|---|----------------------------------------------|-------------------------------|---------|---------|----------|------|-----------|------------|
| 1 | Inbound: Red Hat FY26 CoSell ARO | DR dev   | ARO (AI Apps & Agents)        | $8,000  | Premera | 12345678 | 6/10 | Y         | Production |
| 2 | Premera | FileNet to ARO | Pre-Prod         | ARO (Migrate & Modernize)     | $11,300 | Premera | 12345678 | 6/10 | Y         | Production |
| 3 | Prod - Phase 12 - Storage                    | Storage & File Systems        | $3,500  | BSC     | 87654321 | 6/20 | Y         | Production |
| 4 | Prod - Phase 12 - SQL VMs                    | Windows                       | $3,500  | BSC     | 87654321 | 6/20 | Y         | Production |
| 5 | Prod - Phase 12 - App VMs                    | Linux                         | $3,500  | BSC     | 87654321 | 6/20 | Y         | Production |
| 6 | Purview POC                                  | Purview                       | $1,500  | Multicare| 11223344| 6/25 | Y         | Production |

Total committed $/mo: $31,300
```

## Notes

- All 6 milestones were Production category
- TPIDs are illustrative — actual values come from the account's `msp_tpid` field
- Two Premera ARO milestones were due the next day (6/10), flagged for attention
