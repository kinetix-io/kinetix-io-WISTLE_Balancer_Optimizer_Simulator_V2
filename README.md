# WISTLE — Work Instruction & Standard Time = Line Efficiency (UAT build)

Line-balancing, plan-driven capacity planning and line design for LG assembly lines.
This build is for **functional, UI and module testing with sample data**. It runs entirely
in the browser; the Oracle/FastAPI database layer is **not connected** here.

## Open the app
- **Hosted:** open the GitHub Pages link for this repository, or
- **Local:** download the repository and open `index.html` in Chrome or Edge.
  Keep `index.html` in the same folder as the three `.js` files.

Sign in with the pre-filled Production ID and password, Business Unit **Air Conditioner (AC_)**.
(This is a demonstration sign-in only.)

## Test data
Data files are **not** stored in this repository. Each tester uploads them from their own computer on the
Dashboard. The four sample files (one RAC line, `[PA2] IL(P)_RAC04`, six models) are shared separately:

| Dashboard tile | File |
| --- | --- |
| 1. TAKTDATA | `AC_TAKTDATA_Sample.csv` |
| 2. MASTER ST | `AC_MASTER_ST_Sample.csv` |
| 3. GMES Plan | `AC_GMES_Plan_Sample.csv` |
| 4. Task Precedence (optional) | `AC_Task_Precedence_Sample.csv` |

File names must start with `AC_` (the Business Unit chosen at sign-in). Blank upload templates can be
downloaded from the Dashboard (↓ GMES Plan, ↓ Task Precedence).

## Suggested test path
1. **Dashboard** — choose all four files, click **Refresh Data**. Expect Line Balancing 78.65 %, 68 stages, 6 models.
2. **Optimizer** — Refresh Mapping, try manpower changes, task moves, locks, **Execute & Save**, Undo/Redo, Auto-Optimize.
3. **Optimization Audit** — review the change log; export CSV.
4. **Predictive Planner** — set Plan Date From/To = 2026-08-10. Expect Target Takt 9.71 s, minimum MP 58, Operational LBE 81.18 %.
5. **Open in Line Design** — 58 theoretical vs 70 actual workstations, 82.04 % efficiency; open **Edit Rules** in the
   Precedence Master, tick *Any order within stage* on a few stages and watch the result and the precedence diagram update.
   Switch the task source to the precedence file: 68 workstations, 84.45 %.
6. **User Guide & About** — formulas, KPI definitions (section 13).

## Not available in this build (needs the WISTLE database service)
- **Fetch from DB**, **Save Run to DB**, **DB Dashboard** — show a "not reachable" message.
- **Precedence Master versions** are saved in the tester's own browser (a warning banner says so), not in Oracle.
- Named sessions (log out → save) are stored in the tester's browser.
