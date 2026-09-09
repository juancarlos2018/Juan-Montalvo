# Marginal Analysis — Model Specification


## 1. Inputs

| Name | Value | Unit | Source |
|---|---|---|---|
| TOMATO_BED_CAP | 20 | beds | case givens |
| TOMATO_REVENUE | 8,800 | $/bed | case givens |
| TOMATO_HRS | 2.5 | hrs/wk/bed | case givens |
| TOMATO_DIM | 10% | — | case givens |
| CARROT_BED_CAP | 20 | beds | case givens |
| CARROT_REVENUE | 2,094 | $/bed | case givens |
| CARROT_HRS | 0.833 | hrs/wk/bed | case givens |
| CARROT_DIM | 2.5% | — | case givens |
| MESCLUN_BED_CAP | 30 | beds | case givens |
| MESCLUN_REVENUE | 2,700 | $/bed | case givens |
| MESCLUN_HRS | 1.25 | hrs/wk/bed | case givens |
| MESCLUN_DIM | 1.25% | — | case givens |
| TOTAL_BEDS | 64 | beds | case givens |
| SEASON_WEEKS | 36 | weeks | case givens |
| FIXED_COSTS | 20,000 | $ | case givens |
| OWNER_HRS | 720 | hrs | case givens |
| OWNER_RATE | 34.72 | $/hr | case givens |
| TEMP_WORKER_CAP | 4 | workers | case givens |
| TEMP_HRS_EACH | 1,440 | hrs | case givens |
| TEMP_RATE | 17.36 | $/hr | case givens |


## 2. Structure

| Sheet/Region | Purpose |
|---|---|
| Inputs | All 19 named values from Section 1 — nothing else on this sheet, so any input can be changed in one place |
| Cost Structure | Per-crop labor hours (using the diminishing-returns formula), labor cost split between owner hours and temp workers, fertilizer cost |
| Marginal Cost Schedules | For each crop, cost of the 1st through last bed — this is what gets compared against the flat revenue-per-bed price |
| Optimization | The three decision cells (beds of tomatoes/carrots/mesclun), the constraints, and the Solver setup |
| Checks | The validation rules from Section 4 — formulas confirming no error cells, the q=1 hand-check, and whether the check figures match |
