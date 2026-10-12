# Paper figures -- captions (generated from the saved result files)

Files: `/content/drive/MyDrive/CMx7_SI_DyGraph/figures/paper` (PDF = vector, for LaTeX; PNG = 300 dpi, for Word / slides).

## Figure 1: `fig01_label_structure`

Workload-label composition of each CMx7-MM task (n = 514 recordings; each recording carries the label of the LOSO fold in which it is the test recording, i.e. the tertile of the training subjects' ratings). The share of high-workload recordings ranges from 0% (Active motor) to 90% (Full (cognitive + motor)), so the task name alone predicts much of the label: a lookup that uses no EEG reaches a balanced accuracy of 0.771.

## Figure 2: `fig02_loso_benchmark`

Leave-one-subject-out benchmark (30 held-out subjects, recording-level balanced accuracy; mean and 95 % bootstrap CI over subjects, faint dots = individual subjects). Best EEG model: EEGNet + plain GRL (0.459 [0.407, 0.515]); EEGNet 0.452; final model v2 0.349. The CI of 12 of 12 EEG models lies below the task-only lookup (0.771, dashed); dotted line = chance (1/3).

## Figure 3: `fig03_task_shortcut`

Evidence that the EEG models learn the task rather than workload. (a) Balanced accuracy of EEGNet vs the no-EEG task-only lookup for every held-out subject: EEGNet is above the lookup in 3 of 30 subjects. (b) Accuracy per task on held-out subjects. EEGNet is more accurate on motor (0.574) than on cognitive tasks (0.357). (c) Retraining with the ratings shuffled inside each task (training and validation subjects only; test labels unchanged) does not lower the fold-mean balanced accuracy: EEGNet 0.452 -> 0.438 (Wilcoxon p = 0.99); final model v2 0.349 -> 0.349 (Wilcoxon p = 0.39).

## Figure 4: `fig04_n1_tcai`

Task-conditional adversarial invariance (TCAI, N1) against a plain task gradient-reversal adversary and no task adversary, on identical folds. (a) LOSO: EEGNet backbone A/B/C = 0.452/0.459/0.421, graph backbone 0.410/0.364/0.322. (b) Cross-session (per-subject balanced accuracy). (c) Task information left inside a workload class in the EEGNet embedding (linear probe on validation subjects; A/B/C = 0.218/0.219/0.217, chance 0.23); even without a task adversary this is at chance level, so there is little task information for TCAI to remove. Pre-registered N1 verdict on the EEGNet backbone: NOT SUPPORTED. Error bars: 95 % bootstrap CI.

## Figure 5: `fig05_cross_session`

Cross-session evaluation (the same people, one session held out). (a) Balanced accuracy on each held-out session. Task-only lookup (no EEG): 0.791, 0.751, 0.688; EEGNet: 0.403, 0.497, 0.485; Graph A (+cons. +subj. adv.): 0.504, 0.501, 0.503; Final model v2: 0.363, 0.404, 0.403. (b) Mean sleepiness (Karolinska Sleepiness Scale) per held-out session (3.49 -> 4.34 -> 5.11). The least sleepy session (session 1) is the hardest session for 2 of 3 EEG models.

## Figure 6: `fig06_ablation`

Ablation of the graph model on the LOSO folds (seed 0). (a) Build-up: each step adds one component; Δ = change vs the previous step. Significant steps (Wilcoxon p < 0.05): + TCAI (S20 C) Δ -0.087. (b) Leave-one-out from the final model; the grey band is ±1 seed-to-seed SD of the full model (0.012), i.e. training noise.

## Figure 7: `fig07_xai_regions_bands`

What the models use, on the held-out test subjects. (a) Occlusion importance of five a-priori scalp regions divided by the region's share of the channels (1 = proportional to its size); the fronto-polar (eye) and temporal (EMG) regions stay below 1 for both models (largest 0.95), so neither model relies more than proportionally on these artefact-prone sites. (b) Drop in the predicted-class probability when one frequency band is removed from every channel (mean ± SD over the folds).

## Figure 8: `fig08_scalp_maps`

Channel occlusion importance on the held-out test subjects, as a share of the total (common colour scale). Largest share: EEGNet Oz, Final model v2 T7.

## Figure 9: `fig09_learned_graph`

Epoch-specific graphs of the final model on the held-out test subjects (30 folds). (a) The 25 edges selected most often (line width = selection frequency; most frequent: FP1-F7, FP1-F3, FT7-FC3). (b) The 25 largest differences in mean edge weight between high- and low-workload windows; the largest |Δ| is 0.0128, so the graphs barely change with workload (descriptive, no test).

## Figure 10: `fig10_planned_comparisons`

Planned comparisons on the LOSO folds (family F3 LOSO planned, 13 tests, Holm correction): mean difference in balanced accuracy over the 30 held-out subjects with a 95 % bootstrap CI. 1 of 13 comparisons are significant after correction (filled markers).
