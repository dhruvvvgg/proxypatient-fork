# P2 Step 0: real-data checks

Generated 2026-10-05T14:04:51.435284+00:00 by `models/step0_checks.py`. Aggregates only; cells with n < 30 are suppressed.

## File integrity (SHA-256 vs MANIFEST.json)

| file | sha256 (first 16) | status |
|---|---|---|
| combined_clean_v2.parquet | f31e92a07451986c | OK |
| dae_fit_stats_v2.pkl | d25622a22e0d0921 | OK |
| dae_imputed_combined_v2.parquet | 039222506343a2f6 | OK |
| dae_imputed_test_v2.parquet | - | LOCKED (not hashed without --final-test) |
| dae_imputed_train_v2.parquet | 90bb74933d29b22f | OK |
| dae_imputed_val_v2.parquet | 59c1b3620194d238 | OK |
| dae_weights_v2.pt | 76f576884d86ddd4 | OK |
| men_clean_v2.parquet | e1a4d7757a7eabef | OK |
| preprocess_v2.pkl | 7d3a6075bbc3dc70 | OK |
| test_v2.parquet | - | LOCKED (not hashed without --final-test) |
| train_v2.parquet | e154230300770c4e | OK |
| val_v2.parquet | cbb5d3f54a6573da | OK |
| women_clean_v2.parquet | 4971b55a9e3e21e7 | OK |

## Split: train

Rows: raw 581542, DAE-imputed 581542; columns: 31.

### Columns, dtypes, NaN counts (raw v2 vs DAE-imputed v2)

| column | dtype (imputed) | NaN raw | NaN imputed |
|---|---|---|---|
| _row_id | int64 | - | - |
| sex | int64 | - | - |
| age | int64 | - | - |
| age_band | object | - | - |
| state | int64 | - | - |
| residence | object | - | - |
| education | int64 | - | - |
| wealth_quintile | int64 | - | - |
| waist_cm | float64 | 17552 | - |
| hip_cm | float64 | 17549 | - |
| any_tobacco | float64 | - | - |
| alcohol | float64 | - | - |
| glucose_ever_checked | float64 | 32334 | 32334 |
| told_high_glucose | float64 | 32334 | 32334 |
| on_glucose_medicine | float64 | 32361 | 32361 |
| glucose_time | float64 | 23008 | 23008 |
| glucose_raw | float64 | 22508 | 22508 |
| elevated_glucose_proxy | float64 | 22508 | 22508 |
| bp_ever_checked | float64 | 24412 | - |
| survey_weight | float64 | - | - |
| bmi | float64 | 24147 | 24147 |
| bmi_measured | int64 | - | - |
| bmi_band | object | 24147 | 24147 |
| weight_kg | float64 | 23377 | 23377 |
| height_cm | float64 | 514182 | 514182 |
| systolic_avg | float64 | 24398 | 24398 |
| diastolic_avg | float64 | 24401 | 24401 |
| bp_measured | int64 | - | - |
| on_bp_medication | float64 | 24477 | 24477 |
| hypertension | float64 | 24397 | 24397 |
| self_reported_hypertension | float64 | - | - |

Columns present in only one of raw/imputed: none

### Caveat checks

