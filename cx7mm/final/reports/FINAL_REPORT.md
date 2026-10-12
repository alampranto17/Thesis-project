# CMx7-SI-DyGraph -- final run report

Generated 2026-10-12T14:26:02.750952+00:00 | pre-registration `reports/final_rule.json` | jobs still open: {'cog:core': 0, 'cmx7:core': 0, 'cog:benchmark': 0, 'cog:sweep': 0, 'cmx7:recent': 0, 'cog:recent': 0, 'cog:seeds': 0, 'cmx7:seeds': 0}

## Claims ledger

```
                                                   claim                                       evidence                                                           verdict
                           N1-T theory + TLCI diagnostic TLCI training folds: COG-BCI 0.000, CMx7 0.338                                                         DELIVERED
                      N1 collinearity sweep (H-S1..H-S3)                    n1_sweep/N1_SWEEP_REPORT.md                                                     NOT SUPPORTED
                      N1 TCAI on COG-BCI (H-N1a/c, E7.3)                               cogbci_tests.csv                                                  PARTLY SUPPORTED
N1-M IG-TCAI (non-inferior on CMx7, superior on COG-BCI)                              final_*_tests.csv                                                            PARTLY
                         H-V3 v3 > EEGNet + tricks (cog)                            final_cog_tests.csv                                                     NOT SUPPORTED
                                     v3 best model (cog)                         best-model rule (F0.6)            v3 is NOT the best: highest mean = EEGNet + EA + AdaBN
                        H-V3 v3 > EEGNet + tricks (cmx7)                           final_cmx7_tests.csv                                                     NOT SUPPORTED
                                    v3 best model (cmx7)                         best-model rule (F0.6) v3 is NOT the best: highest mean = CBraMod (frozen, linear probe)
```

## COG

```
                                                      model  fold_bal_acc_mean  ci_low  ci_high  within_task_rho  folds
                      EEGNet + EA + AdaBN (3-seed ensemble)              0.534   0.498    0.571            0.312     29
v3 proposed (EA + IG-TCAI + rank + AdaBN) (3-seed ensemble)              0.533   0.498    0.565            0.322     29
                                        EEGNet + EA + AdaBN              0.527   0.492    0.561            0.283     29
                                       CBraMod (fine-tuned)              0.523   0.483    0.565            0.375     29
                  v3 proposed (EA + IG-TCAI + rank + AdaBN)              0.523   0.489    0.557            0.298     29
                                              EEG-Conformer              0.521   0.483    0.561            0.256     29
                             CBraMod (frozen, linear probe)              0.506   0.454    0.559            0.361     29
                        Graph A (+consistency +subject adv)              0.496   0.460    0.533            0.380     29
                                  Graph B (+plain task GRL)              0.496   0.454    0.540            0.384     29
                                             ShallowConvNet              0.494   0.446    0.544            0.328     29
                                                     EEGNet              0.475   0.439    0.515            0.345     29
                                    EEGNet + plain task GRL              0.469   0.435    0.506            0.340     29
                                              EEGNet + TCAI              0.466   0.425    0.508            0.276     29
                                     IG-TCAI (EEGNet, N1-M)              0.456   0.425    0.487            0.305     29
                                            Graph C (+TCAI)              0.443   0.414    0.471            0.265     29
                                  Final model v2 (proposed)              0.439   0.398    0.483            0.347     29
                                  task-only lookup (no EEG)              0.333   0.333    0.333              NaN     29
```

```
                              test status family  mean_diff              ci  wins  losses      p   met  p_holm
        H-IG-SUP: IG-TCAI > EEGNet    run   None    -0.0192 (-0.056, 0.017)     8      16 0.8854 False     NaN
           (report) TCAI vs EEGNet    run   None    -0.0096 (-0.046, 0.027)    12      13 0.5802 False     NaN
        H-V3: v3 > EEGNet + tricks    run   H-V3    -0.0038 (-0.036, 0.033)     8      15 0.6872 False  0.9431
             (report) v3 vs EEGNet    run   None     0.0479  (0.006, 0.088)    17       8 0.0542 False     NaN
(report) EEGNet + tricks vs EEGNet    run   None     0.0517  (0.002, 0.102)    15       8 0.0726 False     NaN
```

Best-model rule: v3 is NOT the best: highest mean = EEGNet + EA + AdaBN

## CMX7

```
                                                      model  fold_bal_acc_mean  ci_low  ci_high  within_task_rho  folds
                                  task-only lookup (no EEG)              0.771   0.720    0.817              NaN     30
                      EEGNet + EA + AdaBN (3-seed ensemble)              0.468   0.405    0.527            0.108     30
v3 proposed (EA + IG-TCAI + rank + AdaBN) (3-seed ensemble)              0.463   0.401    0.522            0.118     30
                             CBraMod (frozen, linear probe)              0.445   0.401    0.493            0.085     30
                  v3 proposed (EA + IG-TCAI + rank + AdaBN)              0.432   0.378    0.485            0.093     30
                                                     EEGNet              0.428   0.378    0.481           -0.076     30
                                        EEGNet + EA + AdaBN              0.427   0.371    0.483            0.074     30
                                     IG-TCAI (EEGNet, N1-M)              0.417   0.360    0.477           -0.002     30
                                              EEGNet + TCAI              0.408   0.353    0.464           -0.128     30
                                              EEG-Conformer              0.403   0.355    0.449           -0.041     30
                                       CBraMod (fine-tuned)              0.391   0.352    0.427           -0.040     30
                                             ShallowConvNet              0.365   0.330    0.398           -0.214     30
```

```
                                            test status family  mean_diff              ci  wins  losses      p   met  p_holm
H-IG-NI: IG-TCAI non-inferior to EEGNet (margin)    run   None    -0.0109  (-0.069, 0.04)    11       6 0.0315  True     NaN
                    H-IG-vs-TCAI: IG-TCAI > TCAI    run   None     0.0095 (-0.043, 0.056)    11       7 0.2102 False     NaN
                      H-V3: v3 > EEGNet + tricks    run   H-V3     0.0053 (-0.032, 0.042)    12      12 0.4715 False  0.9431
                           (report) v3 vs EEGNet    run   None     0.0041 (-0.053, 0.055)    16      10 0.5506 False     NaN
              (report) EEGNet + tricks vs EEGNet    run   None    -0.0011 (-0.056, 0.055)    14      13 0.9234 False     NaN
```

Best-model rule: v3 is NOT the best: highest mean = CBraMod (frozen, linear probe)

COG-BCI pre-registered benchmark: `cogbci/COGBCI_REPORT.md`. N1 sweep: `cogbci/n1_sweep/N1_SWEEP_REPORT.md`.
