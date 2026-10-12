<!-- CMx7-SI-DyGraph log v1 -->
# ERROR_LOG — CMx7-SI-DyGraph

<!-- BEGIN E-003 -->
## E-003
**Error ID:** E-003
**Date:** 2026-10-12
**Section:** 1
**Status:** SOLVED
**Description:** Resume logic ran before Google Drive was mounted, so it could never find notebook_state.json after a restart.
**Cause:** The progress-tracker cell came before the drive.mount cell.
**Fix / next step:** Drive is now mounted in cell 1.2, before CONFIG and the state reload in 1.4.
<!-- END E-003 -->

<!-- BEGIN E-001 -->
## E-001
**Error ID:** E-001
**Date:** 2026-10-12
**Section:** 2
**Status:** SOLVED
**Description:** dataset_source_used could be undefined on a fresh runtime (NameError risk).
**Cause:** It was only assigned in one branch of the BIDS-root detection cell.
**Fix / next step:** Cell 2.3 assigns it before the search and in the success branch.
<!-- END E-001 -->

<!-- BEGIN E-002 -->
## E-002
**Error ID:** E-002
**Date:** 2026-10-12
**Section:** 3
**Status:** SOLVED
**Description:** Missing-data check reported 'Missing subjects: None' although recordings were missing.
**Cause:** Only whole subject folders were compared.
**Fix / next step:** Cell 3.5 checks every subject x session x task combination.
<!-- END E-002 -->

<!-- BEGIN E-004 -->
## E-004
**Error ID:** E-004
**Date:** 2026-10-12
**Section:** 3
**Status:** SOLVED
**Description:** has_events_tsv / has_channels_tsv could be True because of the NIRS sidecar, not the EEG one.
**Cause:** Substring matching on the recording stem matched files in both eeg/ and nirs/ folders.
**Fix / next step:** Cell 3.4 checks the exact file name inside the same eeg/ folder.
<!-- END E-004 -->

<!-- BEGIN E-005 -->
## E-005
**Error ID:** E-005
**Date:** 2026-10-12
**Section:** 5
**Status:** SOLVED
**Description:** Ratings located and joined: phenotype/cognitive_load.tsv (one 1-9 rating per subject x session x task); 514 EEG recordings have a rating.
**Cause:** The file name ('cognitive_load') did not match the first keyword search (fixed in 3.9).
**Fix / next step:** Use ratings_long.csv / rating_eeg_join.csv from here on.
<!-- END E-005 -->

<!-- BEGIN E-006 -->
## E-006
**Error ID:** E-006
**Date:** 2026-10-12
**Section:** 3
**Status:** OPEN
**Description:** 115 of 630 subject x session x task recordings are missing; the source dataset (OpenNeuro mirror) has the same 515 EDF files, so they cannot be recovered.
**Cause:** Recordings were not collected or not exported by the dataset authors.
**Fix / next step:** Decide subject/recording handling in Section 10 (fold design); never fill gaps.
<!-- END E-006 -->

<!-- BEGIN F-all_audited_recordings_250Hz -->
## F-all_audited_recordings_250Hz
**Error ID:** F-all_audited_recordings_250Hz
**Date:** 2026-10-12
**Section:** 3
**Status:** SOLVED
**Description:** Exact-equality sampling-rate flag replaced by a tolerance check.
**Cause:** eeg.json stores measured effective rates (249.9997-250.0031 Hz).
**Fix / next step:** See D-005.
<!-- END F-all_audited_recordings_250Hz -->

<!-- BEGIN E-008 -->
## E-008
**Error ID:** E-008
**Date:** 2026-10-12
**Section:** 3
**Status:** SOLVED
**Description:** 10 recordings have EEG sidecars but no EDF.
**Cause:** Verified against the OpenNeuro GitHub mirror OpenNeuroDatasets/ds007554: none of these 10 EDFs exist upstream; the mirror has the same 515 EDF files as this copy.
**Fix / next step:** Nothing to re-download; these recordings are treated as missing.
<!-- END E-008 -->

<!-- BEGIN F-all_recordings_have_sidecars -->
## F-all_recordings_have_sidecars
**Error ID:** F-all_recordings_have_sidecars
**Date:** 2026-10-12
**Section:** 3
**Status:** SOLVED
**Description:** Data flag 'all_recordings_have_sidecars' is OK.
**Cause:** Metadata audit (cell 3.10).
**Fix / next step:** No action needed.
<!-- END F-all_recordings_have_sidecars -->

