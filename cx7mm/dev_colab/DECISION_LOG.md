<!-- CMx7-SI-DyGraph log v1 -->
# DECISION_LOG — CMx7-SI-DyGraph

<!-- BEGIN D-001 -->
## D-001
**Decision ID:** D-001
**Date:** 2026-10-12
**Phase:** Phase 1
**Decision:** Use the roadmap's numeric section numbering (0-27); letter names A/B/B2 are retired.
**Reason:** The thesis roadmap and the Project instructions both use numeric sections; one scheme avoids confusion.
**Alternatives considered:**
  - Keep letters A/B/B2
  - Show both names side by side
**Evidence:** Roadmap §10 master tracker maps Phase 1 -> Sections 0-1, Phase 2 -> Sections 2-3.
**Expected effect:** notebook_state.json, PROJECT_STATE.md and the roadmap tracker all use the same IDs.
**Risk:** Old notebook_state.json uses letters; Section 1.4 keeps them as legacy_completed_sections (reference only), so Sections 1-3 are re-run once.
**Reversible:** Yes
<!-- END D-001 -->

<!-- BEGIN D-002 -->
## D-002
**Decision ID:** D-002
**Date:** 2026-10-12
**Phase:** Phase 1
**Decision:** Project outputs live in MyDrive/CMx7_SI_DyGraph (the user's own Drive), not in the shared 'All Thesis data' folder.
**Reason:** Roadmap §10.2 places CMx7_SI_DyGraph in MyDrive; the shared folder is owned by another account, so its storage and access are not under the user's control.
**Alternatives considered:**
  - Write outputs into the shared 'All Thesis data' folder
**Evidence:** Drive metadata: 'All Thesis data' and 'CMx7-MM_dataset' are owned by another account; 'CMx7_SI_DyGraph' is owned by the user.
**Expected effect:** Outputs stay available even if sharing settings change.
**Risk:** Collaborators do not see outputs unless the project folder is shared with them.
**Reversible:** Yes
<!-- END D-002 -->

<!-- BEGIN D-003 -->
## D-003
**Decision ID:** D-003
**Date:** 2026-10-12
**Phase:** Phase 1
**Decision:** use_demo_data = False for metadata-only audits (Sections 2-3); a demo subset is required before batch preprocessing.
**Reason:** Sections 2-3 read only filenames and small sidecar files, so running them on the full dataset is cheap and loads no EEG signal. The roadmap rule 'demo pipeline first' applies to signal processing.
**Alternatives considered:**
  - Build CMx7_MM_Demo first and audit only that
**Evidence:** No CMx7_MM_Demo folder exists yet; the full dataset is reachable through the Drive shortcut.
**Expected effect:** Complete inventory (all 30 subjects) before any signal work.
**Risk:** Must not forget the demo-first rule at Section 6 -- tracked as an open problem in PROJECT_STATE.
**Reversible:** Yes
<!-- END D-003 -->

<!-- BEGIN D-004 -->
## D-004
**Decision ID:** D-004
**Date:** 2026-10-12
**Phase:** Phase 1
**Decision:** force_rescan = False: reuse the cached BIDS scan after a disconnect.
**Reason:** Walking the Drive tree is the slowest step after a restart; the cache is invalidated automatically when BIDS_ROOT or the scan version changes.
**Alternatives considered:**
  - Always rescan
**Evidence:** Earlier runs had force_rescan=True only to detect the newly added dataset shortcut.
**Expected effect:** Faster resume after Colab disconnects.
**Risk:** A changed dataset copy would need force_rescan=True once.
**Reversible:** Yes
<!-- END D-004 -->

<!-- BEGIN D-005 -->
## D-005
**Decision ID:** D-005
**Date:** 2026-10-12
**Phase:** Phase 2
**Decision:** Treat a recording as 250 Hz when |SamplingFrequency - 250| < 0.01 Hz.
**Reason:** eeg.json values are measured effective rates; the largest deviation is 0.003102 Hz (12.4 ppm), i.e. under 2.68 ms drift over a 216 s recording.
**Alternatives considered:**
  - Exact equality (flags every recording)
  - Resample every recording to exactly 250 Hz
**Evidence:** Section 3.8/3.10 sampling-rate summary; Section 4 compares with the rate MNE reads from the EDF header.
**Expected effect:** No spurious FLAG; 4 s windows stay exactly 1000 samples.
**Risk:** If the EDF header itself is non-integer, MNE timing must be checked again in Section 4.
**Reversible:** Yes
<!-- END D-005 -->

<!-- BEGIN D-006 -->
## D-006
**Decision ID:** D-006
**Date:** 2026-10-12
**Phase:** Phase 3
**Decision:** Single-recording signal audit uses sub-001/ses-01/task-nback.
**Reason:** A cognitive task without movement gives the cleanest view of baseline signal quality.
**Alternatives considered:**
  - A motor task (movement artifacts would dominate)
  - A random recording
**Evidence:** Section 4 output for sub-001_ses-01_task-nback.
**Expected effect:** Filtering/notch/bad-channel rules for Section 6 rest on real signal evidence.
**Risk:** One recording may not be representative; Section 6 computes the same QC for every recording.
**Reversible:** Yes
<!-- END D-006 -->

<!-- BEGIN D-007 -->
## D-007
**Decision ID:** D-007
**Date:** 2026-10-12
**Phase:** Phase 3
**Decision:** PROPOSED: keep apply_notch=False for now; decide in Section 6 by measuring residual 50 Hz power after the 1-40 Hz filter.
**Reason:** The 40 Hz low-pass already attenuates 50 Hz; a notch is only justified if residual line noise remains.
**Alternatives considered:**
  - Always apply a 50 Hz notch
  - Never apply a notch
**Evidence:** 50 Hz peak above neighbours: median 2.236624348388742 dB, max 4.314058414418433 dB (threshold 10.0 dB) in sub-001_ses-01_task-nback.
**Expected effect:** Avoids an unnecessary filter step; keeps the pipeline minimal.
**Risk:** If residual 50 Hz remains after filtering, the decision changes (logged then).
**Reversible:** Yes
<!-- END D-007 -->

<!-- BEGIN D-008 -->
## D-008
**Decision ID:** D-008
**Date:** 2026-10-12
**Phase:** Phase 3
**Decision:** Keep each recording's native EDF sampling rate (no resampling). Windows are defined in samples (1000 samples per window); event onsets in seconds are converted to samples with the recording's own sfreq.
**Reason:** MNE reads 250.00100000400002 Hz from the EDF header (4.0 ppm above nominal); resampling such a small offset adds a filter step for no benefit.
**Alternatives considered:**
  - Resample every recording to exactly 250 Hz
  - Overwrite info['sfreq'] with 250
**Evidence:** Section 4.3 EDF header vs eeg.json; D-005 tolerance.
**Expected effect:** Every window has exactly the same number of samples; timing error stays below 1 ms per recording.
**Risk:** Onset-to-sample conversion must always use the recording's own sfreq, never 250.
**Reversible:** Yes
<!-- END D-008 -->

<!-- BEGIN D-009 -->
## D-009
**Decision ID:** D-009
**Date:** 2026-10-12
**Phase:** Phase 3
**Decision:** High variance at FP1/FP2 is treated as ocular (eye blinks), not as bad electrodes. Channels flagged by variance alone are never interpolated; Section 6 bad-channel detection combines flat, correlation and high-frequency noise indicators. Ocular artifacts are handled by ICA in Section 7 using FP1/FP2 as the EOG reference.
**Reason:** Raw plot (4.5) shows blink-shaped frontal deflections; FP1/FP2 robust z = [7.61, 7.47] but median |corr| = [0.529, 0.61] (well-connected channels). No EOG channel exists: physio recordings are ['ECG', 'EMG', 'biodex', 'pushbutton'].
**Alternatives considered:**
  - Interpolate FP1/FP2
  - Drop frontal channels from the graph
**Evidence:** Section 4.5 figure, 4.7 channel QC table, 3.6 physio inventory.
**Expected effect:** Frontal EEG is kept; blinks are removed at the component level instead of deleting channels.
**Risk:** Some recordings may contain genuinely bad frontal electrodes; the Section 6 multi-indicator check must catch those.
**Reversible:** Yes
<!-- END D-009 -->

<!-- BEGIN D-010 -->
## D-010
**Decision ID:** D-010
**Date:** 2026-10-12
**Phase:** Phase 3
**Decision:** Accept D-007: apply_notch stays False.
**Reason:** 50 Hz peak is only 2.2 dB (median) / 4.3 dB (max) above neighbouring frequencies, below the 10.0 dB threshold; the 40 Hz low-pass attenuates 50 Hz further.
**Alternatives considered:**
  - Always apply a 50 Hz notch
**Evidence:** Section 4.6 line-noise numbers.
**Expected effect:** Minimal pipeline; no unnecessary filter.
**Risk:** Re-checked on every recording in Section 6.
**Reversible:** Yes
<!-- END D-010 -->

<!-- BEGIN D-011 -->
## D-011
**Decision ID:** D-011
**Date:** 2026-10-12
**Phase:** Phase 3
**Decision:** Windows are taken only from the task period: from the 'start' event + 3.0 s to 'start' + 180.0 s. Pre-task and post-task rest is excluded. Recordings without a 'start' event (motor imagery in 3.8) get an anchor rule decided in Section 8.
**Reason:** README: each task lasts 3 min with 30 s rest between tasks. Real events: start at [25.0] s, last event at 204.5 s in a 216.0 s recording.
**Alternatives considered:**
  - Use the whole recording
  - Use first-to-last event
**Evidence:** Section 4.4 events table; dataset README.
**Expected effect:** Rest periods do not get the task's workload label.
**Risk:** Anchor for tasks without a 'start' event still to be decided (Section 8).
**Reversible:** Yes
<!-- END D-011 -->

<!-- BEGIN D-012 -->
## D-012
**Decision ID:** D-012
**Date:** 2026-10-12
**Phase:** Phase 4
**Decision:** Workload labels are recording-level: every window of a recording inherits that recording's rating. KSS (sleepiness) is kept only as a covariate for analysis, never as a model input or label.
**Reason:** The dataset has exactly one rating per subject x session x task, given after the task (README + json).
**Alternatives considered:**
  - Window-level labels (no data for them)
  - Use KSS as a second target
**Evidence:** Section 5.3-5.4: rating table layout and join.
**Expected effect:** Label granularity matches what the data can support.
**Risk:** Within-recording workload changes cannot be labelled; reported as a limitation.
**Reversible:** Yes
<!-- END D-012 -->

<!-- BEGIN D-013 -->
## D-013
**Decision ID:** D-013
**Date:** 2026-10-12
**Phase:** Phase 4
**Decision:** Primary workload label: 3 classes from training-fold tertile thresholds (recomputed in every LOSO fold). Real thresholds in every fold: q33 = [2.0], q67 = [6.0] -> low = rating <= q33, high = rating > q67, else medium. Sensitivity label: fixed bins 1-3/4-6/7-9. Mandatory controls: (1) task-only baseline, (2) within-task evaluation, (3) no-movement subset (mentalarithmetic, nback, nbackarithmetic), (4) task probe on embeddings.
**Reason:** Task explains 76.5% of rating variance, subject 6.6%; every candidate label has Cramér's V(task) >= 0.67. S3 has the best balance (smallest class 30.9%, imbalance 1.17) and is fold-safe.
**Alternatives considered:**
  - S1 fixed bins (imbalance 2.03)
  - S2 binary (V = 0.81)
  - S4 within-subject split (forbidden by roadmap §6)
  - Task names as labels (forbidden by roadmap §6)
**Evidence:** Section 5.8 variance table, 5.9 strategy table; within-task rating std: {'task-activemotor': 0.84, 'task-passivemotor': 0.69, 'task-motorimagery': 1.19, 'task-mentalarithmetic': 2.05, 'task-nback': 1.5, 'task-nbackarithmetic': 1.42, 'task-full': 1.12}.
**Expected effect:** Balanced classes without test-subject thresholds; the controls make the 'workload beyond task' claim testable.
**Risk:** Because label ≈ task, high accuracy alone cannot prove workload decoding -- only the controls can.
**Reversible:** Yes
<!-- END D-013 -->

<!-- BEGIN D-014 -->
## D-014
**Decision ID:** D-014
**Date:** 2026-10-12
**Phase:** Phase 4
**Decision:** The 'Full' rating columns are treated as the rating of task-full (not a composite).
**Reason:** Full equals the mean of the other tasks in 0% of sessions and is the highest rating in 87.5%; the README says a rating is given after each task.
**Alternatives considered:**
  - Drop task-full recordings
**Evidence:** Section 5.5.
**Expected effect:** task-full keeps its 77 labelled recordings.
**Risk:** The json description says 'composite'; reported as a dataset documentation inconsistency.
**Reversible:** Yes
<!-- END D-014 -->

<!-- BEGIN D-015 -->
## D-015
**Decision ID:** D-015
**Date:** 2026-10-12
**Phase:** Phase 4
**Decision:** Novelty N3 (task invariance) is evaluated as a controlled trade-off, not assumed: the task-adversarial branch is an ablation, and the main claim is 'workload beyond task identity' (controls 1-3 of D-013).
**Reason:** Task explains 76.5% of the rating, so full task invariance would remove most of the label signal (roadmap §12.2 anticipates this case).
**Alternatives considered:**
  - Keep strong task-invariance claim
**Evidence:** Section 5.8.
**Expected effect:** Honest, testable claim.
**Risk:** Thesis framing of N3 changes; discuss with supervisor.
**Reversible:** Yes
<!-- END D-015 -->

<!-- BEGIN D-016 -->
## D-016
**Decision ID:** D-016
**Date:** 2026-10-12
**Phase:** Phase 5
**Decision:** Minimal pipeline order: load 32 EEG (reference order) -> 1-40 Hz zero-phase FIR -> notch only if CONFIG -> multi-indicator bad channels -> interpolate if <= max_interpolated_channels -> average reference -> BAD_severe/BAD_flat annotations. Blinks are not annotated (ICA, Section 7).
**Reason:** Roadmap §7; filtering before bad-channel detection removes drift that would fake high variance; interpolation before the average reference keeps bad channels out of the reference.
**Alternatives considered:**
  - Reference before bad-channel detection
  - Annotate blinks as BAD
**Evidence:** Section 6 run on sub-001_ses-01_task-nback: status ok, bad [], segment ptp percentiles {50: 67.2, 90: 273.6, 95: 285.6, 99: 418.8, 100: 12541.9}.
**Expected effect:** Same code runs on every recording in Section 8.
**Risk:** Thresholds may need tuning after the all-recording QC.
**Reversible:** Yes
<!-- END D-016 -->

<!-- BEGIN D-017 -->
## D-017
**Decision ID:** D-017
**Date:** 2026-10-12
**Phase:** Phase 5
**Decision:** Saved derivatives are float32 FIF (6.9 MB for this recording).
**Reason:** float32 halves storage versus float64 with no meaningful precision loss for EEG in µV.
**Alternatives considered:**
  - float64
  - float16
**Evidence:** Section 6.10 file size.
**Expected effect:** Smaller derivatives (relevant to E-007).
**Risk:** Final storage format is still decided in Section 9.
**Reversible:** Yes
<!-- END D-017 -->

<!-- BEGIN D-018 -->
## D-018
**Decision ID:** D-018
**Date:** 2026-10-12
**Phase:** Phase 5
**Decision:** ICA sensitivity pipeline: infomax (extended=True), n_components = 31 - interpolated channels, fixed seed, fitted per recording on the minimal output (BAD_ segments skipped). Eye components via FP1/FP2 correlation; heart components via CTPS on the Delsys ECG aligned by StartTime and verified by lag search. The minimal pipeline stays primary.
**Reason:** Project instructions: fit ICA reproducibly, use ECG/EOG/EMG only for artifact detection, do not make ICA primary until validated.
**Alternatives considered:**
  - ICLabel automatic classification (needs extra package, trained on other montages)
  - No ICA at all
**Evidence:** Section 7 on sub-001_ses-01_task-nback: removed [1, 2], ECG {'available': True, 'file': 'sub-001/ses-01/beh/sub-001_ses-01_task-nback_recording-ECG_physio.tsv.gz', 'sfreq_ecg': 1882.453362622982, 'start_time_s': 0.0, 'ecg_duration_s': 215.0, 'eeg_duration_s': 216.0, 'average_pulse_bpm': 72.9, 'n_r_peaks': 260, 'best_component': 0, 'best_component_ctps': 0.235, 'alignment_lag_s': 0.476, 'alignment_corr': 0.052}.
**Expected effect:** A matched ICA-cleaned dataset for the sensitivity analysis.
**Risk:** Component selection thresholds may need review across many recordings.
**Reversible:** Yes
<!-- END D-018 -->

<!-- BEGIN D-019 -->
## D-019
**Decision ID:** D-019
**Date:** 2026-10-12
**Phase:** Phase 5
**Decision:** Adopt the three verified novelties: N1 Task-Conditional Adversarial Invariance (task adversary conditioned on the training rating), N2 Confound-Controlled Evaluation Protocol (task-only baseline, within-task rank agreement on pre-registered tasks, within-task permutation, conditional task probe, stimulus-locked shortcut test), N3 first leakage-audited LOSO + cross-session benchmark on CMx7-MM. Dynamic graph and subject-adversarial training are adopted components, not novelties.
**Reason:** Original N1/N2 overlap with ProtoGIB-Workload (arXiv 2608.10647) and CDBG (arXiv 2609.30831); task explains 76.5 % of the rating (Section 5).
**Alternatives considered:**
  - Keep the original roadmap novelties
**Evidence:** CMx7_SI_DyGraph_Three_Novelties_Literature_Review.docx (verified 2 Oct 2026).
**Expected effect:** Defensible, scoped claims; the evaluation directly answers the label-task confound.
**Risk:** New preprints may appear; repeat the search before submission.
**Reversible:** Yes
<!-- END D-019 -->

<!-- BEGIN D-020 -->
## D-020
**Decision ID:** D-020
**Date:** 2026-10-12
**Phase:** Phase 5
**Decision:** ICA sensitivity pipeline removes eye components only (CONFIG['ica_use_ecg'] = False).
**Reason:** Real Section 7: no heart component (best CTPS 0.235), ECG-EEG alignment correlation 0.052 at lag 0.476 s, ECG duration 215.0 s vs EEG 216.0 s -> separate device clocks not verified.
**Alternatives considered:**
  - Trust StartTime alignment
  - Resample ECG to match the EEG duration
**Evidence:** Section 7.5 output.
**Expected effect:** No component is removed on unverified evidence.
**Risk:** Residual cardiac activity may remain; revisit if many recordings show a cardiac component.
**Reversible:** Yes
<!-- END D-020 -->

<!-- BEGIN D-021 -->
## D-021
**Decision ID:** D-021
**Date:** 2026-10-12
**Phase:** Phase 6
**Decision:** Task period = anchor + transition_exclusion_seconds to anchor + task_duration_seconds. Anchor = 'start' event; for tasks without 'start' (motor imagery): the protocol-constant start (25.000 s, all 'start' events within 0.000 s) when PROTOCOL_CONSTANT_START=True, else first target - median offset {'task-motorimagery': 2.0}. Windows are fixed 1000 samples with a 500-sample step; window metadata stores the rating but no label.
**Reason:** README: each task lasts 3 min; motor imagery events.tsv has no 'start' event (Section 3.8); labels must be fold-specific (D-013).
**Alternatives considered:**
  - Use the whole recording
  - Use first-to-last event
  - Drop motor imagery
**Evidence:** Section 8.3-8.5: 44,805 windows from 515 recordings.
**Expected effect:** Rest periods never receive a task rating; every window has the same shape.
**Risk:** The motor-imagery anchor is an estimate; a sensitivity check (shift +-5 s) is planned for Section 22.
**Reversible:** Yes
<!-- END D-021 -->

<!-- BEGIN D-022 -->
## D-022
**Decision ID:** D-022
**Date:** 2026-10-12
**Phase:** Phase 6
**Decision:** Demo-first: subjects ['sub-009', 'sub-019', 'sub-025'] (complete and fully rated) are preprocessed before the full dataset.
**Reason:** Roadmap golden rule: demo pipeline must work before the full run; Drive space is limited (E-007).
**Alternatives considered:**
  - Process all 515 recordings now
**Evidence:** Section 8.6 demo QC (63 recordings).
**Expected effect:** Errors surface on 63 recordings instead of 515.
**Risk:** Demo subjects may not represent noisier recordings.
**Reversible:** Yes
<!-- END D-022 -->

<!-- BEGIN D-023 -->
## D-023
**Decision ID:** D-023
**Date:** 2026-10-12
**Phase:** Phase 6
**Decision:** Processed EEG is stored as one float32 .npy array per recording (µV, task-period crop) and read through memory maps from a LOCAL copy during training; windows are (array, offset) rows in Parquet; no normalisation stored.
**Reason:** Drive benchmark (9.4) favoured HDF5 (1.0 vs 13 ms/window) because every .npy read re-opens a file over the Drive connection. Training reads from the local disk, where .npy = 0.164 ms and HDF5 = 0.351 ms per window; .npy files are independent (resumable build, no single-file corruption risk) and the 515-file store is already built.
**Alternatives considered:**
  - single HDF5 file
  - compressed NPZ (not lazily readable)
  - one file per window (2x size)
**Evidence:** Sections 9.4, 9.7, 9.9, 9.12.
**Expected effect:** Constant memory; fast reads once copied locally.
**Risk:** A copy to local disk (~2.9 GB) is needed at every new Colab session (Section 12).
**Reversible:** Yes
<!-- END D-023 -->

<!-- BEGIN D-024 -->
## D-024
**Decision ID:** D-024
**Date:** 2026-10-12
**Phase:** Phase 7
**Decision:** Splits: LOSO with 4 validation subjects per fold (seeded rotation, each subject validation 4x) + 3 cross-session folds (test = one session of all subjects; validation = other sessions of [np.str_('sub-008'), np.str_('sub-017'), np.str_('sub-026'), np.str_('sub-030')]). Splits and labels are per recording; label thresholds = tertiles of the fold's TRAINING recordings.
**Reason:** Subject-disjoint validation gives early stopping/model selection without touching the test subject; the rotation is fixed before any result exists; recordings are the labelled unit (87 windows share one rating).
**Alternatives considered:**
  - random validation windows (leaks subject)
  - validation = test subject's other session (leaks subject)
  - thresholds from train+val (D-013 wording allowed it; stricter rule chosen)
**Evidence:** Section 10.6: all leakage assertions PASS incl. the rating-perturbation test.
**Expected effect:** Every later model uses the same folds; results are comparable across models.
**Risk:** Cross-session folds share subjects between train and test by design (they measure session drift, not subject transfer).
**Reversible:** Yes
<!-- END D-024 -->

<!-- BEGIN D-025 -->
## D-025
**Decision ID:** D-025
**Date:** 2026-10-12
**Phase:** Phase 7
**Decision:** The task-only reference (CCEP component 1) is the floor every EEG model is compared with, fold by fold.
**Reason:** Task name alone reaches pooled LOSO balanced accuracy 0.744 (macro-F1 0.744).
**Alternatives considered:**
  - compare against chance only (would overstate any model)
**Evidence:** Section 10.5.
**Expected effect:** Claims of workload decoding must exceed the task-only reference and pass within-task tests (Section 22).
**Risk:** None.
**Reversible:** Yes
<!-- END D-025 -->

<!-- BEGIN D-026 -->
## D-026
**Decision ID:** D-026
**Date:** 2026-10-12
**Phase:** Phase 7
**Decision:** E-013 rule: an amplitude-flagged subject is not usable EEG if digitisation noise > 25% of its 1-40 Hz variance OR both its spectrum slope (2-30 Hz) and mean inter-channel |correlation| fall outside the range of the typical subjects. Result: excluded = none; primary subject set = 'all'.
**Reason:** Signal properties only (no labels, no model results); written before any model was trained.
**Alternatives considered:**
  - exclude all low-amplitude subjects without evidence
  - keep all without checking
**Evidence:** Section 11.4 table and /content/drive/MyDrive/CMx7_SI_DyGraph/figures/sec11_e013_signal_diagnosis.png.
**Expected effect:** Primary analysis uses only usable EEG; the other set is reported as sensitivity.
**Risk:** Thresholds of the rule are a judgement call; both subject sets are kept so the choice can be shown not to drive results.
**Reversible:** Yes
<!-- END D-026 -->

<!-- BEGIN D-027 -->
## D-027
**Decision ID:** D-027
**Date:** 2026-10-12
**Phase:** Phase 7
**Decision:** Normalisation statistics (per channel mean/std) come from the TRAINING recordings of each fold only, weighted exactly as the overlapping windows are seen in training. Two modes are stored: 'train_global' and 'recording_scaled' (each recording divided by its own label-free amplitude scale first). Section 13 selects the mode on validation subjects, never on test.
**Reason:** Subject amplitude spread after normalisation (max/min): train_global 27.68x, recording_scaled 1.37x -- absolute amplitude is a subject shortcut.
**Alternatives considered:**
  - per-window z-scoring (removes all amplitude information)
  - statistics from all subjects (leaks test data)
**Evidence:** Section 11.5/11.6 incl. perturbation test.
**Expected effect:** Models see comparable inputs across subjects without test-data leakage.
**Risk:** recording_scaled uses the test recording's own unlabelled amplitude (transductive, but no label and no other subject).
**Reversible:** Yes
<!-- END D-027 -->

<!-- BEGIN D-028 -->
## D-028
**Decision ID:** D-028
**Date:** 2026-10-12
**Phase:** Phase 8
**Decision:** Training epochs draw 16 random windows per training recording (new draw each epoch, seeded); validation uses a fixed 32 windows per recording; test uses every valid window. Predictions are averaged per recording (the labelled unit). Data are read from a local copy of the store.
**Reason:** The label belongs to the recording (87 windows share it); equal windows per recording stops long/clean recordings from dominating and keeps epochs short.
**Alternatives considered:**
  - all windows every epoch (4.5x slower, same information)
**Evidence:** Section 12.5: {'train_global': {'batch_x': (64, 32, 1000), 'dtype': 'torch.float32', 'finite': True, 'batch_mean': -0.001, 'batch_std': 0.972, 'labels': [0, 1, 2], 'windows_per_s': 225, 'train/val/test windows per epoch': (6896, 2016, 1729), 'train/val/test recordings': (431, 63, 20)}, 'recording_scaled': {'batch_x': (64, 32, 1000), 'dtype': 'torch.float32', 'finite': True, 'batch_mean': -0.001, 'batch_std': 0.941, 'labels': [0, 1, 2], 'windows_per_s': 1912, 'train/val/test windows per epoch': (6896, 2016, 1729), 'train/val/test recordings': (431, 63, 20)}}
**Expected effect:** Fast, balanced training; recording-level evaluation comparable to the task-only reference.
**Risk:** Fewer windows per epoch means more epochs to converge (early stopping handles it).
**Reversible:** Yes
<!-- END D-028 -->

<!-- BEGIN D-029 -->
## D-029
**Decision ID:** D-029
**Date:** 2026-10-12
**Phase:** Phase 8
**Decision:** Normalisation mode for the baselines: 'train_global', chosen by mean VALIDATION balanced accuracy on ['loso_00', 'loso_01', 'loso_02'] ({'recording_scaled': 0.45, 'train_global': 0.476}).
**Reason:** D-027: the mode is selected on validation subjects, never on test subjects.
**Alternatives considered:**
  - train_global
  - recording_scaled
**Evidence:** Section 13.5; /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec13_mode_selection.csv.
**Expected effect:** All later models use the same mode unless an ablation says otherwise.
**Risk:** Selection on 3 folds only (compute budget).
**Reversible:** Yes
<!-- END D-029 -->

<!-- BEGIN D-030 -->
## D-030
**Decision ID:** D-030
**Date:** 2026-10-12
**Phase:** Phase 8
**Decision:** Temporal CNN baseline = shared multi-scale temporal encoder (kernels [11, 25, 51]) per channel + flatten head; the same encoder feeds the graph models later.
**Reason:** Isolates what the graph adds on top of identical temporal features (clean ablation for Sections 15-17).
**Alternatives considered:**
  - EEGNet as the only baseline (Section 14 adds it)
**Evidence:** Section 13.7: {'folds': 30, 'test_recordings': 514, 'mode': 'train_global', 'parameters': 78699, 'pooled_rec_bal_acc': np.float64(0.376), 'pooled_rec_macro_f1': 0.366, 'fold_rec_bal_acc_mean': np.float64(0.407), 'fold_rec_bal_acc_sd': 0.117, 'task_only_pooled_bal_acc (Section 10)': 0.744, 'folds_better_than_task_only': 2, 'mean_diff_vs_task_only': np.float64(-0.363)}
**Expected effect:** Reference point for every later model.
**Risk:** Hyperparameters fixed a priori, not tuned.
**Reversible:** Yes
<!-- END D-030 -->

<!-- BEGIN D-031 -->
## D-031
**Decision ID:** D-031
**Date:** 2026-10-12
**Phase:** Phase 8
**Decision:** EEGNet-8,2 baseline with kernels scaled to 250 Hz (125/16 samples), dropout 0.25, no max-norm (weight decay instead); same folds, loaders, normalisation (D-029), early stopping and recording-level evaluation as the Temporal CNN.
**Reason:** Standard compact EEG reference; tells whether near-chance performance is architecture-specific.
**Alternatives considered:**
  - ShallowConvNet
  - DeepConvNet (too large for 30 subjects)
**Evidence:** Section 14.6: {'folds': 30, 'test_recordings': 514, 'mode': 'train_global', 'parameters': 3595, 'pooled_rec_bal_acc': np.float64(0.459), 'pooled_rec_macro_f1': 0.448, 'fold_bal_acc_mean': np.float64(0.452), 'fold_bal_acc_sd': 0.153, 'tcnn_fold_bal_acc_mean': np.float64(0.407), 'task_only_fold_bal_acc_mean': np.float64(0.771), 'folds_eegnet_better_than_tcnn': 14, 'folds_eegnet_better_than_task_only': 3, 'wilcoxon_p_eegnet_vs_tcnn (descriptive)': 0.0885, 'folds_collapsed_to_one_class': 8}
**Expected effect:** Second baseline for the graph models (Sections 15-17).
**Risk:** Hyperparameters taken from the paper, not tuned.
**Reversible:** Yes
<!-- END D-031 -->

<!-- BEGIN D-032 -->
## D-032
**Decision ID:** D-032
**Date:** 2026-10-12
**Phase:** Phase 8
**Decision:** Fixed-graph GCN baseline: temporal encoder of the Temporal CNN + 2 residual graph-convolution layers on a k-nearest-neighbour electrode graph (k=4, colin27_1020 positions, symmetric, self-loops, D^-1/2 (A+I) D^-1/2) + the same flatten head.
**Reason:** Isolates the effect of message passing on a predefined, data-independent graph (no functional connectivity, no leakage).
**Alternatives considered:**
  - distance-threshold graph
  - fully connected graph
  - correlation graph (data-dependent, excluded by design)
**Evidence:** Section 15.5: {'folds': 30, 'test_recordings': 514, 'mode': 'train_global', 'parameters': 81931, 'pooled_rec_bal_acc': np.float64(0.377), 'pooled_rec_macro_f1': 0.36, 'fold_bal_acc_mean': np.float64(0.423), 'fold_bal_acc_sd': 0.12, 'tcnn_fold_mean': np.float64(0.407), 'eegnet_fold_mean': np.float64(0.452), 'task_only_fold_mean': np.float64(0.771), 'folds_gcn_better_than_tcnn': 11, 'folds_gcn_better_than_eegnet': 11, 'folds_gcn_better_than_task_only': 1, 'wilcoxon_p_gcn_vs_tcnn (descriptive)': 0.4654, 'wilcoxon_p_gcn_vs_eegnet (descriptive)': 0.4758, 'folds_collapsed_to_one_class': 9}
**Expected effect:** Reference for the learnable graphs in Sections 16-17.
**Risk:** k fixed a priori, not tuned.
**Reversible:** Yes
<!-- END D-032 -->

<!-- BEGIN D-033 -->
## D-033
**Decision ID:** D-033
**Date:** 2026-10-12
**Phase:** Phase 8
**Decision:** Static learnable graph: one symmetric sigmoid-weighted 32x32 graph per fold, top-6 links per channel, L1 0.001, initialised from the scalp kNN graph; same encoder, graph layers and head as the fixed-graph GCN. run_fold adds a model's extra_loss() if it defines one (unchanged for the baselines).
**Reason:** Separates 'learning which links matter' from 'one graph per window' (Section 17).
**Alternatives considered:**
  - dense learned graph (no sparsity)
  - random initialisation
**Evidence:** Section 16.5-16.6: {'folds': 30, 'test_recordings': 514, 'mode': 'train_global', 'parameters': 82955, 'pooled_rec_bal_acc': np.float64(0.415), 'pooled_rec_macro_f1': 0.409, 'fold_bal_acc_mean': np.float64(0.405), 'fold_bal_acc_sd': 0.114, 'folds_better_than_fixed_graph': 10, 'folds_better_than_eegnet': 10, 'folds_better_than_task_only': 0, 'wilcoxon_p_vs_fixed_graph (descriptive)': 0.6262, 'wilcoxon_p_vs_tcnn (descriptive)': 0.8086, 'wilcoxon_p_vs_eegnet (descriptive)': 0.2364, 'folds_collapsed_to_one_class': 7}; {'links_per_fold_mean': 111.7, 'stability_mean_jaccard_between_folds': 0.517, 'links_kept_in_all_folds': 69, 'links_kept_in_>=80%_folds': 69, 'share_of_learned_links_that_are_scalp_neighbours': 0.618, 'share_of_scalp_neighbour_links_kept': 1.0}
**Expected effect:** Graph-learning reference for the dynamic model.
**Risk:** top-k and L1 fixed a priori, not tuned.
**Reversible:** Yes
<!-- END D-033 -->

<!-- BEGIN D-034 -->
## D-034
**Decision ID:** D-034
**Date:** 2026-10-12
**Phase:** Phase 9
**Decision:** Epoch-specific dynamic graph: per window, symmetric query/key channel-pair scores (dim 16) + a learnable scalp-neighbour bias (knn), top-6 links per channel with softmax weights, self-loop 0.5; same encoder, graph layers and head as Sections 15-16. Graphs analysed on validation subjects only.
**Reason:** Section 16 showed a free-parameter graph barely moves from its initialisation (all scalp links kept in 30/30 folds, weights 0.881 -> ~0.885); a feature-computed graph receives a gradient from every window and can differ between windows.
**Alternatives considered:**
  - free-parameter static graph (Section 16)
  - dense attention graph (no sparsity)
  - correlation/coherence graphs (excluded by design)
**Evidence:** Section 17.5-17.6: {'folds': 30, 'test_recordings': 514, 'mode': 'train_global', 'parameters': 83052, 'pooled_rec_bal_acc': np.float64(0.37), 'pooled_rec_macro_f1': 0.352, 'fold_bal_acc_mean': np.float64(0.41), 'fold_bal_acc_sd': 0.121, 'folds_better_than_static_graph': 12, 'folds_better_than_fixed_graph': 4, 'folds_better_than_eegnet': 10, 'folds_better_than_task_only': 1, 'wilcoxon_p_vs_static_graph (descriptive)': 0.9353, 'wilcoxon_p_vs_fixed_graph (descriptive)': 0.023, 'wilcoxon_p_vs_tcnn (descriptive)': 0.8552, 'wilcoxon_p_vs_eegnet (descriptive)': 0.301, 'folds_collapsed_to_one_class': 8}; {'validation_subjects': 4.0, 'windows': 2193.067, 'prior_scale_learned': 1.038, 'distinct_graphs_share': 0.858, 'jaccard_same_recording': 0.561, 'jaccard_same_subject_other_recording': 0.487, 'jaccard_different_subjects': 0.355, 'share_links_scalp_neighbours': 0.447, 'workload_separation_vs_chance': 4.511, 'subject_separation_vs_chance': 11.342}
**Expected effect:** Core graph module for Sections 18-21.
**Risk:** top-k, dim and prior fixed a priori, not tuned on test.
**Reversible:** Yes
<!-- END D-034 -->

<!-- BEGIN D-035 -->
## D-035
**Decision ID:** D-035
**Date:** 2026-10-12
**Phase:** Phase 9
**Decision:** Graph consistency/separation loss: per batch, W = spread of (subject, workload-level) mean window graphs around the level prototype (mean of subject means), B = spread of the level prototypes; loss = λ·W/(W+B) added to cross-entropy. λ chosen from [0.1, 0.3, 1.0] on validation subjects of ['loso_00', 'loso_01', 'loso_02'] (tie -> smaller): λ = 1.
**Reason:** Section 17 graphs separated people 11.3x above chance vs workload 4.5x (30/30 folds); the loss targets that subject shortcut in the graph space directly. Scale-free ratio, no margin hyperparameter.
**Alternatives considered:**
  - margin-based contrastive loss on graphs
  - graph loss on all window pairs (O(B^2))
  - no graph loss (Section 17)
**Evidence:** Section 18.4-18.6: {'folds': 30, 'test_recordings': 514, 'mode': 'train_global', 'lambda': 1.0, 'pooled_rec_bal_acc': np.float64(0.364), 'pooled_rec_macro_f1': 0.35, 'fold_bal_acc_mean': np.float64(0.424), 'fold_bal_acc_sd': 0.114, 'folds_better_than_dynamic_graph': 13, 'folds_worse_than_dynamic_graph': 8, 'folds_better_than_fixed_graph': 8, 'folds_better_than_eegnet': 10, 'folds_better_than_task_only': 0, 'wilcoxon_p_vs_dynamic_graph (descriptive)': 0.6894, 'wilcoxon_p_vs_fixed_graph (descriptive)': 0.7151, 'wilcoxon_p_vs_eegnet (descriptive)': 0.429, 'folds_collapsed_to_one_class': 8}
**Expected effect:** Graph-level invariance term for the full model (Section 21).
**Risk:** λ grid fixed a priori; choice uses validation subjects only.
**Reversible:** Yes
<!-- END D-035 -->

<!-- BEGIN D-036 -->
## D-036
**Decision ID:** D-036
**Date:** 2026-10-12
**Phase:** Phase 9
**Decision:** Subject-adversarial learning: subject classifier (64-64-30) on the 64-d embedding behind a gradient reversal layer; reversal strength ramps 0 -> β (DANN schedule) over 500 steps; β chosen from [0.1, 0.3, 1.0] on validation subjects of ['loso_00', 'loso_01', 'loso_02'] (tie -> smaller): β = 0.1. Built on the Section 18 model.
**Reason:** Section 18 reduced subject information in the graphs (11.3x -> 8.6x chance) but ~93% of graph variation was still not workload and accuracy did not change; the features the classifier uses must hide the person directly.
**Alternatives considered:**
  - adversary on the graph instead of the embedding
  - fixed β without ramp
  - MMD / CORAL alignment across subjects
**Evidence:** Section 19.4-19.6: {'folds': 30, 'test_recordings': 514, 'mode': 'train_global', 'lambda': 1.0, 'beta': 0.1, 'pooled_rec_bal_acc': np.float64(0.367), 'pooled_rec_macro_f1': 0.358, 'fold_bal_acc_mean': np.float64(0.41), 'fold_bal_acc_sd': 0.12, 'folds_better_than_section18': 14, 'folds_worse_than_section18': 10, 'folds_better_than_eegnet': 12, 'folds_better_than_task_only': 1, 'wilcoxon_p_vs_section18 (descriptive)': 0.8415, 'wilcoxon_p_vs_section17 (descriptive)': 0.372, 'wilcoxon_p_vs_eegnet (descriptive)': 0.3002, 'folds_collapsed_to_one_class': 9, 'collapsed_folds': 'sub-005, sub-009, sub-010, sub-011, sub-012, sub-013, sub-014, sub-022, sub-026'}
**Expected effect:** Subject-invariance component of the full model (Section 21).
**Risk:** β grid and ramp fixed a priori; choice uses validation only.
**Reversible:** Yes
<!-- END D-036 -->

<!-- BEGIN D-037 -->
## D-037
**Decision ID:** D-037
**Date:** 2026-10-12
**Phase:** Phase 9
**Decision:** Task-adversarial learning on top of the Section 19 model: B = plain task GRL (adversary sees z), C = TCAI (adversary sees [z, one-hot 1-9 training rating]); 7-way task head (64 hidden), DANN ramp over 500 steps; γ chosen separately per variant from [0.1, 0.3, 1.0] on validation of ['loso_00', 'loso_01', 'loso_02']: {'plain': 0.1, 'tcai': 0.3}. Within-task ρ tasks fixed from training rating SD >= 1.0: ['task-full', 'task-mentalarithmetic', 'task-motorimagery', 'task-nback', 'task-nbackarithmetic'].
**Reason:** Task explains 76.5% of rating variance; plain task invariance would also remove the workload signal shared with task difficulty. Conditioning the adversary on the rating targets z ⊥ task | rating (novelty N1).
**Alternatives considered:**
  - condition on the 3-class label instead of the rating
  - adversary on the graph
  - no task adversary (A)
**Evidence:** Section 20.5-20.6: [{'model': 'A_no_task_adv', 'fold_bal_acc_mean': 0.41, 'pooled_rec_macro_f1': 0.358, 'mean_within_task_rho': -0.054}, {'model': 'B_plain_task_grl', 'fold_bal_acc_mean': 0.364, 'pooled_rec_macro_f1': 0.302, 'mean_within_task_rho': -0.175}, {'model': 'C_tcai', 'fold_bal_acc_mean': 0.322, 'pooled_rec_macro_f1': 0.317, 'mean_within_task_rho': -0.008}]; criterion {'TCAI >= plain GRL on pooled macro-F1': True, 'TCAI >= plain GRL on mean within-task ρ': True}; probes [{'probe': 'task from embedding (new person)', 'chance': 0.143, 'A_no_task_adv': 0.156, 'B_plain_task_grl': 0.163, 'C_tcai': 0.161, 'folds_C_lower_than_A': 13, 'wilcoxon_p_C_vs_A': 0.229, 'wilcoxon_p_C_vs_B': 0.685}, {'probe': 'task within workload class (new person)', 'chance': 0.234, 'A_no_task_adv': 0.213, 'B_plain_task_grl': 0.221, 'C_tcai': 0.221, 'folds_C_lower_than_A': 15, 'wilcoxon_p_C_vs_A': 0.452, 'wilcoxon_p_C_vs_B': 0.903}]
**Expected effect:** N1 evidence for the thesis; the full model (Section 21) uses the variant and settings justified here.
**Risk:** γ grid, ramp and rating conditioning fixed a priori; choices use validation only; test used once per variant.
**Reversible:** Yes
<!-- END D-037 -->

<!-- BEGIN D-038 -->
## D-038
**Decision ID:** D-038
**Date:** 2026-10-12
**Phase:** Phase 10
**Decision:** Full model fixed a priori from the project description: temporal CNN + per-window sparse graph + 2 graph layers + attention pooling (4 heads, channel embedding) + graph consistency (λ=1) + subject GRL (β=0.1) + TCAI (γ=0.3); λ/β/γ re-derived from the validation selection files; 3 seeds [0, 1000, 2000]; primary result = seed ensemble (mean class probabilities per recording), per-seed mean ± SD reported.
**Reason:** Sections 18-20 test results were NOT used to drop or re-tune components (no test-based model selection); attention pooling gives channel importance (Section 25) and cuts prediction parameters ~3x; 3 seeds quantify training variance for the N3 benchmark.
**Alternatives considered:**
  - drop components that lowered test accuracy (rejected: test-based selection)
  - flatten head (no channel weights)
  - single seed
**Evidence:** Section 21.5: ensemble {'accuracy': 0.32879377431906615, 'balanced_accuracy': np.float64(0.3253603537090592), 'macro_f1': 0.3229996086071772, 'cohen_kappa': np.float64(-0.01168980094819183), 'mean_within_task_rho': np.float64(-0.15818886449552302)}; seeds [{'seed_offset': 0, 'accuracy': 0.354, 'balanced_accuracy': 0.355, 'macro_f1': 0.35, 'cohen_kappa': 0.031, 'mean_within_task_rho': -0.188, 'fold_bal_acc_mean': 0.333}, {'seed_offset': 1000, 'accuracy': 0.335, 'balanced_accuracy': 0.329, 'macro_f1': 0.314, 'cohen_kappa': -0.007, 'mean_within_task_rho': -0.082, 'fold_bal_acc_mean': 0.327}, {'seed_offset': 2000, 'accuracy': 0.317, 'balanced_accuracy': 0.318, 'macro_f1': 0.318, 'cohen_kappa': -0.026, 'mean_within_task_rho': -0.134, 'fold_bal_acc_mean': 0.311}]
**Expected effect:** Reference model for Sections 22-27; ablation (Section 24) removes one component at a time from it.
**Risk:** Attention-pooling settings fixed a priori, not tuned.
**Reversible:** Yes
<!-- END D-038 -->

<!-- BEGIN D-039 -->
## D-039
**Decision ID:** D-039
**Date:** 2026-10-12
**Phase:** Phase 10
**Decision:** Model v2 = Section 21 full model + per-subject input alignment from the person's own unlabeled EEG; candidates ['subject_zscore', 'subject_euclid'] (z-score; Euclidean alignment with eigenvalue floor); each trained once (seed 0) on all LOSO folds; v2 = best mean validation balanced accuracy, final only if > v1 seed 0 on validation. Result: final = v2 (subject_zscore).
**Reason:** Sections 17-21: identity dominates the representation (probe 0.92) and models collapse to one class per new person (17/30 folds in Section 21); per-subject alignment removes subject offsets before the network.
**Alternatives considered:**
  - no alignment (v1)
  - train-only global normalisation (Section 11)
  - recording-level scaling (Section 24 sensitivity)
**Evidence:** 21B.5 validation {'v1 (no alignment, seed 0)': 0.4156, 'v2 subject_zscore': 0.4387, 'v2 subject_euclid': 0.3991}; test [{'model': 'EEGNet', 'fold_bal_acc_mean': 0.452, 'macro_f1': 0.448}, {'model': 'v1 seed 0', 'fold_bal_acc_mean': 0.333, 'macro_f1': 0.35}, {'model': 'v1 seed ensemble', 'fold_bal_acc_mean': 0.324, 'macro_f1': 0.323}, {'model': 'v2 subject_zscore', 'fold_bal_acc_mean': 0.349, 'macro_f1': 0.319}, {'model': 'v2 subject_euclid', 'fold_bal_acc_mean': 0.324, 'macro_f1': 0.307}]; probes [{'probe': 'who_is_it', 'v1': 0.798, 'v2_subject_zscore': 0.824, 'v2_subject_euclid': 0.855}, {'probe': 'workload', 'v1': 0.326, 'v2_subject_zscore': 0.35, 'v2_subject_euclid': 0.327}, {'probe': 'task', 'v1': 0.146, 'v2_subject_zscore': 0.152, 'v2_subject_euclid': 0.153}, {'probe': 'task_within_class', 'v1': 0.214, 'v2_subject_zscore': 0.204, 'v2_subject_euclid': 0.205}]
**Expected effect:** Final model for Sections 22-27.
**Risk:** Transductive (uses the test person's unlabeled EEG); stated as such.
**Reversible:** Yes
<!-- END D-039 -->

<!-- BEGIN D-040 -->
## D-040
**Decision ID:** D-040
**Date:** 2026-10-12
**Phase:** Phase 10
**Decision:** Scope fixed with the supervisor-facing plan: XAI (attention, Integrated Gradients, channel deletion, band occlusion, artifact-shortcut audit, graph explanation) is part of Section 25; external validation on COG-BCI (Hinss et al. 2023) is done AFTER Section 27 with the frozen final model.
**Reason:** The proposed model must be explained (XAI) and validated on an independent multi-task dataset without influencing any CMx7 decision.
**Alternatives considered:**
  - EEGMAT (single-task; kept optional)
  - external validation before the final model is frozen (rejected: leakage risk)
**Evidence:** planning decision
**Expected effect:** Sections 25 and post-27.
**Risk:** 
**Reversible:** Yes
<!-- END D-040 -->

<!-- BEGIN D-041 -->
## D-041
**Decision ID:** D-041
**Date:** 2026-10-12
**Phase:** Phase 11
**Decision:** N2 protocol completed: task-only Δ, within-task ρ, within-task label permutation (train+val only, seed 7777; final model and EEGNet retrained once), conditional task probe (21B.6), stimulus-rhythm comb features (225 periods 0.8-12.0 s, LOSO logistic decoders).
**Reason:** Separates workload from task identity and stimulus timing; settings fixed before running.
**Alternatives considered:**
  - permutation across tasks (would destroy the task structure)
  - rhythm features from event files (not needed; label-free spectrum)
**Evidence:** 22.3-22.7: [{'component': '1 task-only baseline', 'measure': 'fold-mean balanced accuracy minus task-only', 'final_model': -0.422, 'EEGNet': -0.319, 'reference': 'task-only 0.771'}, {'component': '2 within-task agreement', 'measure': 'mean Spearman ρ over 5 eligible tasks', 'final_model': 0.049, 'EEGNet': -0.041, 'reference': '0 = no tracking'}, {'component': '3 within-task permutation', 'measure': 'fold-mean bal. acc.: permuted minus true training labels', 'final_model': 0.0, 'EEGNet': -0.014, 'reference': '≈0 -> task-level shortcut'}, {'component': '4 conditional task probe', 'measure': 'task within workload class (validation embeddings)', 'final_model': 0.204, 'EEGNet': nan, 'reference': 'chance ≈ 0.23'}, {'component': '5 stimulus rhythm', 'measure': 'task decodable from rhythm-only features (bal. acc.)', 'final_model': nan, 'EEGNet': nan, 'reference': '0.190 (chance 0.143)'}]
**Expected effect:** N2 evidence; final benchmark table (N3).
**Risk:** One permutation seed (time budget).
**Reversible:** Yes
<!-- END D-041 -->

<!-- BEGIN D-042b -->
## D-042b
**Decision ID:** D-042b
**Date:** 2026-10-12
**Phase:** Phase 11
**Decision:** Model v3 (hybrid EEGNet + graph, Section 21C) NOT run.
**Reason:** Section 22 permutation: EEGNet's accuracy is task-level; adding its branch would raise accuracy through the shortcut N2 exposes.
**Alternatives considered:**
  - run v3 anyway
**Evidence:** 22.5 permutation EEGNet 0.452 -> 0.438 (p = 0.99)
**Expected effect:** Time used for N1 on EEGNet instead.
**Risk:** 
**Reversible:** Yes
<!-- END D-042b -->

<!-- BEGIN D-043 -->
## D-043
**Decision ID:** D-043
**Date:** 2026-10-12
**Phase:** Phase 11
**Decision:** N1 (TCAI) evaluated on the EEGNet backbone: plain task GRL vs TCAI, γ from [0.1, 0.3, 1.0] per variant on validation; pre-registered verdict rule saved before training (sec22b_n1_rule.json). Verdict: NOT SUPPORTED.
**Reason:** The graph backbone carried no transferable task information (probe at chance), so TCAI had nothing to remove; EEGNet's accuracy is task-level (Section 22 permutation), which makes it the backbone where TCAI's claim is testable.
**Alternatives considered:**
  - TCAI on the graph backbone only (Section 20)
  - no further N1 test
**Evidence:** 22B.5-22B.6: [{'model': 'A EEGNet', 'fold_bal_acc_mean': 0.452, 'macro_f1': 0.448, 'mean_within_task_rho': -0.041}, {'model': 'B EEGNet + plain GRL', 'fold_bal_acc_mean': 0.459, 'macro_f1': 0.45, 'mean_within_task_rho': -0.076}, {'model': 'C EEGNet + TCAI', 'fold_bal_acc_mean': 0.421, 'macro_f1': 0.428, 'mean_within_task_rho': -0.092}]; probes [{'probe': 'task', 'A': 0.16, 'B': 0.162, 'C': 0.16, 'wilcoxon_p_C_vs_A': 0.974, 'wilcoxon_p_C_vs_B': 0.44}, {'probe': 'task_within_class', 'A': 0.218, 'B': 0.219, 'C': 0.217, 'wilcoxon_p_C_vs_A': 0.919, 'wilcoxon_p_C_vs_B': 0.837}, {'probe': 'workload', 'A': 0.334, 'B': 0.34, 'C': 0.339, 'wilcoxon_p_C_vs_A': 0.318, 'wilcoxon_p_C_vs_B': 0.952}]
**Expected effect:** N1 evidence for the thesis.
**Risk:** Motivated by the Section 22 result; disclosed as such.
**Reversible:** Yes
<!-- END D-043 -->

<!-- BEGIN D-046 -->
## D-046
**Decision ID:** D-046
**Date:** 2026-10-12
**Phase:** Phase 11
**Decision:** N2 extras: rhythm task decoder tested against 100 within-subject label permutations (p = 0.0099); pre-registered hypothesis 'EEGNet mainly separates motor from cognitive tasks' (groups fixed a priori): SUPPORTED.
**Reason:** Section 22 left the rhythm decoder (0.19-0.20 vs 0.143) without a significance test, and EEGNet's per-task pattern (14.6) suggested a motor/cognitive split; both are needed before writing RQ1 and N2.
**Alternatives considered:**
  - parametric binomial test (ignores fold structure)
  - post-hoc task grouping (rejected: groups fixed by task design)
**Evidence:** 22C.3-22C.5: [{'item': 'rhythm task decoder (pooled bal. acc.)', 'value': 0.19, 'reference': 'null mean 0.141', 'p_value': 0.0099}, {'item': 'EEGNet acc. motor - cognitive (held-out subjects)', 'value': 0.2172, 'reference': '0', 'p_value': 0.0132}, {'item': 'EEGNet motor-vs-cognitive probe (validation)', 'value': 0.5412, 'reference': 'chance 0.5', 'p_value': 0.0}, {'item': 'hypothesis verdict', 'value': nan, 'reference': 'SUPPORTED', 'p_value': nan}]
**Expected effect:** RQ1 answer and N2 component 5 strength.
**Risk:** No new training.
**Reversible:** Yes
<!-- END D-046 -->

<!-- BEGIN D-044 -->
## D-044
**Decision ID:** D-044
**Date:** 2026-10-12
**Phase:** Phase 11
**Decision:** Cross-session evaluation on ['xses_ses-01', 'xses_ses-02', 'xses_ses-03'] (seed 0): task-only, EEGNet (+plain GRL, +TCAI), dynamic graph, graph A/B/C, final v2. Final-model alignment statistics from each person's TRAINING sessions only; KSS confound analysed within task.
**Reason:** Second benchmark protocol (N3) and the pre-planned cross-session test of N1.
**Alternatives considered:**
  - alignment using the test session (transductive)
**Evidence:** 23.4: [{'model': 'task name only (no EEG)', 'balanced_accuracy': 0.744, 'macro_f1': 0.744, 'mean_within_task_rho': nan}, {'model': 'EEGNet', 'balanced_accuracy': 0.462, 'macro_f1': 0.46, 'mean_within_task_rho': 0.132}, {'model': 'EEGNet + plain GRL', 'balanced_accuracy': 0.465, 'macro_f1': 0.463, 'mean_within_task_rho': 0.136}, {'model': 'EEGNet + TCAI', 'balanced_accuracy': 0.478, 'macro_f1': 0.476, 'mean_within_task_rho': 0.124}, {'model': 'Dynamic graph', 'balanced_accuracy': 0.46, 'macro_f1': 0.459, 'mean_within_task_rho': 0.184}, {'model': 'Graph A (+consistency +subject adv)', 'balanced_accuracy': 0.501, 'macro_f1': 0.475, 'mean_within_task_rho': 0.205}, {'model': 'Graph B (+plain GRL)', 'balanced_accuracy': 0.481, 'macro_f1': 0.468, 'mean_within_task_rho': 0.149}, {'model': 'Graph C (+TCAI)', 'balanced_accuracy': 0.466, 'macro_f1': 0.457, 'mean_within_task_rho': 0.166}, {'model': 'Final model v2', 'balanced_accuracy': 0.383, 'macro_f1': 0.377, 'mean_within_task_rho': 0.037}]; N1 [{'backbone': 'EEGNet', 'macro_f1_A': 0.46, 'macro_f1_B': 0.463, 'macro_f1_C': 0.476, 'rho_A': 0.132, 'rho_B': 0.136, 'rho_C': 0.124, 'C1_macroF1_C>=B': True, 'C2_rho_C>=B': False}, {'backbone': 'graph', 'macro_f1_A': 0.475, 'macro_f1_B': 0.468, 'macro_f1_C': 0.457, 'rho_A': 0.205, 'rho_B': 0.149, 'rho_C': 0.166, 'C1_macroF1_C>=B': False, 'C2_rho_C>=B': True}]
**Expected effect:** Cross-session results for Sections 26-27.
**Risk:** Seed 0 only; 3 folds.
**Reversible:** Yes
<!-- END D-044 -->

<!-- BEGIN D-045 -->
## D-045
**Decision ID:** D-045
**Date:** 2026-10-12
**Phase:** Phase 11
**Decision:** Ablation: leave-one-out from the final model (['− TCAI', '− subject adversary', '− graph consistency']; seed 0, all LOSO folds), build-up table across Sections 16-21B, low-amplitude re-analysis (['sub-009', 'sub-010', 'sub-011', 'sub-012', 'sub-013']); seed SD 0.012 used as the noise reference.
**Reason:** Quantifies each component's contribution on identical folds.
**Alternatives considered:**
  - multi-seed ablation (time)
**Evidence:** 24.3: [{'variant': 'FINAL model v2 (all components)', 'fold_bal_acc_mean': 0.349, 'macro_f1': 0.319, 'mean_within_task_rho': 0.049}, {'variant': '− TCAI', 'fold_bal_acc_mean': 0.382, 'macro_f1': 0.353, 'mean_within_task_rho': 0.005}, {'variant': '− subject adversary', 'fold_bal_acc_mean': 0.328, 'macro_f1': 0.318, 'mean_within_task_rho': -0.04}, {'variant': '− graph consistency', 'fold_bal_acc_mean': 0.332, 'macro_f1': 0.334, 'mean_within_task_rho': -0.095}]
**Expected effect:** Ablation evidence for Sections 26-27.
**Risk:** Seed 0 only.
**Reversible:** Yes
<!-- END D-045 -->

<!-- BEGIN D-047 -->
## D-047
**Decision ID:** D-047
**Date:** 2026-10-12
**Phase:** Phase 12
**Decision:** XAI on held-out test subjects (EEGNet, final model v2): occlusion (channel/region/band), Integrated Gradients (16 steps), deletion test, attention, learned graphs; artefact audit with a-priori regions and threshold 1.5x.
**Reason:** Explains what the models use and checks EMG/eye shortcuts; descriptive only, no setting chosen from it.
**Alternatives considered:**
  - validation subjects only (Section 21.6 already did attention there)
  - SHAP (slower, same family as IG)
**Evidence:** 25.5: [{'model': 'EEGNet', 'temporal_occlusion_ratio': 0.6982533150578941, 'temporal_ig_ratio': 0.865442793816328, 'temporal_attention_ratio': nan, 'frontal_polar_occlusion_ratio': 0.9471578042426568, 'top_band': 'delta', 'gamma_drop': 0.004350129557042237, 'EMG_warning': False, 'eye_warning': False, 'channel_ranking_stability_occlusion': 0.02120537971483466}, {'model': 'Final model v2', 'temporal_occlusion_ratio': 0.8902088955929295, 'temporal_ig_ratio': 0.9053921063327127, 'temporal_attention_ratio': 1.0283965494121527, 'frontal_polar_occlusion_ratio': 0.7742505608870338, 'top_band': 'beta', 'gamma_drop': 0.010415614388845522, 'EMG_warning': False, 'eye_warning': False, 'channel_ranking_stability_occlusion': 0.02672160986955202}]
**Expected effect:** Interpretability chapter.
**Risk:** Seed 0 models only.
**Reversible:** Yes
<!-- END D-047 -->

<!-- BEGIN D-048 -->
## D-048
**Decision ID:** D-048
**Date:** 2026-10-12
**Phase:** Phase 12
**Decision:** Statistics: subject = unit (n = 30); Wilcoxon signed-rank, bootstrap 95% CI over subjects, rank-biserial r and Cohen's d_z; Holm within four families fixed before the p-values (F1 vs chance, F2 vs task-only, F3 planned LOSO, F4 cross-session); Friedman + Nemenyi CD.
**Reason:** One consistent, conservative method for every thesis claim.
**Alternatives considered:**
  - Bonferroni (more conservative)
  - no correction (inflates false positives)
**Evidence:** 26.6 claims: [{'claim': 'N3a LOSO benchmark', 'verdict': 'DELIVERED'}, {'claim': 'N3b cross-session benchmark', 'verdict': 'DELIVERED'}, {'claim': 'N2-1 task-only reference', 'verdict': 'SUPPORTED'}, {'claim': 'N2-2 within-task agreement', 'verdict': 'SUPPORTED'}, {'claim': 'N2-3 within-task permutation', 'verdict': 'SUPPORTED'}, {'claim': 'N2-5 stimulus rhythm', 'verdict': 'SUPPORTED (weak cue)'}, {'claim': 'RQ1 EEGNet mechanism', 'verdict': 'SUPPORTED'}, {'claim': 'N1 TCAI, EEGNet LOSO', 'verdict': 'NOT SUPPORTED'}, {'claim': 'N1 TCAI, graph LOSO', 'verdict': 'NOT SUPPORTED'}, {'claim': 'N1 TCAI, cross-session', 'verdict': 'NOT SUPPORTED'}, {'claim': 'Subject adversary', 'verdict': 'NOT SUPPORTED (direction only)'}, {'claim': 'Normalisation is not the cause', 'verdict': 'SUPPORTED'}, {'claim': 'Artefact shortcut audit', 'verdict': 'NO WARNING'}]
**Expected effect:** Statistics chapter; claims ledger.
**Risk:** Seed 0 except the v1 ensemble.
**Reversible:** Yes
<!-- END D-048 -->

<!-- BEGIN D-049 -->
## D-049
**Decision ID:** D-049
**Date:** 2026-10-12
**Phase:** Phase 12
**Decision:** Final report built only from saved result files; SHA-256 manifest of results/figures/folds; download bundle without checkpoints or EEG.
**Reason:** Every number in the thesis is traceable to a file and a hash.
**Alternatives considered:**
  - hand-copied tables (error-prone)
**Evidence:** 27.3-27.4: 161 files hashed; claims [{'claim': 'N3a LOSO benchmark', 'verdict': 'DELIVERED'}, {'claim': 'N3b cross-session benchmark', 'verdict': 'DELIVERED'}, {'claim': 'N2-1 task-only reference', 'verdict': 'SUPPORTED'}, {'claim': 'N2-2 within-task agreement', 'verdict': 'SUPPORTED'}, {'claim': 'N2-3 within-task permutation', 'verdict': 'SUPPORTED'}, {'claim': 'N2-5 stimulus rhythm', 'verdict': 'SUPPORTED (weak cue)'}, {'claim': 'RQ1 EEGNet mechanism', 'verdict': 'SUPPORTED'}, {'claim': 'N1 TCAI, EEGNet LOSO', 'verdict': 'NOT SUPPORTED'}, {'claim': 'N1 TCAI, graph LOSO', 'verdict': 'NOT SUPPORTED'}, {'claim': 'N1 TCAI, cross-session', 'verdict': 'NOT SUPPORTED'}, {'claim': 'Subject adversary', 'verdict': 'NOT SUPPORTED (direction only)'}, {'claim': 'Normalisation is not the cause', 'verdict': 'SUPPORTED'}, {'claim': 'Artefact shortcut audit', 'verdict': 'NO WARNING'}]
**Expected effect:** Thesis results chapter and appendix.
**Risk:** None.
**Reversible:** Yes
<!-- END D-049 -->

<!-- BEGIN D-050 -->
## D-050
**Decision ID:** D-050
**Date:** 2026-10-12
**Phase:** Phase 12
**Decision:** Paper figures (10) and LaTeX tables (3) generated only from the saved result files of Sections 22-27; vector PDF + 300 dpi PNG at IEEE column widths; colour-blind-safe categorical slots with marker shapes as a second cue; captions generated from the same tables.
**Reason:** Every number in a figure, table or caption is traceable to a result file; no re-analysis and no new choice from test data.
**Alternatives considered:**
  - hand-made figures (error-prone)
  - re-using the diagnostic figures of Sections 13-26 (too dense for a paper)
**Evidence:** 28.13 checks: {'all_figures_drawn': True, 'pdf_and_png_written': True, 'png_resolution_at_least_dpi': True, 'fig02_values_equal_table': True, 'fig03_one_point_per_subject': True, 'fig04_values_equal_table': True, 'label_figure_covers_all_test_recordings': True, 'latex_tables_complete': True, 'captions_for_every_figure': True, 'result_files_unchanged': True, 'outputs_only_in_paper_folders': True}
**Expected effect:** Figures and tables for the thesis / paper.
**Risk:** None (descriptive).
**Reversible:** Yes
<!-- END D-050 -->
