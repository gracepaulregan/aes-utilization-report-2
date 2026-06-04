# AES Resource Utilization Report

**PwC | Application Evolution Services — Oracle Practice**

An interactive, self-contained HTML dashboard for tracking resource utilization across Delivery Centers, identifying below-target resources, and managing gap categories with remediation actions.

## Features

- **9-Tab Interactive Report** — Cover, Executive Summary, 6 Gap Category deep-dives, Next Steps, and Overall Data
- **All 5 Delivery Centers** — Bangalore AC, Buenos Aires AC, Manila AC, Mexico AC, US Non AC
- **Drill-Down on Every Tile** — Click any KPI, stat card, or utilization band to see the underlying employee data
- **Overall Data Tab** — Full filterable, sortable table of all resources with column filters for DC, Level, Job Family, Deployer, Gap Category, Current Project, and Util Range
- **User Remarks** — Add timestamped comments (name + date/time + remark) to any employee row; persists across sessions
- **Upload / Refresh** — Drag-and-drop a new CSV or paste Excel data directly on the cover page to refresh all tabs
- **Export to Excel** — Download the filtered Overall Data view as a CSV file (opens in Excel)
- **Download HTML** — Save the full report as a standalone HTML file to share offline
- **Keyboard Navigation** — Use ← → arrow keys to move between slides

## How to Use

1. Open `index.html` in any modern browser (Chrome, Edge, Firefox, Safari)
2. The report loads with the embedded default dataset (264 resources, Feb–May FY)
3. Navigate tabs using the top navigation bar or arrow keys
4. Click any tile, stat, or band for drill-down details
5. To refresh with new data: use the upload zone on the Cover page
6. On the Overall Data tab: use filters, add remarks, and export to Excel

## Data Format

The dashboard expects a CSV with these columns (from the Oracle AES Overall Sheet):

| Column | Description |
|--------|-------------|
| Workday ID | Unique employee identifier |
| Employee | Full name |
| Status | Active / Inactive |
| Level | Associate, Exp Associate, Senior Associate, Manager, etc. |
| Delivery Centers | Bangalore AC, Manila AC, Mexico AC, Buenos Aires AC, US Non AC |
| Job Family | Oracle Technology, Oracle Finance, Oracle Human Capital, etc. |
| Deployer | Resource deployer name |
| Current Availability | 0%, 25%, 50%, 75%, 100% |
| Current Project | Project assignment(s) |
| Leakage Reasons | Gap category from source data |
| Avg -Res Util | Average resource utilization % |
| Util Target | Target utilization % |
| Capacity | Total capacity hours |
| Client Hrs | Billable client hours |
| Feb-Util, Mar-Util, Apr-Util, May-Util | Monthly utilization % |

## Gap Categories

| Category | Description |
|----------|-------------|
| Project Charging Variance | 100% allocated but not charging per allocation |
| Partial On Bench | 25–75% deployed, remaining capacity unbilled |
| New Project-WBS Pending | Staffed but WBS codes not yet issued |
| On Bench | Fully unallocated (100% available) |
| Recently Allocated | Newly onboarded, in ramp-up phase |
| Unclassified Gap | Below 80% with no gap category assigned |

## Technology

- Pure HTML + CSS + vanilla JavaScript
- No server required — runs entirely in the browser
- Data embedded as Base64 (self-contained, no external dependencies)
- Remarks stored in browser localStorage

## Confidentiality

**For Internal Use Only** — This report contains PwC confidential resource data. Do not share the GitHub Pages link outside authorized personnel.

---

*Reporting Period: May 2026 | PwC Advisory — AES Oracle Practice*
