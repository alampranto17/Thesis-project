# CMx7-SI-DyGraph — Final Results Report

Generated 2026-10-12 18:44 UTC from the saved result files (no recomputation). Random seed 42.

## 1. Study design

- Dataset: CMx7-MM, 30 subjects, 514 recordings (7 tasks x 3 sessions), 32 EEG channels at 250 Hz.
- Preprocessing: 1.0-40.0 Hz band-pass, average reference, notch False; windows 4.0 s, step 2.0 s, 3.0 s transition exclusion.
- Labels: low / medium / high workload from each fold's TRAINING-subject rating tertiles.
- Protocols: leave-one-subject-out (30 folds, 4 separate validation subjects per fold) and cross-session (3 folds: one held-out session).
- Evaluation: recording level (softmax averaged over windows); balanced accuracy, macro-F1, within-task Spearman ρ.
- All model and hyper-parameter choices were made on validation subjects; test subjects were used only for the reported numbers.

## 2. Claims ledger

| claim | statement | evidence | verdict |
|---|---|---|---|
| N3a LOSO benchmark | 14 EEG models on identical 30-subject LOSO folds | best EEG model EEGNet + plain GRL 0.459 [0.407, 0.515]; 8/14 above chance after Holm; Friedman p 1.52e-18 | DELIVERED |
| N3b cross-session benchmark | same models, unseen session of known people | best EEG model Graph A (+consistency +subject adv) 0.444; task-only 0.771 | DELIVERED |
| N2-1 task-only reference | EEG models do not exceed a no-EEG task lookup | task-only 0.771; 14/14 EEG models significantly below it (Holm) | SUPPORTED |
| N2-2 within-task agreement | no LOSO model tracks the rating inside a task | models with within-task ρ CI above 0: none | SUPPORTED |
| N2-3 within-task permutation | EEGNet's accuracy survives shuffling the ratings inside each task (task-level) | Δ -0.014 [-0.079, +0.046], r_rb +0.00, p_Holm 1 | SUPPORTED |
| N2-5 stimulus rhythm | stimulus timing carries a task cue | rhythm decoder 0.190 vs null 0.141, permutation p 0.0099 | SUPPORTED (weak cue) |
| RQ1 EEGNet mechanism | EEGNet mainly separates motor from cognitive tasks (pre-registered, 22C) | 22C H-a probe and H-b accuracy | SUPPORTED |
| N1 TCAI, EEGNet LOSO | TCAI beats plain GRL (pre-registered C1-C3) | verdict NOT SUPPORTED; Δ -0.038 [-0.083, +0.003], r_rb -0.44, p_Holm 0.763 | NOT SUPPORTED |
| N1 TCAI, graph LOSO | TCAI improves the graph model | vs plain GRL Δ -0.041 [-0.086, -0.004], r_rb -0.53, p_Holm 0.486; removing TCAI from the final model Δ +0.034 [-0.032, +0.100], r_rb +0.22, p_Holm 1 | NOT SUPPORTED |
| N1 TCAI, cross-session | TCAI >= plain GRL on macro-F1 and within-task ρ | EEGNet: C1 True, C2 False, ρ C-B CI (-0.055, 0.042); graph: C1 False, C2 True, ρ C-B CI (-0.091, 0.122) | NOT SUPPORTED |
| Subject adversary | removing the subject adversary lowers accuracy | Δ -0.020 [-0.064, +0.026], r_rb -0.32, p_Holm 1 | NOT SUPPORTED (direction only) |
| Normalisation is not the cause | recording_scaled input does not change the conclusions (D-027) | Δ -0.033 [-0.092, +0.021], r_rb -0.20, p_Holm 1 / Δ +0.009 [-0.060, +0.077], r_rb +0.11, p_Holm 1 | SUPPORTED |
| Artefact shortcut audit | models do not rely on EMG / eye regions (25) | EEGNet: EMG warning False, eye warning False, top band delta; Final model v2: EMG warning False, eye warning False, top band beta | NO WARNING |

## 3. LOSO benchmark (N3)