| check | value |
|---|---|
| women: rows | 509493 |
| women: glucose known | 491715 |
| women: glucose P5/P50/P95/P99 | 84.0 / 107.0 / 155.0 / 995.0 |
| women: share glucose >= 200 | 0.02796 |
| women: mean any_tobacco (non-missing n=509493) | 0.06368 |
| women: mean alcohol (non-missing n=509493) | 0.01856 |
| women: mean hypertension (non-missing n=489794) | 0.1208 |
| women: mean bmi_measured (non-missing n=509493) | 0.9619 |
| women: mean bp_measured (non-missing n=509493) | 0.9613 |
| women: BMI P1/P5/P50/P95/P99 | 14.97 / 16.53 / 21.68 / 30.24 / 35.51 |
| women: weight_kg P1/P50/P99 | 33.0 / 50.0 / 84.3 |
| women: waist_cm P1/P50/P99 | 53.3 / 77.2 / 999.5 |
| women: hip_cm P1/P50/P99 | 63.4 / 89.6 / 999.5 |
| men: rows | 72049 |
| men: glucose known | 67319 |
| men: glucose P5/P50/P95/P99 | 85.0 / 110.0 / 171.0 / 995.0 |
| men: share glucose >= 200 | 0.03469 |
| men: mean any_tobacco (non-missing n=72049) | 0.4337 |
| men: mean alcohol (non-missing n=72049) | 0.2601 |
| men: mean hypertension (non-missing n=67351) | 0.1931 |
| men: mean bmi_measured (non-missing n=72049) | 0.934 |
| men: mean bp_measured (non-missing n=72049) | 0.9348 |
| men: BMI P1/P5/P50/P95/P99 | 15.26 / 16.89 / 22.16 / 29.18 / 33.70 |
| men: height_cm P1/P50/P99 | 143.2 / 162.6 / 179.8 |
| men: weight_kg P1/P50/P99 | 37.7 / 58.2 / 93.8 |
| men: waist_cm P1/P50/P99 | 56.3 / 80.4 / 999.5 |
| men: hip_cm P1/P50/P99 | 64.1 / 90.1 / 999.5 |
| glucose median (all) -> unit verdict | 108.0 -> mg/dL |
| glucose known: women + men == total known? | 491715 + 67319 vs 559034 |
| sex values present | ['0', '1'] |
| rows where elevated_glucose_proxy != (glucose_raw >= threshold) | suppressed (n<30) |
| rows with glucose known but proxy missing (or reverse) | suppressed (n<30) |
| age_band label disagrees with numeric age (sex-specific bands) | suppressed (n<30) |
| women: ages outside [15, 49] | suppressed (n<30) |
| men: ages outside [15, 54] | suppressed (n<30) |
| bmi missing but bmi_measured==1 | suppressed (n<30) |
| bmi present but bmi_measured==0 | suppressed (n<30) |
| bmi_band labels | ['normal', 'obese', 'overweight', 'underweight'] |
| residence labels | ['rural', 'urban'] |
| state codes: n distinct / range | 36 / 1-37 |

## Split: val

Rows: raw 124618, DAE-imputed 124618; columns: 31.

### Columns, dtypes, NaN counts (raw v2 vs DAE-imputed v2)

| column | dtype (imputed) | NaN raw | NaN imputed |
|---|---|---|---|
| _row_id | int64 | - | - |
| sex | int64 | - | - |
| age | int64 | - | - |
| age_band | object | - | - |
| state | int64 | - | - |
| residence | object | - | - |
| education | int64 | - | - |
| wealth_quintile | int64 | - | - |
| waist_cm | float64 | 3744 | - |
| hip_cm | float64 | 3744 | - |
| any_tobacco | float64 | - | - |
| alcohol | float64 | - | - |
| glucose_ever_checked | float64 | 6929 | 6929 |
| told_high_glucose | float64 | 6929 | 6929 |
| on_glucose_medicine | float64 | 6938 | 6938 |
| glucose_time | float64 | 4945 | 4945 |
| glucose_raw | float64 | 4824 | 4824 |
| elevated_glucose_proxy | float64 | 4824 | 4824 |
| bp_ever_checked | float64 | 5218 | - |
| survey_weight | float64 | - | - |
| bmi | float64 | 5214 | 5214 |
| bmi_measured | int64 | - | - |
| bmi_band | object | 5214 | 5214 |
| weight_kg | float64 | 5039 | 5039 |
| height_cm | float64 | 110131 | 110131 |
| systolic_avg | float64 | 5215 | 5215 |
| diastolic_avg | float64 | 5218 | 5218 |
| bp_measured | int64 | - | - |
| on_bp_medication | float64 | 5232 | 5232 |
| hypertension | float64 | 5215 | 5215 |
| self_reported_hypertension | float64 | - | - |

Columns present in only one of raw/imputed: none

### Caveat checks

