# XAI pre-registration — CMx7-SI-DyGraph

**Written:** 13 Oct 2026, before any XAI computation on the models named below. The Git commit time of this file is the pre-registration timestamp.
**Machine-readable copy:** `xai_prereg.json` (same folder). If the two differ, the JSON is binding.

## 0. Honest status
- **Already known:** the models are trained and their test accuracy is known (FINAL and DEV_v4 runs).
- **Not yet known:** none of the attribution analyses below has been computed for the models in §1.
- **Earlier XAI run:** the development notebook (Section 25) ran XAI on EEGNet and Final model v2 (CMx7-MM). Those results are prior information and are not re-used as evidence here.
- **Reporting rule:** every hypothesis is reported, whatever the outcome.

## 1. Models
| Role | Key | Definition | Weights |
|---|---|---|---|
| **M_prop** (proposed) | `d_v3_ls` | v4 locked in `cx7mm/final/dev/v4_lock.json`: EEGNet backbone with Euclidean alignment (EA), IG-TCAI, within-task ranking loss (λ_rank = 0.5), label smoothing 0.1, SWA, and AdaBN on the test subject | `cx7mm/final/dev/{cmx7,cog}/d_v3_ls/loso_*/swa_model.pt` |
| **M_ref** (same pipeline, without our components) | `d_tricks` | EEGNet + EA + AdaBN, SWA; same training protocol as M_prop | `cx7mm/final/dev/{cmx7,cog}/d_tricks/loso_*/swa_model.pt` |
| **M_base** (standard baseline) | `eegnet_s0` | EEGNet, train_global normalisation, early stopping (FINAL run) | `cx7mm/final/{cmx7,cogbci}/checkpoints/eegnet_s0/loso_*/best.pt` (LOSO folds only; sweep folds `L*__loso_*` are not used) |
| Descriptive only | `final_model_s0` / development v2 | Graph model v2 (attention weights and learned graphs) | COG-BCI: `cx7mm/final/cogbci/checkpoints/final_model_s0`; CMx7-MM: development checkpoints on Drive |

- **Seeds:** seed 0 only.
- **Amendment rule:** if the final proposed model is changed before XAI is run (plan step P2), a dated amendment naming the new M_prop is committed **before** any XAI computation. The hypotheses stay unchanged.

## 2. Data and attribution settings (fixed)
- **Test subjects:** each fold's held-out test subject, explained by that fold's model only. CMx7-MM: 30 folds; COG-BCI: 29 folds.
- **Windows:** 6 evenly spaced valid windows per test recording (as in the development notebook). An explanation map per recording is the mean over its windows.
- **Target:** the logit (Integrated Gradients) or probability (occlusion) of the recording's **true** workload class. The predicted class is not used, so that prediction errors do not change the target.
- **Alignment inside the explanation:** EA and AdaBN models are explained exactly as they are tested.
  - AdaBN statistics are re-estimated on the test subject's windows first.
  - Attributions are computed with respect to the input **before** the EA transform (the transform R^-1/2 is part of the differentiable graph). Channel attributions therefore refer to real electrodes.
- **Integrated Gradients (IG):** 16 steps; zero baseline in the normalised input space (= the training mean). Channel map = sum over time of |IG|, L1-normalised to sum 1.
- **Occlusion:**
  - Channel occlusion sets one channel to 0.
  - Region occlusion sets all channels of one region to 0.
  - Band occlusion removes one band from every channel (FFT zeroing). Bands: δ 1–4, θ 4–8, α 8–13, β 13–30, γ 30–40 Hz.
  - Region × band occlusion removes one band in one region only.
  - Effect = drop in true-class probability.
  - Share = |effect| / Σ |effects| within the same set (regions or bands).
- **Regions:** copied from `config_final.json` of the development notebook (32-channel CMx7 montage, also used for COG-BCI):
  - frontal_polar_eye: FP1, FP2, F7, F8
  - frontal: F3, Fz, F4
  - temporal_emg: FT7, FT8, T7, T8, TP7, TP8
  - central_motor: FC3, FC4, C1, Cz, C2, C3, C4, CP1, CP2
  - parietal_occipital: P7, P3, Pz, P4, P8, PO7, PO3, PO4, PO8, Oz
- **Unit of analysis:** the held-out subject (per-subject mean of the recording-level values).