| model | fold_bal_acc_mean | ci_low | ci_high | macro_f1 | one_class_folds | within_task_rho | rho_ci_low | rho_ci_high | p_holm_vs_chance | p_holm_vs_task_only |
|---|---|---|---|---|---|---|---|---|---|---|
| task name only (no EEG) | 0.771 | 0.720 | 0.818 | 0.744 | 0 |  |  |  |  |  |
| Temporal CNN | 0.407 | 0.367 | 0.450 | 0.366 | 8 | -0.129 | -0.308 | 0.081 | 0.023 | 0.000 |
| EEGNet | 0.452 | 0.401 | 0.508 | 0.448 | 8 | -0.041 | -0.213 | 0.141 | 0.004 | 0.000 |
| EEGNet + plain GRL | 0.459 | 0.407 | 0.515 | 0.450 | 10 | -0.076 | -0.239 | 0.094 | 0.002 | 0.000 |
| EEGNet + TCAI | 0.421 | 0.365 | 0.481 | 0.428 | 11 | -0.092 | -0.277 | 0.118 | 0.056 | 0.000 |
| Fixed-graph GCN | 0.423 | 0.383 | 0.466 | 0.360 | 9 | -0.043 | -0.217 | 0.135 | 0.007 | 0.000 |
| Static learnable graph | 0.405 | 0.369 | 0.448 | 0.409 | 7 | -0.037 | -0.200 | 0.143 | 0.006 | 0.000 |
| Dynamic graph | 0.410 | 0.370 | 0.455 | 0.352 | 8 | -0.086 | -0.232 | 0.082 | 0.008 | 0.000 |
| + graph consistency | 0.424 | 0.387 | 0.467 | 0.350 | 8 | -0.140 | -0.310 | 0.054 | 0.003 | 0.000 |
| + subject adversary | 0.410 | 0.367 | 0.451 | 0.358 | 9 | -0.054 | -0.221 | 0.127 | 0.009 | 0.000 |
| + plain task GRL (graph) | 0.364 | 0.319 | 0.408 | 0.302 | 10 | -0.175 | -0.329 | -0.003 | 0.494 | 0.000 |
| + TCAI (graph) | 0.322 | 0.280 | 0.361 | 0.317 | 9 | -0.008 | -0.223 | 0.189 | 1.000 | 0.000 |
| Full model v1 (seed 0) | 0.333 | 0.294 | 0.368 | 0.350 | 17 | -0.188 | -0.333 | 0.002 | 1.000 | 0.000 |
| Full model v1 (seed ensemble) | 0.324 | 0.296 | 0.353 | 0.323 | 17 | -0.158 | -0.317 | 0.047 | 1.000 | 0.000 |
| Final model v2 | 0.349 | 0.305 | 0.390 | 0.319 | 12 | 0.049 | -0.125 | 0.204 | 1.000 | 0.000 |
| Final − TCAI | 0.382 | 0.334 | 0.429 | 0.353 | 7 | 0.005 | -0.149 | 0.156 |  |  |
| Final − subject adversary | 0.328 | 0.288 | 0.366 | 0.318 | 11 | -0.040 | -0.214 | 0.141 |  |  |
| Final − graph consistency | 0.332 | 0.292 | 0.371 | 0.334 | 8 | -0.095 | -0.251 | 0.063 |  |  |
| EEGNet, recording_scaled | 0.419 | 0.365 | 0.470 | 0.385 | 7 | -0.109 | -0.353 | 0.163 |  |  |
| Final, recording_scaled | 0.357 | 0.311 | 0.403 | 0.358 | 10 | 0.003 | -0.192 | 0.196 |  |  |
| EEGNet, within-task permuted labels | 0.438 | 0.380 | 0.496 | 0.426 | 8 | 0.013 | -0.175 | 0.205 |  |  |
| Final, within-task permuted labels | 0.349 | 0.303 | 0.398 | 0.362 | 4 | 0.020 | -0.147 | 0.172 |  |  |


Friedman test: χ² = 118.04, p = 1.52e-18; Nemenyi CD = 3.916.


