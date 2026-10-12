# N1 collinearity sweep (COG-BCI)

**Verdict:** NOT SUPPORTED

Pre-registration: `results/n1_sweep_rule.json`. Designed after the CMx7 N1 result (NOT SUPPORTED) was known and while the main COG-BCI benchmark was training (partial training logs visible, E7 not run). Separate experiment; it does not replace the main COG-BCI N1 test.

## Collinearity index

```
                 dataset                             level  TLCI  shortcut  train_fit_task_only_bal_acc  train_recordings_per_fold class_counts_per_fold  nback_share
           COG-BCI sweep                        L0_crossed 0.000     0.000                        0.333                      216.0            [72 72 72]        0.500
           COG-BCI sweep                     L1_correlated 0.360     0.227                        0.602                      216.0            [72 72 72]        0.500
           COG-BCI sweep                      L2_collinear 1.000     0.579                        0.667                      216.0            [72 72 72]        0.667
COG-BCI (all recordings)                           natural 0.000     0.000                          NaN                        NaN                   NaN          NaN
                 CMx7-MM  natural (label = rating tertile) 0.264     0.466                          NaN                        NaN                   NaN          NaN
                 CMx7-MM natural (TCAI condition = rating) 0.333     0.310                          NaN                        NaN                   NaN          NaN
```

## Accuracy per level

```
        level  TLCI              model  mean_bal_acc  ci_low  ci_high
   L0_crossed  0.00           A EEGNet         0.481   0.430    0.530
   L0_crossed  0.00 B + plain task GRL         0.426   0.385    0.470
   L0_crossed  0.00           C + TCAI         0.437   0.407    0.467
   L0_crossed  0.00   task-only lookup         0.333   0.333    0.333
L1_correlated  0.36           A EEGNet         0.363   0.341    0.396
L1_correlated  0.36 B + plain task GRL         0.385   0.352    0.426
L1_correlated  0.36           C + TCAI         0.381   0.359    0.407
L1_correlated  0.36   task-only lookup         0.333   0.333    0.333
 L2_collinear  1.00           A EEGNet         0.341   0.311    0.370
 L2_collinear  1.00 B + plain task GRL         0.348   0.326    0.374
 L2_collinear  1.00           C + TCAI         0.363   0.337    0.393
 L2_collinear  1.00   task-only lookup         0.333   0.333    0.333
```

## Tests

```
                              test  mean_diff              ci  wins  losses  p_one_sided   met  p_two_sided
H-S1 A(L0) > A(L2)  [manipulation]     0.1407  (0.089, 0.193)    12       0       0.0011  True          NaN
  H-S2 C(L1) > A(L1)  [primary N1]     0.0185 (-0.015, 0.048)     6       1       0.0862 False          NaN
 H-S3 gain(L1) > gain(L2)  [shape]    -0.0037  (-0.07, 0.052)     6       5       0.2518 False          NaN
      (report) C - A at L0_crossed    -0.0444   (-0.1, 0.011)     4       8          NaN  None       0.1808
      (report) C - B at L0_crossed     0.0111 (-0.022, 0.041)     7       3          NaN  None       0.5733
      (report) B - A at L0_crossed    -0.0556 (-0.119, 0.004)     4       7          NaN  None       0.1088
   (report) C - B at L1_correlated    -0.0037 (-0.048, 0.037)     4       3          NaN  None       0.9314
   (report) B - A at L1_correlated     0.0222 (-0.026, 0.067)     5       1          NaN  None       0.2918
    (report) C - A at L2_collinear     0.0222 (-0.011, 0.059)     5       4          NaN  None       0.3385
    (report) C - B at L2_collinear     0.0148 (-0.007, 0.037)     6       3          NaN  None       0.1303
    (report) B - A at L2_collinear     0.0074 (-0.022, 0.041)     4       6          NaN  None       0.8776
```