## 3. Hypotheses

### H-X0 Sanity (gate; tested for every model on both datasets)
1. **H-X0a Deletion test.** Channels are removed in IG order and in random order (mean of 10 random orders), at 0, 4, 8, 16 and 24 removed channels. The area under the true-class-probability curve is smaller for IG order. One-sided Wilcoxon over subjects, p < 0.05.
2. **H-X0b Model randomisation (Adebayo et al., 2018).** The median Spearman correlation between the IG channel maps of the trained model and the same architecture with re-initialised weights is < 0.5.

If H-X0 fails for a model on a dataset, no H-X1–H-X4 claim involving that model on that dataset is made. Those tests are reported as "not evaluable".

### Primary hypotheses (one family, Holm correction, α = 0.05; all tests one-sided Wilcoxon signed-rank over held-out subjects)
| ID | Dataset | Claim | Metric (per subject) | Test |
|---|---|---|---|---|
| **H-X1** | COG-BCI | Explanations of M_prop carry less task identity given the workload level than those of M_ref | Task-within-level decodability of the IG channel maps. Logistic regression (standardised features, C = 1.0) trained on the maps of the other subjects of the same model, predicting task (N-back vs MATB) separately within each workload level; per-subject balanced accuracy, averaged over the 3 levels | M_prop < M_ref |
| **H-X2a** | CMx7-MM | M_prop relies less on the temporal (EMG-prone) region than the standard baseline | temporal_emg share of region occlusion | M_prop < M_base |
| **H-X2b** | CMx7-MM | M_prop relies less on the γ band than the standard baseline | γ share of band occlusion | M_prop < M_base |
| **H-X3-cmx** | CMx7-MM | M_prop relies more on established workload markers (frontal θ, parietal α) | (frontal-θ effect + parietal_occipital-α effect) / Σ \|effects\| over all 25 region × band cells | M_prop > M_base |
| **H-X3-cog** | COG-BCI | same as H-X3-cmx | same | M_prop > M_base |
| **H-X4-cmx** | CMx7-MM | Explanations of M_prop are more consistent across people | Spearman correlation between a subject's mean IG channel map and the mean map of all other subjects | M_prop > M_ref |
| **H-X4-cog** | COG-BCI | same as H-X4-cmx | same | M_prop > M_ref |

**Why different references.**
- H-X1 and H-X4 test our own components (IG-TCAI, ranking loss, label smoothing). M_ref has exactly the same alignment and training protocol, so the difference isolates those components.
- H-X2 and H-X3 test the full proposed pipeline against the standard baseline. Development results showed that this baseline (EEGNet) uses a task-level shortcut (motor vs cognitive).
- Every other pair (M_prop vs M_base for H-X1/H-X4, M_prop vs M_ref for H-X2/H-X3) is reported as secondary, without a claim.

**Workload-marker rationale (H-X3).** Workload studies report increased frontal theta and reduced parietal alpha with higher load (Borghini et al., 2014; Kakkos et al., 2021). The hypothesis concerns the *share of reliance*, not the direction of the effect.

## 4. Secondary analyses (reported, no claim)
- H-X1 on CMx7-MM: task-within-class decodability over the 7 tasks; chance level by a label-permutation null with 100 permutations.
- IG maps vs channel occlusion maps: Spearman agreement per model.
- Region shares separately for motor and cognitive task groups (CMx7-MM).
- Graph model v2: attention weights and the mean learned graph per workload class and task group.
- Effect sizes: rank-biserial r and the bootstrap 95 % CI (2,000 resamples over subjects) for every test.

## 5. Verdict
- **SUPPORTED:** the hypothesis passes Holm-corrected p < 0.05 **and** its H-X0 gates pass.
- **NOT SUPPORTED:** H-X0 passes but the test does not.
- **NOT EVALUABLE:** H-X0 fails.
- **The XAI novelty claim** ("the proposed model's explanations are less task-specific and less shortcut-driven") is made **only if H-X1 is SUPPORTED**. H-X2–H-X4 add to it; they cannot replace it.

## 6. What is not allowed
- Changing regions, bands, windows, the target, IG steps, the classifier in H-X1, or the references after seeing any XAI output.
- Dropping a hypothesis or a model from the report.
- Running more seeds or methods and reporting only the favourable ones.