| model | average_rank | differs_from_best_by_more_than_CD |
|---|---|---|
| task name only (no EEG) | 1.633 | False |
| EEGNet + plain GRL | 6.717 | True |
| + subject adversary | 7.000 | True |
| EEGNet | 7.167 | True |
| Fixed-graph GCN | 7.367 | True |
| + graph consistency | 7.383 | True |
| EEGNet + TCAI | 7.917 | True |
| Static learnable graph | 8.217 | True |
| Temporal CNN | 8.317 | True |
| Dynamic graph | 8.483 | True |
| + plain task GRL (graph) | 8.983 | True |
| Final model v2 | 9.550 | True |
| + TCAI (graph) | 10.183 | True |
| Full model v1 (seed 0) | 10.350 | True |
| Full model v1 (seed ensemble) | 10.733 | True |

## 4. Cross-session benchmark (N3) and sleepiness (KSS)

| model | subject_bal_acc_mean | ci_low | ci_high | loso_fold_mean_same_model | within_task_rho | cross_session_minus_loso |
|---|---|---|---|---|---|---|
| task name only (no EEG) | 0.771 | 0.721 | 0.817 | 0.771 |  | 0.000 |
| EEGNet | 0.409 | 0.365 | 0.453 | 0.452 | 0.132 | -0.043 |
| EEGNet + plain GRL | 0.409 | 0.366 | 0.451 | 0.459 | 0.136 | -0.050 |
| EEGNet + TCAI | 0.423 | 0.385 | 0.461 | 0.421 | 0.124 | 0.002 |
| Dynamic graph | 0.390 | 0.340 | 0.441 | 0.410 | 0.184 | -0.020 |
| Graph A (+consistency +subject adv) | 0.444 | 0.395 | 0.492 | 0.410 | 0.205 | 0.034 |
| Graph B (+plain GRL) | 0.428 | 0.384 | 0.472 | 0.364 | 0.149 | 0.064 |
| Graph C (+TCAI) | 0.415 | 0.362 | 0.470 | 0.322 | 0.166 | 0.092 |
| Final model v2 | 0.368 | 0.327 | 0.408 | 0.349 | 0.037 | 0.019 |


Per held-out session (mean KSS, mean rating, balanced accuracy):


| session | mean_KSS | mean_rating | recordings | bal_acc task name only (no EEG) | bal_acc EEGNet | bal_acc EEGNet + TCAI | bal_acc Final model v2 |
|---|---|---|---|---|---|---|---|
| ses-01 | 3.490 | 4.400 | 176 | 0.791 | 0.403 | 0.397 | 0.363 |
| ses-02 | 4.340 | 4.290 | 166 | 0.751 | 0.497 | 0.526 | 0.404 |
| ses-03 | 5.110 | 4.450 | 172 | 0.688 | 0.485 | 0.513 | 0.403 |

## 5. N1 — task-conditional adversarial invariance (TCAI)

EEGNet backbone, LOSO (pre-registered rule, Section 22B):


| model | accuracy | balanced_accuracy | macro_f1 | cohen_kappa | fold_bal_acc_mean | fold_bal_acc_sd | one_class_folds | mean_within_task_rho | within_task_rho_CI |
|---|---|---|---|---|---|---|---|---|---|
| A EEGNet | 0.463 | 0.459 | 0.448 | 0.190 | 0.452 | 0.153 | 8 | -0.041 |  |
| B EEGNet + plain GRL | 0.463 | 0.459 | 0.450 | 0.189 | 0.459 | 0.153 | 10 | -0.076 |  |
| C EEGNet + TCAI | 0.446 | 0.443 | 0.428 | 0.165 | 0.421 | 0.165 | 11 | -0.092 | (-0.149, 0.108) |


Cross-session (A = no task adversary, B = plain GRL, C = TCAI):


| backbone | macro_f1_A | macro_f1_B | macro_f1_C | rho_A | rho_B | rho_C | rho_C_minus_B_95CI | C1_macroF1_C>=B | C2_rho_C>=B |
|---|---|---|---|---|---|---|---|---|---|
| EEGNet | 0.460 | 0.463 | 0.476 | 0.132 | 0.136 | 0.124 | (-0.055, 0.042) | True | False |
| graph | 0.475 | 0.468 | 0.457 | 0.205 | 0.149 | 0.166 | (-0.091, 0.122) | False | True |