<!-- BEGIN F-all_recordings_250Hz_within_tolerance -->
## F-all_recordings_250Hz_within_tolerance
**Error ID:** F-all_recordings_250Hz_within_tolerance
**Date:** 2026-10-12
**Section:** 3
**Status:** SOLVED
**Description:** Data flag 'all_recordings_250Hz_within_tolerance' is OK.
**Cause:** Metadata audit (cell 3.10).
**Fix / next step:** No action needed.
<!-- END F-all_recordings_250Hz_within_tolerance -->

<!-- BEGIN F-all_audited_recordings_32_eeg_channels -->
## F-all_audited_recordings_32_eeg_channels
**Error ID:** F-all_audited_recordings_32_eeg_channels
**Date:** 2026-10-12
**Section:** 3
**Status:** SOLVED
**Description:** Data flag 'all_audited_recordings_32_eeg_channels' is OK.
**Cause:** Metadata audit (cell 3.10).
**Fix / next step:** No action needed.
<!-- END F-all_audited_recordings_32_eeg_channels -->

<!-- BEGIN F-single_channel_order -->
## F-single_channel_order
**Error ID:** F-single_channel_order
**Date:** 2026-10-12
**Section:** 3
**Status:** SOLVED
**Description:** Data flag 'single_channel_order' is OK.
**Cause:** Metadata audit (cell 3.10).
**Fix / next step:** No action needed.
<!-- END F-single_channel_order -->

<!-- BEGIN F-eeg_units_uV_only -->
## F-eeg_units_uV_only
**Error ID:** F-eeg_units_uV_only
**Date:** 2026-10-12
**Section:** 3
**Status:** SOLVED
**Description:** Data flag 'eeg_units_uV_only' is OK.
**Cause:** Metadata audit (cell 3.10).
**Fix / next step:** No action needed.
<!-- END F-eeg_units_uV_only -->

<!-- BEGIN F-no_orphan_eeg_sidecars -->
## F-no_orphan_eeg_sidecars
**Error ID:** F-no_orphan_eeg_sidecars
**Date:** 2026-10-12
**Section:** 3
**Status:** SOLVED
**Description:** Orphan sidecars explained.
**Cause:** Absent in source dataset.
**Fix / next step:** See E-008.
<!-- END F-no_orphan_eeg_sidecars -->

<!-- BEGIN E-007 -->
## E-007
**Error ID:** E-007
**Date:** 2026-10-12
**Section:** 4
**Status:** SOLVED
**Description:** Storage estimate 3.56 GB fits in 11.72 GB free.
**Cause:** Storage check.
**Fix / next step:** No action needed.
<!-- END E-007 -->

<!-- BEGIN F4-edf_sfreq_within_tolerance -->
## F4-edf_sfreq_within_tolerance
**Error ID:** F4-edf_sfreq_within_tolerance
**Date:** 2026-10-12
**Section:** 4
**Status:** SOLVED
**Description:** Section 4 data flag 'edf_sfreq_within_tolerance' is OK.
**Cause:** Single-recording audit of sub-001_ses-01_task-nback.
**Fix / next step:** No action needed.
<!-- END F4-edf_sfreq_within_tolerance -->

<!-- BEGIN F4-edf_sfreq_exactly_nominal -->
## F4-edf_sfreq_exactly_nominal
**Error ID:** F4-edf_sfreq_exactly_nominal
**Date:** 2026-10-12
**Section:** 4
**Status:** SOLVED
**Description:** EDF sfreq is 250.001 Hz.
**Cause:** Measured rate.
**Fix / next step:** See D-008.
<!-- END F4-edf_sfreq_exactly_nominal -->

<!-- BEGIN F4-duration_matches_eeg_json -->
## F4-duration_matches_eeg_json
**Error ID:** F4-duration_matches_eeg_json
**Date:** 2026-10-12
**Section:** 4
**Status:** SOLVED
**Description:** Section 4 data flag 'duration_matches_eeg_json' is OK.
**Cause:** Single-recording audit of sub-001_ses-01_task-nback.
**Fix / next step:** No action needed.
<!-- END F4-duration_matches_eeg_json -->

