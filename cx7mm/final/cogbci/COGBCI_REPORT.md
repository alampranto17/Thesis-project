# COG-BCI external test

Generated 2026-10-12 14:25 UTC. Pre-registration: `results/cogbci_rule.json`.

**N1 verdict:** PARTLY SUPPORTED  
**Proposed-model claim:** not supported  
**Crossed-design check:** task-only 0.333

## Benchmark

| model                               |   fold_bal_acc_mean |   ci_low |   ci_high |   macro_f1 |   one_class_folds |   acc_nback |   acc_matb |   rho_score_vs_level |   rho_score_vs_rsme |
|:------------------------------------|--------------------:|---------:|----------:|-----------:|------------------:|------------:|-----------:|---------------------:|--------------------:|
| task-only lookup (no EEG)           |              0.3333 |   0.3333 |    0.3333 |     0.1667 |                29 |      0.3333 |     0.3333 |             nan      |            nan      |
| EEGNet                              |              0.4751 |   0.4387 |    0.5153 |     0.4455 |                 2 |      0.3985 |     0.5517 |               0.3768 |              0.3447 |
| EEGNet + plain task GRL             |              0.4693 |   0.4349 |    0.5057 |     0.4346 |                 3 |      0.3831 |     0.5556 |               0.3598 |              0.3404 |
| EEGNet + TCAI                       |              0.4655 |   0.4272 |    0.5077 |     0.4387 |                 5 |      0.387  |     0.5441 |               0.3413 |              0.2759 |
| Graph A (+consistency +subject adv) |              0.4962 |   0.4598 |    0.5345 |     0.4814 |                 1 |      0.4023 |     0.59   |               0.4225 |              0.3796 |
| Graph B (+plain task GRL)           |              0.4962 |   0.454  |    0.5402 |     0.4833 |                 2 |      0.4138 |     0.5785 |               0.3899 |              0.3837 |
| Graph C (+TCAI)                     |              0.4425 |   0.4138 |    0.4713 |     0.4319 |                 3 |      0.3793 |     0.5057 |               0.3326 |              0.2649 |
| Final model v2 (proposed)           |              0.4387 |   0.3985 |    0.4808 |     0.417  |                 1 |      0.3716 |     0.5057 |               0.3348 |              0.3468 |
| ShallowConvNet                      |              0.4943 |   0.4464 |    0.5441 |     0.4831 |                 2 |      0.4176 |     0.5709 |               0.386  |              0.3283 |
| EEG-Conformer                       |              0.5211 |   0.4847 |    0.5613 |     0.4908 |                 0 |      0.4138 |     0.6284 |               0.4429 |              0.2561 |
| CBraMod (frozen, linear probe)      |              0.5057 |   0.4559 |    0.5594 |     0.5031 |                 3 |      0.4483 |     0.5632 |               0.3975 |              0.3606 |
| CBraMod (fine-tuned)                |              0.523  |   0.4828 |    0.5651 |     0.5218 |                 0 |      0.4138 |     0.6322 |               0.4523 |              0.3747 |

## N1

| test                      | a               | b                                   |   delta |   ci_low |   ci_high |   wins |   losses |   rank_biserial_r |   p_raw | alternative   |   p_holm |
|:--------------------------|:----------------|:------------------------------------|--------:|---------:|----------:|-------:|---------:|------------------:|--------:|:--------------|---------:|
| H-N1a EEGNet: TCAI > none | EEGNet + TCAI   | EEGNet                              | -0.0096 |  -0.046  |    0.0268 |     12 |       13 |           -0.1262 |  0.7099 | greater       |        1 |
| H-N1a graph: TCAI > none  | Graph C (+TCAI) | Graph A (+consistency +subject adv) | -0.0536 |  -0.0958 |   -0.0134 |      8 |       17 |           -0.5354 |  0.9906 | greater       |        1 |

| test                        | a                         | b                                   |   delta |   ci_low |   ci_high |   wins |   losses |   rank_biserial_r |   p_raw | alternative   |   p_holm |
|:----------------------------|:--------------------------|:------------------------------------|--------:|---------:|----------:|-------:|---------:|------------------:|--------:|:--------------|---------:|
| H-N1b EEGNet: TCAI vs plain | EEGNet + TCAI             | EEGNet + plain task GRL             | -0.0038 |  -0.0441 |    0.0364 |      8 |       12 |           -0.019  |  0.9403 | two-sided     |   1      |
| H-N1b graph: TCAI vs plain  | Graph C (+TCAI)           | Graph B (+plain task GRL)           | -0.0536 |  -0.1073 |   -0.0057 |      9 |       19 |           -0.3719 |  0.0842 | two-sided     |   0.3368 |
| plain GRL vs none (EEGNet)  | EEGNet + plain task GRL   | EEGNet                              | -0.0057 |  -0.0402 |    0.0287 |     13 |       14 |           -0.0608 |  0.7812 | two-sided     |   1      |
| plain GRL vs none (graph)   | Graph B (+plain task GRL) | Graph A (+consistency +subject adv) | -0      |  -0.0345 |    0.0364 |     10 |       13 |            0.0036 |  0.9878 | two-sided     |   1      |

| test                           |   delta |   wins_lower |   p_raw |
|:-------------------------------|--------:|-------------:|--------:|
| H-N1c eegnet: task probe C < A | -0.0468 |           21 |  0.0011 |
| H-N1c graph: task probe C < A  | -0.0367 |           18 |  0.0054 |

## Proposed model vs EEGNet

| test                         | a                                   | b      |   delta |   ci_low |   ci_high |   wins |   losses |   rank_biserial_r |   p_raw | alternative   |   p_holm |
|:-----------------------------|:------------------------------------|:-------|--------:|---------:|----------:|-------:|---------:|------------------:|--------:|:--------------|---------:|
| H-M final model v2 vs EEGNet | Final model v2 (proposed)           | EEGNet | -0.0364 |  -0.0881 |    0.0153 |      9 |       15 |           -0.2867 |  0.2185 | two-sided     |   0.4371 |
| H-M Graph A vs EEGNet        | Graph A (+consistency +subject adv) | EEGNet |  0.0211 |  -0.0211 |    0.0613 |     15 |       10 |            0.2462 |  0.2808 | two-sided     |   0.4371 |

## Probes

| model                               |   task_probe |   workload_probe |
|:------------------------------------|-------------:|-----------------:|
| EEGNet                              |       0.6434 |           0.3676 |
| EEGNet + plain task GRL             |       0.5842 |           0.3692 |
| EEGNet + TCAI                       |       0.5967 |           0.3693 |
| Graph A (+consistency +subject adv) |       0.8147 |           0.396  |
| Graph B (+plain task GRL)           |       0.7719 |           0.4023 |
| Graph C (+TCAI)                     |       0.778  |           0.3908 |