Planned N1 / ablation comparisons (Holm, family F3/F4):


| family | comparison | delta | ci_low | ci_high | rank_biserial_r | p_raw | p_holm |
|---|---|---|---|---|---|---|---|
| F1 LOSO vs chance | EEGNet + TCAI vs chance | 0.0877 | 0.0308 | 0.1467 | 0.6789 | 0.0094 | 0.0564 |
| F1 LOSO vs chance | + TCAI (graph) vs chance | -0.0110 | -0.0536 | 0.0266 | -0.0588 | 0.8313 | 1.0000 |
| F2 LOSO vs task-only | EEGNet + TCAI vs task-only | -0.3497 | -0.4167 | -0.2761 | -0.9770 | 0.0000 | 0.0000 |
| F2 LOSO vs task-only | + TCAI (graph) vs task-only | -0.4484 | -0.5075 | -0.3894 | -1.0000 | 0.0000 | 0.0000 |
| F3 LOSO planned | N1 EEGNet: TCAI vs plain GRL | -0.0377 | -0.0832 | 0.0028 | -0.4416 | 0.0763 | 0.7627 |
| F3 LOSO planned | N1 EEGNet: TCAI vs no adversary | -0.0307 | -0.0819 | 0.0118 | -0.2982 | 0.2837 | 1.0000 |
| F3 LOSO planned | N1 graph: TCAI vs plain GRL | -0.0413 | -0.0856 | -0.0036 | -0.5263 | 0.0442 | 0.4861 |
| F3 LOSO planned | N1 graph: TCAI vs no task adversary | -0.0872 | -0.1312 | -0.0457 | -0.8667 | 0.0002 | 0.0027 |
| F3 LOSO planned | ablation: - TCAI | 0.0338 | -0.0318 | 0.1003 | 0.2167 | 0.3531 | 1.0000 |
| F4 cross-session | EEGNet + TCAI vs task-only | -0.3479 | -0.4047 | -0.2877 | -0.9954 | 0.0000 | 0.0000 |
| F4 cross-session | Graph C (+TCAI) vs task-only | -0.3562 | -0.4285 | -0.2799 | -0.9699 | 0.0000 | 0.0000 |
| F4 cross-session | N1 EEGNet (cross-session): TCAI vs plain GRL | 0.0136 | -0.0110 | 0.0393 | 0.1884 | 0.4289 | 0.7869 |
| F4 cross-session | N1 graph (cross-session): TCAI vs plain GRL | -0.0135 | -0.0553 | 0.0303 | -0.1806 | 0.3876 | 0.7869 |

## 6. N2 — confound-controlled evaluation protocol

| component | measure | final_model | EEGNet | reference |
|---|---|---|---|---|
| 1 task-only baseline | fold-mean balanced accuracy minus task-only | -0.422 | -0.319 | task-only 0.771 |
| 2 within-task agreement | mean Spearman ρ over 5 eligible tasks | 0.049 | -0.041 | 0 = no tracking |
| 3 within-task permutation | fold-mean bal. acc.: permuted minus true training labels | 0.000 | -0.014 | ≈0 -> task-level shortcut |
| 4 conditional task probe | task within workload class (validation embeddings) | 0.204 |  | chance ≈ 0.23 |
| 5 stimulus rhythm | task decodable from rhythm-only features (bal. acc.) |  |  | 0.190 (chance 0.143) |


Within-task permutation (Section 22):


| model | true_fold_bal_acc | permuted_fold_bal_acc | folds_permuted_lower | folds_permuted_higher | wilcoxon_p | true_macro_f1 | permuted_macro_f1 | true_within_task_rho | permuted_within_task_rho | rho_true_minus_permuted_95CI |
|---|---|---|---|---|---|---|---|---|---|---|
| final | 0.349 | 0.349 | 17 | 12 | 0.387 | 0.319 | 0.362 | 0.049 | 0.020 | (-0.239, 0.239) |
| eegnet | 0.452 | 0.438 | 13 | 11 | 0.989 | 0.448 | 0.426 | -0.041 | 0.013 | (-0.238, 0.128) |