| check | value |
|---|---|
| women: rows | 109145 |
| women: glucose known | 105300 |
| women: glucose P5/P50/P95/P99 | 84.0 / 107.0 / 156.0 / 995.0 |
| women: share glucose >= 200 | 0.02809 |
| women: mean any_tobacco (non-missing n=109145) | 0.06417 |
| women: mean alcohol (non-missing n=109145) | 0.01908 |
| women: mean hypertension (non-missing n=104913) | 0.1219 |
| women: mean bmi_measured (non-missing n=109145) | 0.9615 |
| women: mean bp_measured (non-missing n=109145) | 0.9612 |
| women: BMI P1/P5/P50/P95/P99 | 15.03 / 16.54 / 21.67 / 30.19 / 35.60 |
| women: weight_kg P1/P50/P99 | 33.1 / 50.0 / 84.1 |
| women: waist_cm P1/P50/P99 | 53.2 / 77.0 / 999.5 |
| women: hip_cm P1/P50/P99 | 63.1 / 89.6 / 999.5 |
| men: rows | 15473 |
| men: glucose known | 14494 |
| men: glucose P5/P50/P95/P99 | 85.0 / 109.0 / 168.0 / 995.0 |
| men: share glucose >= 200 | 0.03374 |
| men: mean any_tobacco (non-missing n=15473) | 0.4326 |
| men: mean alcohol (non-missing n=15473) | 0.2522 |
| men: mean hypertension (non-missing n=14490) | 0.1854 |
| men: mean bmi_measured (non-missing n=15473) | 0.9347 |
| men: mean bp_measured (non-missing n=15473) | 0.9365 |
| men: BMI P1/P5/P50/P95/P99 | 15.23 / 16.89 / 22.13 / 29.05 / 33.51 |
| men: height_cm P1/P50/P99 | 142.8 / 162.7 / 180.2 |
| men: weight_kg P1/P50/P99 | 37.3 / 58.3 / 93.8 |
| men: waist_cm P1/P50/P99 | 56.2 / 80.3 / 999.5 |
| men: hip_cm P1/P50/P99 | 64.3 / 90.1 / 999.5 |
| glucose median (all) -> unit verdict | 107.0 -> mg/dL |
| glucose known: women + men == total known? | 105300 + 14494 vs 119794 |
| sex values present | ['0', '1'] |
| rows where elevated_glucose_proxy != (glucose_raw >= threshold) | suppressed (n<30) |
| rows with glucose known but proxy missing (or reverse) | suppressed (n<30) |
| age_band label disagrees with numeric age (sex-specific bands) | suppressed (n<30) |
| women: ages outside [15, 49] | suppressed (n<30) |
| men: ages outside [15, 54] | suppressed (n<30) |
| bmi missing but bmi_measured==1 | suppressed (n<30) |
| bmi present but bmi_measured==0 | suppressed (n<30) |
| bmi_band labels | ['normal', 'obese', 'overweight', 'underweight'] |
| residence labels | ['rural', 'urban'] |
| state codes: n distinct / range | 36 / 1-37 |

## Training scope (train split)

Scope `complete_conditions`: 550923 of 581542 rows in scope (94.73%).

| rule (applied in order) | excluded | women | men |
|---|---|---|---|
| glucose_raw known | 22508 | 17778 | 4730 |
| bmi_measured == 1 | 6422 | 5525 | 897 |
| hypertension not null | 1689 | 1511 | 178 |

Share excluded by sex and harmonised age band:

| cell | share excluded |
|---|---|
| sex=0, age=15-24 | 0.05259 |
| sex=0, age=25-34 | 0.04154 |
| sex=0, age=35+ | 0.05109 |
| sex=1, age=15-24 | 0.07891 |
| sex=1, age=25-34 | 0.0812 |
| sex=1, age=35+ | 0.08136 |

## Condition cell sizes (in-scope train, all 8 conditions jointly)

|  | count |
|---|---|
| possible_full_condition_cells | 1920 |
| observed | 1696 |
| n<30 | 957 |
| 30<=n<500 | 577 |
| n>=500 | 162 |
| never_observed | 224 |

Rows with any missing condition after scope: None (by condition: sex=None, age_band=None, residence=None, wealth_quintile=None, bmi_band=None, hypertension=None, tobacco=None, alcohol=None)

## Outcome: elevated glucose (proxy) rate, single variables and pairs (in-scope train, unweighted)

Overall: n=550923, rate=1.869%.

