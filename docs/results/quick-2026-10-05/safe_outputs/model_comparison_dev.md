# Model comparison (VAL split)

Created 2026-10-05T14:08:54.977587+00:00. Rows evaluated: 6,596 (of 10,000 requested; rows a baseline could not fill by rejection sampling are dropped for all models). Outcome: elevated glucose (proxy), glucose >= 200 mg/dL. Aggregates only.
retained subset filled by every evaluated model, not full requested scope
CVAE: full scoped TRAIN with optional state; TVAE/CTGAN: stratified TRAIN subsample without state. Different data/state use, not a controlled architecture-only comparison.
TSTR uses held-out matched conditions (transductive utility), not independent cohort TSTR

| model | mean KS | corr diff (Frob.) | % >= threshold | P95 | P99 | cond. MAE pp | cond. max pp | directions | age in band | BMI in band | TSTR AUC |
|---|---|---|---|---|---|---|---|---|---|---|---|
| REAL | - | - | 1.455 | 145.2 | 272.4 | - | - | - | - | - | - |
| CVAE | 0.0358 | 1.563 | 1.243 | 145 | 254.2 | 0.6307 | 4.207 | 3/5 | 1 | 1 | 0.665 |
| TVAE | 0.13 | 2.347 | 0.2426 | 113 | 124 | 1.364 | 3.728 | 4/5 | 0.8119 | 0.7694 | 0.6351 |
| CTGAN | 0.2169 | 2.971 | 2.213 | 175 | 242.2 | 1.111 | 2.868 | 3/5 | 0.3047 | 0.3946 | 0.4857 |

TRTR AUC (real train -> real eval): CVAE: 0.75646, TVAE: 0.75646, CTGAN: 0.75646

Nearest-record distance, median (generated -> train vs real eval -> train): CVAE: 0.31739 vs 0.29458, TVAE: 0.29334 vs 0.29458, CTGAN: 1.3637 vs 0.29458

Full per-column, per-cell and per-sex numbers are in the JSON file.