Rhythm-decoder null test and the EEGNet motor/cognitive hypothesis (Section 22C):


| item | value | reference | p_value |
|---|---|---|---|
| rhythm task decoder (pooled bal. acc.) | 0.1900 | null mean 0.141 | 0.0099 |
| EEGNet acc. motor - cognitive (held-out subjects) | 0.2172 | 0 | 0.0132 |
| EEGNet motor-vs-cognitive probe (validation) | 0.5412 | chance 0.5 | 0.0000 |
| hypothesis verdict |  | SUPPORTED |  |


Per-task accuracy on held-out subjects:


| group | task | acc_eegnet | acc_final | acc_task_only | acc_group_only | recordings |
|---|---|---|---|---|---|---|
| cognitive | task-mentalarithmetic | 0.303 | 0.211 | 0.566 | 0.566 | 76 |
| cognitive | task-nback | 0.279 | 0.267 | 0.674 | 0.674 | 86 |
| cognitive | task-nbackarithmetic | 0.507 | 0.356 | 0.740 | 0.247 | 73 |
| cognitive_motor | task-full | 0.494 | 0.364 | 0.896 | 0.896 | 77 |
| motor | task-activemotor | 0.552 | 0.388 | 0.881 | 0.881 | 67 |
| motor | task-motorimagery | 0.482 | 0.410 | 0.639 | 0.639 | 83 |
| motor | task-passivemotor | 0.750 | 0.346 | 0.923 | 0.923 | 52 |

## 7. Ablation and normalisation sensitivity

| variant | fold_bal_acc_mean | macro_f1 | mean_within_task_rho | one_class_folds | validation_bal_acc | delta_vs_final | wilcoxon_p_vs_final |
|---|---|---|---|---|---|---|---|
| FINAL model v2 (all components) | 0.349 | 0.319 | 0.049 | 12 | 0.439 | 0.000 |  |
| − TCAI | 0.382 | 0.353 | 0.005 | 7 | 0.445 | 0.034 | 0.353 |
| − subject adversary | 0.328 | 0.318 | -0.040 | 11 | 0.418 | -0.020 | 0.176 |
| − graph consistency | 0.332 | 0.334 | -0.095 | 8 | 0.425 | -0.016 | 0.917 |


Build-up (one component at a time):


| step | fold_bal_acc_mean | macro_f1 | mean_within_task_rho | validation_bal_acc | delta_vs_previous | wilcoxon_p_vs_previous |
|---|---|---|---|---|---|---|
| Static learnable graph (S16) | 0.405 | 0.409 | -0.037 | 0.447 |  |  |
| Dynamic graph (S17) | 0.410 | 0.352 | -0.086 | 0.451 | 0.005 | 0.903 |
| + graph consistency (S18) | 0.424 | 0.350 | -0.140 | 0.448 | 0.014 | 0.737 |
| + subject adversary (S19) | 0.410 | 0.358 | -0.054 | 0.448 | -0.015 | 0.879 |
| + TCAI (S20 C) | 0.322 | 0.317 | -0.008 | 0.453 | -0.087 | 0.001 |
| + attention pooling = v1 (S21, seed 0) | 0.333 | 0.350 | -0.188 | 0.416 | 0.011 | 0.737 |
| + subject alignment = v2 (S21B) | 0.349 | 0.319 | 0.049 | 0.439 | 0.015 | 0.360 |


Normalisation sensitivity (D-027):


| run | fold_bal_acc_mean | macro_f1 | reference | reference_fold_mean | delta_vs_reference | wilcoxon_p_vs_reference |
|---|---|---|---|---|---|---|
| EEGNet, recording_scaled input | 0.419 | 0.385 | EEGNet, train_global (Section 14) | 0.452 | -0.033 | 0.394 |
| final model, recording_scaled input (no subject alignment) | 0.357 | 0.358 | final model v2, subject_zscore | 0.349 | 0.009 | 0.649 |
|   (same, vs v1 train_global seed 0) | 0.357 | 0.358 | v1 train_global seed 0 | 0.333 | 0.024 | 0.317 |

