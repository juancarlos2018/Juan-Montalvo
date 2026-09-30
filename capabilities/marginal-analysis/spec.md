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
| CARROT_HRS | 0.8333 (=2.5/3) | hrs/wk/bed | case givens, corrected from rounded 0.833 during audit |
| CARROT_DIM | 2.5% | — | case givens |
| MESCLUN_BED_CAP | 30 | beds | case givens |
| MESCLUN_REVENUE | 2,700 | $/bed | case givens |
| MESCLUN_HRS | 1.25 | hrs/wk/bed | case givens |
| MESCLUN_DIM | 1.25% | — | case givens |
| TOTAL_BEDS | 64 | beds | case givens |
| SEASON_WEEKS | 36 | weeks | case givens |
| FIXED_COSTS | 20,000 | $ | case givens |
| OWNER_HRS | 720 | hrs | case givens |
| OWNER_RATE | 34.7222 (=50,000/1,440) | $/hr | case givens, corrected from rounded 34.72 during audit |
| TEMP_WORKER_CAP | 4 | workers | case givens |
| TEMP_HRS_EACH | 1,440 | hrs | case givens |
| TEMP_RATE | 17.3611 (=25,000/1,440) | $/hr | case givens, corrected from rounded 17.36 during audit |


## 2. Structure

| Sheet/Region | Purpose |
|---|---|
| Inputs | All 19 named values from Section 1 — nothing else on this sheet, so any input can be changed in one place |
| Cost Structure | Per-crop labor hours (using the diminishing-returns formula), labor cost split between owner hours and temp workers, fertilizer cost |
| Marginal Cost Schedules | For each crop, cost of the 1st through last bed — this is what gets compared against the flat revenue-per-bed price |
| Optimization | The three decision cells (beds of tomatoes/carrots/mesclun), the constraints, and the Solver setup |
| Checks | The validation rules from Section 4 — formulas confirming no error cells, the q=1 hand-check, and whether the check figures match |

## 3. Calculation Logic

LABOR_HRS(crop, q) = q × HRS_PER_BED(crop) × SEASON_WEEKS × (1 + DIM_PCT(crop))^q

TOTAL_LABOR_HRS = sum of LABOR_HRS across all three crops at chosen bed counts

Labor cost:
- OWNER_HRS (720) are consumed first, at OWNER_RATE ($34.72/hr)
- Any remaining hours beyond OWNER_HRS are covered by temp workers at TEMP_RATE ($17.36/hr), up to TEMP_WORKER_CAP × TEMP_HRS_EACH (4 × 1,440 = 5,760 hrs max)
- BLENDED_LABOR_RATE = TOTAL_LABOR_COST / TOTAL_LABOR_HRS (one rate for the whole farm)
   APPLICABLE_LABOR_RATE = BLENDED_LABOR_RATE for every crop — the owner/temp split is a farm-wide fact, not calculated separately per crop.

FERTILIZER_COST(crop, q) = q × FERTILIZER_PER_BED(crop)

REVENUE(crop, q) = q × REVENUE_PER_BED(crop)

PROFIT = sum of REVENUE across all crops − sum of FERTILIZER_COST across all crops − TOTAL_LABOR_COST − FIXED_COSTS

## 4. Validation Rules

- q=1 hand check: 1 bed of tomatoes should require 1 × 2.5 × 36 × 1.10 = 99 hours exactly
- Cross-check: at least one intermediate marginal-cost value compared against the Farm Profit Lab
- Solver run from two starting points (0/0/0 and 20/0/0) — results should agree; if not, that is itself a finding
- No error cells (#REF!, #DIV/0!, #NAME?) anywhere in the workbook
- Every calculated cell contains a formula, not a pasted/typed number
- All constraint-check cells (bed caps, 64-bed total, temp worker cap) show green/passing
- Check figures match: optimal mix = 10 tomato / 20 carrot / 30 mesclun beds, profit = $42,762

## 5. Outputs

- Optimal bed counts for tomatoes, carrots, and mesclun
- Total season profit
- Marginal cost schedule for each crop (cost of the 1st through last bed)
- The bed count where each crop's marginal cost crosses its price, run standalone (not constrained by the 64-bed total)

## 6. Audit Findings

I checked the built model against the check figures in Section 4 and found two bugs.

**Bug 1 — Solver was using the wrong profit cell.** I noticed the profit target was showing 0, so I traced the formula back and found that the "Maximize PROFIT" cell was linked to an empty cell instead of the actual profit calculation.

**Bug 2 — Three input values had been rounded instead of using their exact values.** I noticed the final profit was off by about $13.49 from the published check figure, so I checked the input numbers and found the rounded carrot labor hours, owner hourly rate, and temporary-worker hourly rate.

**Fix and confirmation.** To fix both, I changed the Solver target to the correct profit cell and replaced the rounded inputs with the exact values (Section 1 now shows the corrected values). I then reran the calculations and confirmed the final profit matched the correct result of $42,761.66, and ran Solver from two different starting points (0/0/0 and 20/0/0) to check the answer — see the Checks tab for that result.