<!-- BEGIN F4-edf_units_microvolt -->
## F4-edf_units_microvolt
**Error ID:** F4-edf_units_microvolt
**Date:** 2026-10-12
**Section:** 4
**Status:** SOLVED
**Description:** Section 4 data flag 'edf_units_microvolt' is OK.
**Cause:** Single-recording audit of sub-001_ses-01_task-nback.
**Fix / next step:** No action needed.
<!-- END F4-edf_units_microvolt -->

<!-- BEGIN F4-amplitude_plausible_1_to_100uV -->
## F4-amplitude_plausible_1_to_100uV
**Error ID:** F4-amplitude_plausible_1_to_100uV
**Date:** 2026-10-12
**Section:** 4
**Status:** SOLVED
**Description:** Section 4 data flag 'amplitude_plausible_1_to_100uV' is OK.
**Cause:** Single-recording audit of sub-001_ses-01_task-nback.
**Fix / next step:** No action needed.
<!-- END F4-amplitude_plausible_1_to_100uV -->

<!-- BEGIN F4-events_inside_recording -->
## F4-events_inside_recording
**Error ID:** F4-events_inside_recording
**Date:** 2026-10-12
**Section:** 4
**Status:** SOLVED
**Description:** Section 4 data flag 'events_inside_recording' is OK.
**Cause:** Single-recording audit of sub-001_ses-01_task-nback.
**Fix / next step:** No action needed.
<!-- END F4-events_inside_recording -->

<!-- BEGIN F4-line_noise_below_threshold -->
## F4-line_noise_below_threshold
**Error ID:** F4-line_noise_below_threshold
**Date:** 2026-10-12
**Section:** 4
**Status:** SOLVED
**Description:** Section 4 data flag 'line_noise_below_threshold' is OK.
**Cause:** Single-recording audit of sub-001_ses-01_task-nback.
**Fix / next step:** No action needed.
<!-- END F4-line_noise_below_threshold -->

<!-- BEGIN F4-no_bad_channel_candidates -->
## F4-no_bad_channel_candidates
**Error ID:** F4-no_bad_channel_candidates
**Date:** 2026-10-12
**Section:** 4
**Status:** SOLVED
**Description:** FP1/FP2 flagged by variance only.
**Cause:** Eye blinks.
**Fix / next step:** See D-009.
<!-- END F4-no_bad_channel_candidates -->

<!-- BEGIN F4-mne_bids_reader_works -->
## F4-mne_bids_reader_works
**Error ID:** F4-mne_bids_reader_works
**Date:** 2026-10-12
**Section:** 4
**Status:** SOLVED
**Description:** Section 4 data flag 'mne_bids_reader_works' is OK.
**Cause:** Single-recording audit of sub-001_ses-01_task-nback.
**Fix / next step:** No action needed.
<!-- END F4-mne_bids_reader_works -->

<!-- BEGIN E-010 -->
## E-010
**Error ID:** E-010
**Date:** 2026-10-12
**Section:** 8
**Status:** OPEN
**Description:** Stimulus-locked activity is task-specific: real-peak/random-onset ratio for N-back (np.float64(1.93), np.float64(1.38)) (frontal max, other median) vs ~1.0 for the other tasks (demo subjects). No stimulus-rate spectral comb in clean data.
**Cause:** N-back has 120 stimuli at 1.5 s; averaged auditory responses / stimulus-locked eye activity.
**Fix / next step:** N2: task decoding from stimulus-locked features; report with TCAI (N1).
<!-- END E-010 -->

<!-- BEGIN E-011 -->
## E-011
**Error ID:** E-011
**Date:** 2026-10-12
**Section:** 5
**Status:** OPEN
**Description:** sub-011 / ses-01 / task-passivemotor has EEG but no rating.
**Cause:** n/a in cognitive_load.tsv.
**Fix / next step:** Excluded from supervised training; still usable for unsupervised checks.
<!-- END E-011 -->

<!-- BEGIN F5-every_eeg_recording_has_rating -->
## F5-every_eeg_recording_has_rating
**Error ID:** F5-every_eeg_recording_has_rating
**Date:** 2026-10-12
**Section:** 5
**Status:** SOLVED
**Description:** One EEG recording has no rating.
**Cause:** See E-011.
**Fix / next step:** See E-011.
<!-- END F5-every_eeg_recording_has_rating -->