## 8. Explainability (Section 25)

Artefact shortcut audit (a-priori threshold):


| model | temporal_occlusion_ratio | temporal_ig_ratio | temporal_attention_ratio | frontal_polar_occlusion_ratio | top_band | gamma_drop | EMG_warning | eye_warning | channel_ranking_stability_occlusion | occlusion_vs_ig_spearman |
|---|---|---|---|---|---|---|---|---|---|---|
| EEGNet | 0.698 | 0.865 |  | 0.947 | delta | 0.004 | False | False | 0.021 | 0.278 |
| Final model v2 | 0.890 | 0.905 | 1.028 | 0.774 | beta | 0.010 | False | False | 0.027 | 0.062 |


Region importance:


| model | region | channel_share | occlusion_share | occlusion_ratio | ig_ratio | attention_ratio |
|---|---|---|---|---|---|---|
| EEGNet | frontal_polar_eye | 0.125 | 0.118 | 0.947 | 0.704 |  |
| EEGNet | frontal | 0.094 | 0.133 | 1.417 | 1.032 |  |
| EEGNet | temporal_emg | 0.188 | 0.131 | 0.698 | 0.865 |  |
| EEGNet | central_motor | 0.281 | 0.334 | 1.187 | 1.183 |  |
| EEGNet | parietal_occipital | 0.312 | 0.284 | 0.909 | 1.025 |  |
| Final model v2 | frontal_polar_eye | 0.125 | 0.097 | 0.774 | 0.798 | 0.928 |
| Final model v2 | frontal | 0.094 | 0.110 | 1.178 | 1.224 | 1.077 |
| Final model v2 | temporal_emg | 0.188 | 0.167 | 0.890 | 0.905 | 1.028 |
| Final model v2 | central_motor | 0.281 | 0.300 | 1.068 | 1.150 | 1.095 |
| Final model v2 | parietal_occipital | 0.312 | 0.326 | 1.042 | 0.936 | 0.904 |


Band occlusion:


| model | band | band_hz | drop_mean | drop_sd | folds_positive |
|---|---|---|---|---|---|
| EEGNet | delta | 1-4 | 0.0536 | 0.0301 | 29 |
| EEGNet | theta | 4-8 | 0.0020 | 0.0083 | 20 |
| EEGNet | alpha | 8-13 | 0.0112 | 0.0287 | 19 |
| EEGNet | beta | 13-30 | 0.0064 | 0.0199 | 17 |
| EEGNet | gamma | 30-40 | 0.0044 | 0.0121 | 17 |
| Final model v2 | delta | 1-4 | 0.0099 | 0.0520 | 19 |
| Final model v2 | theta | 4-8 | -0.0059 | 0.0470 | 16 |
| Final model v2 | alpha | 8-13 | 0.0083 | 0.0147 | 23 |
| Final model v2 | beta | 13-30 | 0.0224 | 0.0401 | 26 |
| Final model v2 | gamma | 30-40 | 0.0104 | 0.0177 | 22 |


Deletion (faithfulness) test:


| model | auc_ig | auc_random | folds_ig_faster | wilcoxon_p_ig_faster |
|---|---|---|---|---|
| EEGNet | 0.3683 | 0.4128 | 29 | 0.0000 |
| Final model v2 | 0.3878 | 0.3994 | 22 | 0.0098 |


Learned-graph edges with the largest high-minus-low difference (final model):


| edge | region_pair | high_minus_low | folds_same_sign_high_low | edge_frequency |
|---|---|---|---|---|
| CP1-P3 | central_motor/parietal_occipital | -0.0128 | 0.6667 | 0.8869 |
| Cz-CP1 | central_motor/central_motor | -0.0123 | 0.5667 | 0.8905 |
| FP2-F8 | frontal_polar_eye/frontal_polar_eye | -0.0122 | 0.6333 | 0.9340 |
| Pz-P4 | parietal_occipital/parietal_occipital | -0.0120 | 0.6667 | 0.8961 |
| FP2-F4 | frontal_polar_eye/frontal | -0.0116 | 0.6333 | 0.9362 |
| C4-CP2 | central_motor/central_motor | -0.0116 | 0.6667 | 0.9115 |
| CP2-P4 | central_motor/parietal_occipital | -0.0115 | 0.7333 | 0.8875 |
| P3-Pz | parietal_occipital/parietal_occipital | -0.0112 | 0.7000 | 0.8953 |
| FP1-F7 | frontal_polar_eye/frontal_polar_eye | -0.0107 | 0.5667 | 0.9460 |
| C2-CP2 | central_motor/central_motor | -0.0101 | 0.7000 | 0.9176 |