| variables | cell | n | rate % |
|---|---|---|---|
| sex | 0 | 484679 | 1.795 |
| sex | 1 | 66244 | 2.409 |
| age_band | 15-24 | 181135 | 0.835 |
| age_band | 25-34 | 165510 | 1.248 |
| age_band | 35+ | 204278 | 3.29 |
| residence | rural | 416505 | 1.567 |
| residence | urban | 134418 | 2.804 |
| wealth_quintile | 1 | 113989 | 1.117 |
| wealth_quintile | 2 | 123102 | 1.353 |
| wealth_quintile | 3 | 116220 | 1.819 |
| wealth_quintile | 4 | 106524 | 2.445 |
| wealth_quintile | 5 | 91088 | 2.899 |
| bmi_band | normal | 333308 | 1.36 |
| bmi_band | obese | 28037 | 5.839 |
| bmi_band | overweight | 93058 | 3.471 |
| bmi_band | underweight | 96520 | 0.93 |
| hypertension | 0 | 483024 | 1.451 |
| hypertension | 1 | 67899 | 4.84 |
| tobacco | 0 | 490625 | 1.855 |
| tobacco | 1 | 60298 | 1.987 |
| alcohol | 0 | 524542 | 1.857 |
| alcohol | 1 | 26381 | 2.111 |
| sex+age_band | 0|15-24 | 160965 | 0.843 |
| sex+age_band | 0|25-34 | 147541 | 1.243 |
| sex+age_band | 0|35+ | 176173 | 3.128 |
| sex+age_band | 1|15-24 | 20170 | 0.768 |
| sex+age_band | 1|25-34 | 17969 | 1.286 |
| sex+age_band | 1|35+ | 28105 | 4.305 |
| sex+residence | 0|rural | 367022 | 1.502 |
| sex+residence | 0|urban | 117657 | 2.711 |
| sex+residence | 1|rural | 49483 | 2.055 |
| sex+residence | 1|urban | 16761 | 3.454 |
| sex+wealth_quintile | 0|1 | 100973 | 1.103 |
| sex+wealth_quintile | 0|2 | 108210 | 1.317 |
| sex+wealth_quintile | 0|3 | 102012 | 1.729 |
| sex+wealth_quintile | 0|4 | 93540 | 2.339 |
| sex+wealth_quintile | 0|5 | 79944 | 2.764 |
| sex+wealth_quintile | 1|1 | 13016 | 1.222 |
| sex+wealth_quintile | 1|2 | 14892 | 1.612 |
| sex+wealth_quintile | 1|3 | 14208 | 2.463 |
| sex+wealth_quintile | 1|4 | 12984 | 3.204 |
| sex+wealth_quintile | 1|5 | 11144 | 3.868 |
| sex+bmi_band | 0|normal | 291711 | 1.295 |
| sex+bmi_band | 0|obese | 25675 | 5.651 |
| sex+bmi_band | 0|overweight | 80465 | 3.339 |
| sex+bmi_band | 0|underweight | 86828 | 0.904 |
| sex+bmi_band | 1|normal | 41597 | 1.813 |
| sex+bmi_band | 1|obese | 2362 | 7.875 |
| sex+bmi_band | 1|overweight | 12593 | 4.312 |
| sex+bmi_band | 1|underweight | 9692 | 1.166 |
| sex+hypertension | 0|0 | 428914 | 1.423 |
| sex+hypertension | 0|1 | 55765 | 4.655 |
| sex+hypertension | 1|0 | 54110 | 1.674 |
| sex+hypertension | 1|1 | 12134 | 5.687 |
| sex+tobacco | 0|0 | 453374 | 1.8 |
| sex+tobacco | 0|1 | 31305 | 1.725 |
| sex+tobacco | 1|0 | 37251 | 2.518 |
| sex+tobacco | 1|1 | 28993 | 2.27 |
| sex+alcohol | 0|0 | 475623 | 1.807 |
| sex+alcohol | 0|1 | 9056 | 1.193 |
| sex+alcohol | 1|0 | 48919 | 2.345 |
| sex+alcohol | 1|1 | 17325 | 2.592 |
| age_band+residence | 15-24|rural | 140517 | 0.715 |
| age_band+residence | 15-24|urban | 40618 | 1.251 |
| age_band+residence | 25-34|rural | 124224 | 1.095 |
| age_band+residence | 25-34|urban | 41286 | 1.708 |
| age_band+residence | 35+|rural | 151764 | 2.744 |
| age_band+residence | 35+|urban | 52514 | 4.867 |
| age_band+wealth_quintile | 15-24|1 | 39583 | 0.627 |
| age_band+wealth_quintile | 15-24|2 | 43423 | 0.712 |
| age_band+wealth_quintile | 15-24|3 | 38850 | 0.746 |
| age_band+wealth_quintile | 15-24|4 | 33527 | 1.002 |
| age_band+wealth_quintile | 15-24|5 | 25752 | 1.278 |
| age_band+wealth_quintile | 25-34|1 | 33802 | 0.902 |
| age_band+wealth_quintile | 25-34|2 | 35603 | 0.952 |
| age_band+wealth_quintile | 25-34|3 | 34271 | 1.164 |
| age_band+wealth_quintile | 25-34|4 | 32885 | 1.566 |
| age_band+wealth_quintile | 25-34|5 | 28949 | 1.751 |
| age_band+wealth_quintile | 35+|1 | 40604 | 1.773 |
| age_band+wealth_quintile | 35+|2 | 44076 | 2.307 |
| age_band+wealth_quintile | 35+|3 | 43099 | 3.306 |
| age_band+wealth_quintile | 35+|4 | 40112 | 4.37 |
| age_band+wealth_quintile | 35+|5 | 36387 | 4.961 |
| age_band+bmi_band | 15-24|normal | 111729 | 0.772 |
| age_band+bmi_band | 15-24|obese | 2858 | 1.994 |
| age_band+bmi_band | 15-24|overweight | 12159 | 1.637 |
| age_band+bmi_band | 15-24|underweight | 54389 | 0.723 |
| age_band+bmi_band | 25-34|normal | 104182 | 0.949 |
| age_band+bmi_band | 25-34|obese | 8386 | 3.363 |
| age_band+bmi_band | 25-34|overweight | 30461 | 1.911 |
| age_band+bmi_band | 25-34|underweight | 22481 | 0.943 |
| age_band+bmi_band | 35+|normal | 117397 | 2.283 |
| age_band+bmi_band | 35+|obese | 16793 | 7.729 |
| age_band+bmi_band | 35+|overweight | 50438 | 4.855 |
| age_band+bmi_band | 35+|underweight | 19650 | 1.491 |
| age_band+hypertension | 15-24|0 | 173141 | 0.818 |
| age_band+hypertension | 15-24|1 | 7994 | 1.201 |
| age_band+hypertension | 25-34|0 | 149978 | 1.123 |
| age_band+hypertension | 25-34|1 | 15532 | 2.453 |
| age_band+hypertension | 35+|0 | 159905 | 2.446 |
| age_band+hypertension | 35+|1 | 44373 | 6.33 |
| age_band+tobacco | 15-24|0 | 172279 | 0.844 |
| age_band+tobacco | 15-24|1 | 8856 | 0.655 |
| age_band+tobacco | 25-34|0 | 147393 | 1.27 |
| age_band+tobacco | 25-34|1 | 18117 | 1.065 |
| age_band+tobacco | 35+|0 | 170953 | 3.377 |
| age_band+tobacco | 35+|1 | 33325 | 2.842 |
| age_band+alcohol | 15-24|0 | 177513 | 0.84 |
| age_band+alcohol | 15-24|1 | 3622 | 0.58 |
| age_band+alcohol | 25-34|0 | 157242 | 1.254 |
| age_band+alcohol | 25-34|1 | 8268 | 1.125 |
| age_band+alcohol | 35+|0 | 189787 | 3.307 |
| age_band+alcohol | 35+|1 | 14491 | 3.057 |
| residence+wealth_quintile | rural|1 | 109866 | 1.11 |
| residence+wealth_quintile | rural|2 | 112479 | 1.295 |
| residence+wealth_quintile | rural|3 | 93130 | 1.695 |
| residence+wealth_quintile | rural|4 | 66020 | 2.142 |
| residence+wealth_quintile | rural|5 | 35010 | 2.451 |
| residence+wealth_quintile | urban|1 | 4123 | 1.285 |
| residence+wealth_quintile | urban|2 | 10623 | 1.958 |
| residence+wealth_quintile | urban|3 | 23090 | 2.317 |
| residence+wealth_quintile | urban|4 | 40504 | 2.938 |
| residence+wealth_quintile | urban|5 | 56078 | 3.179 |
| residence+bmi_band | rural|normal | 258733 | 1.214 |
| residence+bmi_band | rural|obese | 15920 | 5.082 |
| residence+bmi_band | rural|overweight | 62405 | 3.022 |
| residence+bmi_band | rural|underweight | 79447 | 0.872 |
| residence+bmi_band | urban|normal | 74575 | 1.867 |
| residence+bmi_band | urban|obese | 12117 | 6.833 |
| residence+bmi_band | urban|overweight | 30653 | 4.385 |
| residence+bmi_band | urban|underweight | 17073 | 1.201 |
| residence+hypertension | rural|0 | 366997 | 1.236 |
| residence+hypertension | rural|1 | 49508 | 4.024 |
| residence+hypertension | urban|0 | 116027 | 2.133 |
| residence+hypertension | urban|1 | 18391 | 7.036 |
| residence+tobacco | rural|0 | 367831 | 1.552 |
| residence+tobacco | rural|1 | 48674 | 1.685 |
| residence+tobacco | urban|0 | 122794 | 2.762 |
| residence+tobacco | urban|1 | 11624 | 3.252 |
| residence+alcohol | rural|0 | 395276 | 1.557 |
| residence+alcohol | rural|1 | 21229 | 1.766 |
| residence+alcohol | urban|0 | 129266 | 2.775 |
| residence+alcohol | urban|1 | 5152 | 3.533 |
| wealth_quintile+bmi_band | 1|normal | 74284 | 1.003 |
| wealth_quintile+bmi_band | 1|obese | 1537 | 3.448 |
| wealth_quintile+bmi_band | 1|overweight | 9171 | 2.464 |
| wealth_quintile+bmi_band | 1|underweight | 28997 | 0.859 |
| wealth_quintile+bmi_band | 2|normal | 79095 | 1.163 |
| wealth_quintile+bmi_band | 2|obese | 3287 | 3.985 |
| wealth_quintile+bmi_band | 2|overweight | 15975 | 2.504 |
| wealth_quintile+bmi_band | 2|underweight | 24745 | 0.865 |
| wealth_quintile+bmi_band | 3|normal | 70878 | 1.356 |
| wealth_quintile+bmi_band | 3|obese | 5386 | 5.533 |
| wealth_quintile+bmi_band | 3|overweight | 20514 | 3.261 |
| wealth_quintile+bmi_band | 3|underweight | 19442 | 0.957 |
| wealth_quintile+bmi_band | 4|normal | 61113 | 1.684 |
| wealth_quintile+bmi_band | 4|obese | 7676 | 6.397 |
| wealth_quintile+bmi_band | 4|overweight | 23266 | 4.002 |
| wealth_quintile+bmi_band | 4|underweight | 14469 | 1.057 |
| wealth_quintile+bmi_band | 5|normal | 47938 | 1.829 |
| wealth_quintile+bmi_band | 5|obese | 10151 | 6.541 |
| wealth_quintile+bmi_band | 5|overweight | 24132 | 4.16 |
| wealth_quintile+bmi_band | 5|underweight | 8867 | 1.083 |
| wealth_quintile+hypertension | 1|0 | 101638 | 0.94 |
| wealth_quintile+hypertension | 1|1 | 12351 | 2.575 |
| wealth_quintile+hypertension | 2|0 | 108836 | 1.099 |
| wealth_quintile+hypertension | 2|1 | 14266 | 3.288 |
| wealth_quintile+hypertension | 3|0 | 101774 | 1.389 |
| wealth_quintile+hypertension | 3|1 | 14446 | 4.846 |
| wealth_quintile+hypertension | 4|0 | 92502 | 1.877 |
| wealth_quintile+hypertension | 4|1 | 14022 | 6.19 |
| wealth_quintile+hypertension | 5|0 | 78274 | 2.185 |
| wealth_quintile+hypertension | 5|1 | 12814 | 7.265 |
| wealth_quintile+tobacco | 1|0 | 94054 | 1.099 |
| wealth_quintile+tobacco | 1|1 | 19935 | 1.199 |
| wealth_quintile+tobacco | 2|0 | 106548 | 1.299 |
| wealth_quintile+tobacco | 2|1 | 16554 | 1.697 |
| wealth_quintile+tobacco | 3|0 | 104239 | 1.76 |
| wealth_quintile+tobacco | 3|1 | 11981 | 2.329 |
| wealth_quintile+tobacco | 4|0 | 98680 | 2.385 |
| wealth_quintile+tobacco | 4|1 | 7844 | 3.187 |
| wealth_quintile+tobacco | 5|0 | 87104 | 2.861 |
| wealth_quintile+tobacco | 5|1 | 3984 | 3.74 |
| wealth_quintile+alcohol | 1|0 | 105507 | 1.126 |
| wealth_quintile+alcohol | 1|1 | 8482 | 1.002 |
| wealth_quintile+alcohol | 2|0 | 116738 | 1.347 |
| wealth_quintile+alcohol | 2|1 | 6364 | 1.446 |
| wealth_quintile+alcohol | 3|0 | 111097 | 1.788 |
| wealth_quintile+alcohol | 3|1 | 5123 | 2.499 |
| wealth_quintile+alcohol | 4|0 | 102849 | 2.408 |
| wealth_quintile+alcohol | 4|1 | 3675 | 3.456 |
| wealth_quintile+alcohol | 5|0 | 88351 | 2.848 |
| wealth_quintile+alcohol | 5|1 | 2737 | 4.567 |
| bmi_band+hypertension | normal|0 | 298862 | 1.136 |
| bmi_band+hypertension | normal|1 | 34446 | 3.298 |
| bmi_band+hypertension | obese|0 | 19988 | 4.293 |
| bmi_band+hypertension | obese|1 | 8049 | 9.678 |
| bmi_band+hypertension | overweight|0 | 73670 | 2.647 |
| bmi_band+hypertension | overweight|1 | 19388 | 6.602 |
| bmi_band+hypertension | underweight|0 | 90504 | 0.892 |
| bmi_band+hypertension | underweight|1 | 6016 | 1.513 |
| bmi_band+tobacco | normal|0 | 294366 | 1.339 |
| bmi_band+tobacco | normal|1 | 38942 | 1.518 |
| bmi_band+tobacco | obese|0 | 26007 | 5.795 |
| bmi_band+tobacco | obese|1 | 2030 | 6.404 |
| bmi_band+tobacco | overweight|0 | 83185 | 3.441 |
| bmi_band+tobacco | overweight|1 | 9873 | 3.727 |
| bmi_band+tobacco | underweight|0 | 87067 | 0.906 |
| bmi_band+tobacco | underweight|1 | 9453 | 1.153 |
| bmi_band+alcohol | normal|0 | 316284 | 1.348 |
| bmi_band+alcohol | normal|1 | 17024 | 1.568 |
| bmi_band+alcohol | obese|0 | 27015 | 5.826 |
| bmi_band+alcohol | obese|1 | 1022 | 6.164 |
| bmi_band+alcohol | overweight|0 | 88055 | 3.451 |
| bmi_band+alcohol | overweight|1 | 5003 | 3.818 |
| bmi_band+alcohol | underweight|0 | 93188 | 0.925 |
| bmi_band+alcohol | underweight|1 | 3332 | 1.08 |
| hypertension+tobacco | 0|0 | 433393 | 1.448 |
| hypertension+tobacco | 0|1 | 49631 | 1.485 |
| hypertension+tobacco | 1|0 | 57232 | 4.936 |
| hypertension+tobacco | 1|1 | 10667 | 4.322 |
| hypertension+alcohol | 0|0 | 462692 | 1.451 |
| hypertension+alcohol | 0|1 | 20332 | 1.471 |
| hypertension+alcohol | 1|0 | 61850 | 4.896 |
| hypertension+alcohol | 1|1 | 6049 | 4.265 |
| tobacco+alcohol | 0|0 | 480350 | 1.844 |
| tobacco+alcohol | 0|1 | 10275 | 2.355 |
| tobacco+alcohol | 1|0 | 44192 | 1.998 |
| tobacco+alcohol | 1|1 | 16106 | 1.956 |

## States with fewer than 500 rows (train, before scope)

None.