<!-- BEGIN F5-no_non_numeric_ratings -->
## F5-no_non_numeric_ratings
**Error ID:** F5-no_non_numeric_ratings
**Date:** 2026-10-12
**Section:** 5
**Status:** SOLVED
**Description:** Section 5 data flag 'no_non_numeric_ratings' is OK.
**Cause:** Rating audit.
**Fix / next step:** No action needed.
<!-- END F5-no_non_numeric_ratings -->

<!-- BEGIN F5-full_column_is_a_task_rating -->
## F5-full_column_is_a_task_rating
**Error ID:** F5-full_column_is_a_task_rating
**Date:** 2026-10-12
**Section:** 5
**Status:** SOLVED
**Description:** Section 5 data flag 'full_column_is_a_task_rating' is OK.
**Cause:** Rating audit.
**Fix / next step:** No action needed.
<!-- END F5-full_column_is_a_task_rating -->

<!-- BEGIN F5-S1_task_confound_below_limit -->
## F5-S1_task_confound_below_limit
**Error ID:** F5-S1_task_confound_below_limit
**Date:** 2026-10-12
**Section:** 5
**Status:** SOLVED
**Description:** F5-S1_task_confound_below_limit reviewed.
**Cause:** Rating is mostly determined by task.
**Fix / next step:** Handled by D-013 controls and D-015.
<!-- END F5-S1_task_confound_below_limit -->

<!-- BEGIN F5-S1_no_class_below_min_share -->
## F5-S1_no_class_below_min_share
**Error ID:** F5-S1_no_class_below_min_share
**Date:** 2026-10-12
**Section:** 5
**Status:** SOLVED
**Description:** Section 5 data flag 'S1_no_class_below_min_share' is OK.
**Cause:** Rating audit.
**Fix / next step:** No action needed.
<!-- END F5-S1_no_class_below_min_share -->

<!-- BEGIN F5-task_explains_less_than_half_of_rating -->
## F5-task_explains_less_than_half_of_rating
**Error ID:** F5-task_explains_less_than_half_of_rating
**Date:** 2026-10-12
**Section:** 5
**Status:** SOLVED
**Description:** F5-task_explains_less_than_half_of_rating reviewed.
**Cause:** Rating is mostly determined by task.
**Fix / next step:** Handled by D-013 controls and D-015.
<!-- END F5-task_explains_less_than_half_of_rating -->

<!-- BEGIN E-012 -->
## E-012
**Error ID:** E-012
**Date:** 2026-10-12
**Section:** 5
**Status:** SOLVED
**Description:** Full column could be a composite score.
**Cause:** json description.
**Fix / next step:** Ruled out in 5.5 (D-014).
<!-- END E-012 -->

<!-- BEGIN F6-status_ok -->
## F6-status_ok
**Error ID:** F6-status_ok
**Date:** 2026-10-12
**Section:** 6
**Status:** SOLVED
**Description:** Section 6 data flag 'status_ok' is OK.
**Cause:** Minimal preprocessing of sub-001_ses-01_task-nback.
**Fix / next step:** No action needed.
<!-- END F6-status_ok -->

<!-- BEGIN F6-no_bad_channels -->
## F6-no_bad_channels
**Error ID:** F6-no_bad_channels
**Date:** 2026-10-12
**Section:** 6
**Status:** SOLVED
**Description:** Section 6 data flag 'no_bad_channels' is OK.
**Cause:** Minimal preprocessing of sub-001_ses-01_task-nback.
**Fix / next step:** No action needed.
<!-- END F6-no_bad_channels -->

<!-- BEGIN F6-task_period_mostly_clean -->
## F6-task_period_mostly_clean
**Error ID:** F6-task_period_mostly_clean
**Date:** 2026-10-12
**Section:** 6
**Status:** SOLVED
**Description:** Section 6 data flag 'task_period_mostly_clean' is OK.
**Cause:** Minimal preprocessing of sub-001_ses-01_task-nback.
**Fix / next step:** No action needed.
<!-- END F6-task_period_mostly_clean -->

<!-- BEGIN F6-residual_50Hz_below_threshold -->
## F6-residual_50Hz_below_threshold
**Error ID:** F6-residual_50Hz_below_threshold
**Date:** 2026-10-12
**Section:** 6
**Status:** SOLVED
**Description:** Section 6 data flag 'residual_50Hz_below_threshold' is OK.
**Cause:** Minimal preprocessing of sub-001_ses-01_task-nback.
**Fix / next step:** No action needed.
<!-- END F6-residual_50Hz_below_threshold -->