## 9. Statistics summary

31 of 53 tests are significant after Holm correction (alpha 0.05). Significant tests:


| family | comparison | delta | ci_low | ci_high | rank_biserial_r | p_holm |
|---|---|---|---|---|---|---|
| F1 LOSO vs chance | Temporal CNN vs chance | 0.0740 | 0.0336 | 0.1167 | 0.7154 | 0.0231 |
| F1 LOSO vs chance | EEGNet vs chance | 0.1184 | 0.0674 | 0.1742 | 0.8623 | 0.0035 |
| F1 LOSO vs chance | EEGNet + plain GRL vs chance | 0.1254 | 0.0746 | 0.1815 | 0.9394 | 0.0023 |
| F1 LOSO vs chance | Fixed-graph GCN vs chance | 0.0900 | 0.0491 | 0.1339 | 0.8398 | 0.0075 |
| F1 LOSO vs chance | Static learnable graph vs chance | 0.0716 | 0.0349 | 0.1153 | 0.8615 | 0.0060 |
| F1 LOSO vs chance | Dynamic graph vs chance | 0.0770 | 0.0371 | 0.1219 | 0.8000 | 0.0077 |
| F1 LOSO vs chance | + graph consistency vs chance | 0.0910 | 0.0528 | 0.1337 | 0.9134 | 0.0032 |
| F1 LOSO vs chance | + subject adversary vs chance | 0.0763 | 0.0325 | 0.1172 | 0.8095 | 0.0092 |
| F2 LOSO vs task-only | Temporal CNN vs task-only | -0.3634 | -0.4239 | -0.2995 | -0.9862 | 0.0000 |
| F2 LOSO vs task-only | EEGNet vs task-only | -0.3190 | -0.3861 | -0.2455 | -0.9724 | 0.0000 |
| F2 LOSO vs task-only | EEGNet + plain GRL vs task-only | -0.3120 | -0.3761 | -0.2460 | -0.9754 | 0.0000 |
| F2 LOSO vs task-only | EEGNet + TCAI vs task-only | -0.3497 | -0.4167 | -0.2761 | -0.9770 | 0.0000 |
| F2 LOSO vs task-only | Fixed-graph GCN vs task-only | -0.3474 | -0.4036 | -0.2886 | -0.9954 | 0.0000 |
| F2 LOSO vs task-only | Static learnable graph vs task-only | -0.3658 | -0.4224 | -0.3042 | -1.0000 | 0.0000 |
| F2 LOSO vs task-only | Dynamic graph vs task-only | -0.3604 | -0.4300 | -0.2858 | -0.9862 | 0.0000 |
| F2 LOSO vs task-only | + graph consistency vs task-only | -0.3464 | -0.4084 | -0.2842 | -1.0000 | 0.0000 |
| F2 LOSO vs task-only | + subject adversary vs task-only | -0.3611 | -0.4207 | -0.3000 | -0.9914 | 0.0000 |
| F2 LOSO vs task-only | + plain task GRL (graph) vs task-only | -0.4070 | -0.4705 | -0.3425 | -0.9914 | 0.0000 |
| F2 LOSO vs task-only | + TCAI (graph) vs task-only | -0.4484 | -0.5075 | -0.3894 | -1.0000 | 0.0000 |
| F2 LOSO vs task-only | Full model v1 (seed 0) vs task-only | -0.4374 | -0.5007 | -0.3737 | -1.0000 | 0.0000 |
| F2 LOSO vs task-only | Full model v1 (seed ensemble) vs task-only | -0.4465 | -0.5059 | -0.3821 | -1.0000 | 0.0000 |
| F2 LOSO vs task-only | Final model v2 vs task-only | -0.4222 | -0.4915 | -0.3553 | -1.0000 | 0.0000 |
| F3 LOSO planned | N1 graph: TCAI vs no task adversary | -0.0872 | -0.1312 | -0.0457 | -0.8667 | 0.0027 |
| F4 cross-session | EEGNet vs task-only | -0.3617 | -0.4184 | -0.3024 | -0.9957 | 0.0000 |
| F4 cross-session | EEGNet + plain GRL vs task-only | -0.3615 | -0.4181 | -0.3038 | -0.9957 | 0.0000 |
| F4 cross-session | EEGNet + TCAI vs task-only | -0.3479 | -0.4047 | -0.2877 | -0.9954 | 0.0000 |
| F4 cross-session | Dynamic graph vs task-only | -0.3803 | -0.4467 | -0.3148 | -0.9914 | 0.0000 |
| F4 cross-session | Graph A (+consistency +subject adv) vs task-only | -0.3270 | -0.3879 | -0.2650 | -0.9871 | 0.0000 |
| F4 cross-session | Graph B (+plain GRL) vs task-only | -0.3426 | -0.4089 | -0.2710 | -0.9742 | 0.0000 |
| F4 cross-session | Graph C (+TCAI) vs task-only | -0.3562 | -0.4285 | -0.2799 | -0.9699 | 0.0000 |
| F4 cross-session | Final model v2 vs task-only | -0.4031 | -0.4658 | -0.3353 | -0.9871 | 0.0000 |

