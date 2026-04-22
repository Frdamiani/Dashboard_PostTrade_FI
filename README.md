The goal was to automate the daily post-trade checks we were doing manually every morning.

## What it does

Tracks a portfolio of short-term fixed income instruments (CDs, T-bills, government bonds)
and flags anomalies automatically via three controls:

- settlement date overdue (status not confirmed and settlement date < today)
- price outlier (clean price below 99%)
- status errors

Each flagged trade gets color-highlighted directly in the sheet. A summary tab
aggregates KPIs: total exposure, confirmed vs. pending trades, alert count,
weighted average price, breakdown by instrument type.

There's also a one-click PDF export macro that auto-names the file with the current date.

## Structure

| Sheet | Description |
|---|---|
| `Suivi_Trades` | Main trade log with controls column |
| `Synthese` | KPI summary and instrument breakdown |

## How to use

1. Save the file as `.xlsm`
2. Import `Module_Dashboard_PostTrade.bas` via the VBA editor (Alt+F11 → Import File)
3. Run macros from the editor or assign them to buttons in the sheet

**Macros:**
- `ActualiserDashboard` — recalculates formulas and updates the last-refresh timestamp
- `LancerControles` — runs the three checks and highlights anomalies
- `ExportPDF` — exports the trade sheet as a dated PDF

## Stack

Excel / VBA — no external dependencies