<!-- BEGIN F6-alpha_band_preserved -->
## F6-alpha_band_preserved
**Error ID:** F6-alpha_band_preserved
**Date:** 2026-10-12
**Section:** 6
**Status:** SOLVED
**Description:** Alpha 'loss' was raw spectral leakage.
**Cause:** DC offsets + drift.
**Fix / next step:** Cell 6.7 compares against a 0.1 Hz high-passed copy.
<!-- END F6-alpha_band_preserved -->

<!-- BEGIN F6-no_strong_stimulus_comb -->
## F6-no_strong_stimulus_comb
**Error ID:** F6-no_strong_stimulus_comb
**Date:** 2026-10-12
**Section:** 6
**Status:** SOLVED
**Description:** Section 6 data flag 'no_strong_stimulus_comb' is OK.
**Cause:** Minimal preprocessing of sub-001_ses-01_task-nback.
**Fix / next step:** No action needed.
<!-- END F6-no_strong_stimulus_comb -->

<!-- BEGIN F7-ica_converged -->
## F7-ica_converged
**Error ID:** F7-ica_converged
**Date:** 2026-10-12
**Section:** 7
**Status:** SOLVED
**Description:** Section 7 data flag 'ica_converged' is OK.
**Cause:** ICA on sub-001_ses-01_task-nback.
**Fix / next step:** No action needed.
<!-- END F7-ica_converged -->

<!-- BEGIN F7-eye_component_found -->
## F7-eye_component_found
**Error ID:** F7-eye_component_found
**Date:** 2026-10-12
**Section:** 7
**Status:** SOLVED
**Description:** Section 7 data flag 'eye_component_found' is OK.
**Cause:** ICA on sub-001_ses-01_task-nback.
**Fix / next step:** No action needed.
<!-- END F7-eye_component_found -->

<!-- BEGIN F7-ecg_available -->
## F7-ecg_available
**Error ID:** F7-ecg_available
**Date:** 2026-10-12
**Section:** 7
**Status:** SOLVED
**Description:** Section 7 data flag 'ecg_available' is OK.
**Cause:** ICA on sub-001_ses-01_task-nback.
**Fix / next step:** No action needed.
<!-- END F7-ecg_available -->

<!-- BEGIN F7-heart_component_found -->
## F7-heart_component_found
**Error ID:** F7-heart_component_found
**Date:** 2026-10-12
**Section:** 7
**Status:** SOLVED
**Description:** No heart component.
**Cause:** See D-020.
**Fix / next step:** ICA eye-only.
<!-- END F7-heart_component_found -->

<!-- BEGIN F7-pulse_plausible_40_120bpm -->
## F7-pulse_plausible_40_120bpm
**Error ID:** F7-pulse_plausible_40_120bpm
**Date:** 2026-10-12
**Section:** 7
**Status:** SOLVED
**Description:** Section 7 data flag 'pulse_plausible_40_120bpm' is OK.
**Cause:** ICA on sub-001_ses-01_task-nback.
**Fix / next step:** No action needed.
<!-- END F7-pulse_plausible_40_120bpm -->

<!-- BEGIN F7-ecg_alignment_lag_below_0.1s -->
## F7-ecg_alignment_lag_below_0.1s
**Error ID:** F7-ecg_alignment_lag_below_0.1s
**Date:** 2026-10-12
**Section:** 7
**Status:** SOLVED
**Description:** ECG alignment unverified.
**Cause:** Separate device clocks.
**Fix / next step:** See D-020.
<!-- END F7-ecg_alignment_lag_below_0.1s -->

<!-- BEGIN F7-not_capped -->
## F7-not_capped
**Error ID:** F7-not_capped
**Date:** 2026-10-12
**Section:** 7
**Status:** SOLVED
**Description:** Section 7 data flag 'not_capped' is OK.
**Cause:** ICA on sub-001_ses-01_task-nback.
**Fix / next step:** No action needed.
<!-- END F7-not_capped -->

