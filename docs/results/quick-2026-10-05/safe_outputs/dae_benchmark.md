# DAE vs median benchmark (P2, corrected)

Generated 2026-10-05T14:06:42.681306+00:00 by `models/check_dae_benchmark.py`.
Un-imputed val_v2, truly known cells only, 10% masked per column (one column at a time), median = true median of known train_v2 cells.

| column | n masked | SD (val known) | RMSE median | RMSE DAE | better | improvement % |
|---|---|---|---|---|---|---|
| waist_cm | 12087 | 100.9 | 102.1 | 15.58 | DAE | 84.75 |
| hip_cm | 12087 | 99.48 | 103.3 | 13.94 | DAE | 86.51 |

- waist_cm: DAE RMSE 15.5759 vs median 102.1253 (84.75% lower); column SD 100.8551.
- hip_cm: DAE RMSE 13.9399 vs median 103.3214 (86.51% lower); column SD 99.478.

An RMSE close to the SD means the imputer is not much better than a constant.