## 10. Limitations

- One dataset (CMx7-MM); external validation on COG-BCI is planned after this notebook.
- Workload labels come from subjective ratings split into training-fold tertiles; ratings are partly fixed by the task.
- Most models were trained with one seed (seed 0); the seed-to-seed SD of the full model (Section 21) is the noise reference.
- The within-task permutation and the ablations use one permutation / one seed because of the compute budget.
- Four validation subjects per fold make hyper-parameter selection noisy.
- Explanations describe seed-0 models on held-out subjects; they are descriptive and were not used for any decision.

## 11. Reproducibility

- Exact configuration: `configs/config_final.json`; file hashes, package versions and decision IDs: `reports/final_manifest.json`.
- Notebook state: completed sections [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28].
- Figures (36): `sec10_folds_and_task_only.png`, `sec11_e013_signal_diagnosis.png`, `sec13_tcnn_vs_task_only.png`, `sec14_eegnet_vs_tcnn_vs_task_only.png`, `sec15_fixed_graph.png`, `sec15_gcn_vs_baselines.png`, `sec16_learned_static_graph.png`, `sec17_dynamic_graph_analysis.png`, `sec18_graph_consistency.png`, `sec19_subject_adversarial_probes.png`, `sec20_tcai_vs_plain.png`, `sec21_full_model.png`, `sec21b_model_v2.png`, `sec22_benchmark_and_n2.png`, `sec22b_tcai_eegnet.png`, `sec22c_n2_extras.png`, `sec23_cross_session.png`, `sec24_ablation.png`, `sec25_learned_graphs.png`, `sec25_xai_overview.png`, `sec26_statistics.png`, `sec4_sub-001_ses-01_task-nback_channel_std.png`, `sec4_sub-001_ses-01_task-nback_psd.png`, `sec4_sub-001_ses-01_task-nback_raw_segment.png`, `sec5_label_strategies_by_task.png`, `sec5_rating_distribution.png`, `sec5_rating_heatmap.png`, `sec6_sub-001_ses-01_task-nback_before_after_psd.png`, `sec6_sub-001_ses-01_task-nback_before_after_segment.png`, `sec6_sub-001_ses-01_task-nback_stimulus_rhythm.png`, `sec7_sub-001_ses-01_task-nback_raw_minimal_ica.png`, `sec7_sub-001_ses-01_task-nback_removed_components.png`, `sec7_sub-001_ses-01_task-nback_variance_removed.png`, `sec8_example_window.png`, `sec8_stimulus_locked_by_task.png`, `sec9_subject_amplitude.png`