<!-- BEGIN F7-non_frontal_change_below_20pct -->
## F7-non_frontal_change_below_20pct
**Error ID:** F7-non_frontal_change_below_20pct
**Date:** 2026-10-12
**Section:** 7
**Status:** SOLVED
**Description:** ICA changed non-frontal channels by a median of ~44 %.
**Cause:** Average reference spreads frontal blinks to every channel (visible at Cz/Pz/Oz in 7.7).
**Fix / next step:** Expected for eye-only ICA after CAR; supports running the ICA sensitivity analysis.
<!-- END F7-non_frontal_change_below_20pct -->

<!-- BEGIN F8-all_recordings_have_anchor -->
## F8-all_recordings_have_anchor
**Error ID:** F8-all_recordings_have_anchor
**Date:** 2026-10-12
**Section:** 8
**Status:** SOLVED
**Description:** Section 8 data flag 'all_recordings_have_anchor' is OK.
**Cause:** Window generation.
**Fix / next step:** No action needed.
<!-- END F8-all_recordings_have_anchor -->

<!-- BEGIN F8-all_full_recordings_have_expected_windows -->
## F8-all_full_recordings_have_expected_windows
**Error ID:** F8-all_full_recordings_have_expected_windows
**Date:** 2026-10-12
**Section:** 8
**Status:** SOLVED
**Description:** Section 8 data flag 'all_full_recordings_have_expected_windows' is OK.
**Cause:** Window generation.
**Fix / next step:** No action needed.
<!-- END F8-all_full_recordings_have_expected_windows -->

<!-- BEGIN F8-demo_all_preprocessed -->
## F8-demo_all_preprocessed
**Error ID:** F8-demo_all_preprocessed
**Date:** 2026-10-12
**Section:** 8
**Status:** SOLVED
**Description:** Section 8 data flag 'demo_all_preprocessed' is OK.
**Cause:** Window generation.
**Fix / next step:** No action needed.
<!-- END F8-demo_all_preprocessed -->

<!-- BEGIN F8-demo_rejected_windows_below_5pct -->
## F8-demo_rejected_windows_below_5pct
**Error ID:** F8-demo_rejected_windows_below_5pct
**Date:** 2026-10-12
**Section:** 8
**Status:** SOLVED
**Description:** Section 8 data flag 'demo_rejected_windows_below_5pct' is OK.
**Cause:** Window generation.
**Fix / next step:** No action needed.
<!-- END F8-demo_rejected_windows_below_5pct -->

<!-- BEGIN F8-no_estimated_anchors -->
## F8-no_estimated_anchors
**Error ID:** F8-no_estimated_anchors
**Date:** 2026-10-12
**Section:** 8
**Status:** SOLVED
**Description:** Motor-imagery anchor.
**Cause:** No 'start' event in motor imagery.
**Fix / next step:** Protocol-constant start used and validated (D-021 rev.).
<!-- END F8-no_estimated_anchors -->

<!-- BEGIN F8-protocol_constant_start -->
## F8-protocol_constant_start
**Error ID:** F8-protocol_constant_start
**Date:** 2026-10-12
**Section:** 8
**Status:** SOLVED
**Description:** Section 8 data flag 'protocol_constant_start' is OK.
**Cause:** Window generation.
**Fix / next step:** No action needed.
<!-- END F8-protocol_constant_start -->

<!-- BEGIN E-013 -->
## E-013
**Error ID:** E-013
**Date:** 2026-10-12
**Section:** 11
**Status:** SOLVED
**Description:** Amplitude-flagged subjects: ['sub-009', 'sub-010', 'sub-011', 'sub-012', 'sub-013']; judged not usable EEG by the pre-registered rule: none.
**Cause:** Five consecutive subjects recorded ~14x lower amplitude (one recording period/setup); EDF headers normal.
**Fix / next step:** Kept: their EEG is real but scaled; 'recording_scaled' normalisation removes the amplitude difference. Both normalisation modes are stored.
<!-- END E-013 -->

<!-- BEGIN E-014 -->
## E-014
**Error ID:** E-014
**Date:** 2026-10-12
**Section:** 13
**Status:** OPEN
**Description:** Temporal CNN collapses to one class for 8 held-out subjects (5 of them low-amplitude, E-013); pooled balanced accuracy near chance.
**Cause:** Large between-subject differences (amplitude, spectrum) under train_global normalisation; weak cross-subject workload signal.
**Fix / next step:** Pre-registered sensitivity: recording_scaled normalisation (Section 24). Subject-adversarial training (Section 19) targets the subject shift directly. No change based on test scores.
<!-- END E-014 -->
