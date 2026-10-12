<!-- CMx7-SI-DyGraph log v1 -->
# PROJECT_STATE — CMx7-SI-DyGraph

<!-- BEGIN SECTION 01 -->
## Section 1
**Phase:** Phase 1 (Notebook Section 1)
**Status:** Completed (pending your real output)
**Date:** 2026-10-12
**Objective:** Colab environment, Drive project structure, logs and CONFIG.
**Completed tasks:**
  - Drive mounted
  - CONFIG defined
  - State reload after mount
  - 13 project folders
  - PROJECT_STATE/DECISION_LOG/ERROR_LOG/EXPERIMENT_LOG initialised
  - Packages + hardware recorded
**Files created:**
  - /content/drive/MyDrive/CMx7_SI_DyGraph/configs/preprocessing_config.json
  - /content/drive/MyDrive/CMx7_SI_DyGraph/logs/environment_report.json
  - /content/drive/MyDrive/CMx7_SI_DyGraph/PROJECT_STATE.md
  - /content/drive/MyDrive/CMx7_SI_DyGraph/DECISION_LOG.md
  - /content/drive/MyDrive/CMx7_SI_DyGraph/ERROR_LOG.md
  - /content/drive/MyDrive/CMx7_SI_DyGraph/EXPERIMENT_LOG.csv
**Outputs checked:**
  - Package versions
  - GPU/RAM/disk
  - read/write test
**Sanity checks passed:**
  - drive_mounted
  - readwrite_ok
  - project_root_outside_raw_data
  - all_folders_exist
  - all_logs_exist
**Errors found:**
  - E-003
**Errors solved:**
  - E-003
**Open problems:**
  - Demo subset (CMx7_MM_Demo) not created yet -- needed before Section 6
**Scientific decisions:**
  - D-001
  - D-002
  - D-003
  - D-004
**Next required input:** Printed output of Section 1
**Next phase:** Phase 2 / Sections 2-3: BIDS discovery and metadata audit
<!-- END SECTION 01 -->

<!-- BEGIN SECTION 02 -->
## Section 2
**Phase:** Phase 2 (Notebook Section 2)
**Status:** Completed (pending your real output)
**Date:** 2026-10-12
**Objective:** Locate BIDS root and count files without loading EEG.
**Completed tasks:**
  - BIDS root located
  - Shallow tree printed
  - Scan cached (version 2)
  - Counts recorded
**Files created:**
  - /content/drive/MyDrive/CMx7_SI_DyGraph/metadata/dataset_discovery_summary.json
  - /content/drive/MyDrive/CMx7_SI_DyGraph/reports/bids_tree_shallow.txt
  - /content/drive/MyDrive/CMx7_SI_DyGraph/cache/bids_scan_cache.json
**Outputs checked:**
  - Subject/session/task counts
  - EEG/sidecar/physio counts
  - Rating candidates
**Sanity checks passed:**
  - bids_root_found
  - dataset_description_exists
  - eeg_files_found
  - subject_count_matches
  - session_count_matches
  - task_count_matches
  - project_root_outside_bids_root
**Errors found:**
  - E-001
**Errors solved:**
  - E-001
**Open problems:**
  - Ratings source unknown (checked in Section 3)
**Scientific decisions:**
  - D-003
  - D-004
**Next required input:** Printed output of Section 2
**Next phase:** Section 3: BIDS metadata audit
<!-- END SECTION 02 -->

<!-- BEGIN SECTION 03 -->
## Section 3
**Phase:** Phase 2 (Notebook Section 3)
**Status:** Completed (pending your real output)
**Date:** 2026-10-12
**Objective:** Audit all BIDS metadata without loading EEG signal.
**Completed tasks:**
  - participants profile
  - exact-match recording inventory
  - subject x session x task completeness
  - physio inventory
  - sidecar audit of every recording
  - channel-order check
  - rating search
**Files created:**
  - /content/drive/MyDrive/CMx7_SI_DyGraph/metadata/recording_inventory.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/metadata/missing_data_report.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/metadata/completeness_matrix.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/metadata/physio_inventory.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/metadata/participants_profile.json
  - /content/drive/MyDrive/CMx7_SI_DyGraph/metadata/reference_channel_order.json
  - /content/drive/MyDrive/CMx7_SI_DyGraph/metadata/rating_evidence.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/metadata/orphan_eeg_sidecars.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/reports/bids_audit_report.md
  - /content/drive/MyDrive/CMx7_SI_DyGraph/derivatives/quality_control/eeg_sidecar_audit.csv
**Outputs checked:**
  - sfreq
  - line frequency
  - channel count/order/units
  - trial_type values
  - durations
  - rating evidence
**Sanity checks passed:**
  - inventory_rows_equal_eeg_files
  - no_duplicate_recordings
  - inventory_subjects_in_participants_tsv
  - completeness_adds_up
  - sidecar_audit_has_rows
**Errors found:**
  - E-002
  - E-004
  - E-005
  - E-006
**Errors solved:**
  - E-002
  - E-004
**Open problems:**
  - E-005 ratings not confirmed
  - no_missing_recordings
  - no_orphan_eeg_sidecars
**Scientific decisions:**
  - D-003
**Next required input:** Printed output of Section 3 + where the ratings are (if not found)
**Next phase:** Phase 3 / Section 4: single-recording raw EEG signal audit
<!-- END SECTION 03 -->

<!-- BEGIN SECTION 04 -->
## Section 4
**Phase:** Phase 3 (Notebook Section 4)
**Status:** Completed and reviewed
**Date:** 2026-10-12
**Objective:** Check one raw EEG recording against its metadata and screen signal quality.
**Completed tasks:**
  - EDF header vs metadata
  - 32 channels in reference order
  - events
  - raw plot
  - PSD + line noise
  - channel QC
  - mne-bids reader OK
  - storage estimate
  - review decisions D-008..D-011
**Files created:**
  - /content/drive/MyDrive/CMx7_SI_DyGraph/derivatives/quality_control/sec4_sub-001_ses-01_task-nback_qc_summary.json
  - /content/drive/MyDrive/CMx7_SI_DyGraph/derivatives/quality_control/sec4_sub-001_ses-01_task-nback_channel_qc.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/derivatives/quality_control/sec4_sub-001_ses-01_task-nback_events_summary.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/sec4_sub-001_ses-01_task-nback_raw_segment.png
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/sec4_sub-001_ses-01_task-nback_psd.png
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/sec4_sub-001_ses-01_task-nback_channel_std.png
**Outputs checked:**
  - sfreq 250.001 Hz
  - units µV
  - duration
  - events start/target/trigger
  - 50 Hz small
  - FP1/FP2 blinks
  - stimulus-rhythm comb
**Sanity checks passed:**
  - array_shape_is_32_x_samples
  - channel_order_equals_reference
  - all_values_finite
  - qc_table_has_all_channels
  - segment_inside_recording
**Errors found:**
  - E-007 storage
  - E-010 stimulus-rhythm shortcut risk
**Errors solved:**
  - E-008
  - F4 flags explained
**Open problems:**
  - E-007 storage (3.56 GB needed vs 2.36 GB free)
  - E-010 task-rhythm shortcut risk
  - E-006 missing recordings
**Scientific decisions:**
  - D-006
  - D-007
  - D-008
  - D-009
  - D-010
  - D-011
**Next required input:** Printed output of Section 5
**Next phase:** Phase 4 / Section 5: subjective workload rating audit
<!-- END SECTION 04 -->

<!-- BEGIN SECTION 05 -->
## Section 5
**Phase:** Phase 4 (Notebook Section 5)
**Status:** Completed and reviewed -- label strategy chosen (D-013)
**Date:** 2026-10-12
**Objective:** Audit subjective workload ratings and choose the label strategy.
**Completed tasks:**
  - rating audit
  - label strategy D-013
  - Full column D-014
  - N3 framing D-015
**Files created:**
  - /content/drive/MyDrive/CMx7_SI_DyGraph/metadata/ratings_long.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/metadata/rating_eeg_join.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec5_label_strategy_comparison.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec5_loso_tertile_thresholds.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec5_rating_variance_explained.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/reports/sec5_rating_audit_summary.json
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/sec5_rating_distribution.png
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/sec5_rating_heatmap.png
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/sec5_label_strategies_by_task.png
**Outputs checked:**
  - 514/515 EEG recordings rated
  - task R2 0.765
  - subject R2 0.066
  - Cramér's V 0.67-0.83
**Sanity checks passed:**
  - long_rows_equal_wide_cells
  - no_duplicate_subject_session_task
  - all_tasks_mapped
  - ratings_inside_scale
  - join_counts_add_up
  - every_strategy_labels_every_recording
**Errors found:**
  - E-011
**Errors solved:**
  - E-005
  - E-012
**Open problems:**
  - E-011 one unrated recording
  - KSS (sleepiness) rises over sessions {'ses-01': 3.48, 'ses-02': 4.47, 'ses-03': 5.27} -- relevant for cross-session evaluation
**Scientific decisions:**
  - D-012
  - D-013
  - D-014
  - D-015
**Next required input:** Printed output of Sections 6 and 7
**Next phase:** Phase 5 / Sections 6-7: minimal preprocessing + ICA sensitivity pipeline
<!-- END SECTION 05 -->

<!-- BEGIN SECTION 06 -->
## Section 6
**Phase:** Phase 5 (Notebook Section 6)
**Status:** Completed (pending your real output)
**Date:** 2026-10-12
**Objective:** Minimal preprocessing of one recording with reusable functions.
**Completed tasks:**
  - load_eeg_recording
  - detect_bad_channels
  - annotate_artifacts
  - preprocess_minimal
  - before/after
  - stimulus-rhythm check
**Files created:**
  - /content/drive/MyDrive/CMx7_SI_DyGraph/derivatives/minimal/sub-001_ses-01_task-nback_desc-minimal_eeg.fif
  - /content/drive/MyDrive/CMx7_SI_DyGraph/derivatives/quality_control/sec6_sub-001_ses-01_task-nback_minimal_report.json
  - /content/drive/MyDrive/CMx7_SI_DyGraph/derivatives/quality_control/sec6_sub-001_ses-01_task-nback_bad_channel_qc.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/sec6_sub-001_ses-01_task-nback_before_after_segment.png
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/sec6_sub-001_ses-01_task-nback_before_after_psd.png
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/sec6_sub-001_ses-01_task-nback_stimulus_rhythm.png
**Outputs checked:**
  - bad channels
  - interpolation
  - power change
  - residual 50 Hz
  - comb
  - stimulus-locked average
**Sanity checks passed:**
  - 32_channels_in_reference_order
  - sfreq_unchanged
  - all_values_finite
  - average_reference_applied
  - interpolated_within_limit
  - dc_offset_removed
  - high_frequencies_removed
  - annotations_inside_recording
**Errors found:** None
**Errors solved:** None
**Open problems:**
  - E-007 storage before batch run
**Scientific decisions:**
  - D-016
  - D-017
**Next required input:** Printed output and figures of Sections 6 and 7
**Next phase:** Section 7: ICA sensitivity pipeline
<!-- END SECTION 06 -->

<!-- BEGIN SECTION 07 -->
## Section 7
**Phase:** Phase 5 (Notebook Section 7)
**Status:** Completed and reviewed
**Date:** 2026-10-12
**Objective:** ICA sensitivity version of the audit recording.
**Completed tasks:**
  - eye components removed
  - heart removal rejected (D-020)
  - novelties D-019 adopted
**Files created:**
  - /content/drive/MyDrive/CMx7_SI_DyGraph/derivatives/ica_cleaned/sub-001_ses-01_task-nback_desc-ica_eeg.fif
  - /content/drive/MyDrive/CMx7_SI_DyGraph/derivatives/ica_cleaned/sub-001_ses-01_task-nback_ica.fif
  - /content/drive/MyDrive/CMx7_SI_DyGraph/derivatives/quality_control/sec7_sub-001_ses-01_task-nback_ica_excluded_components.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/derivatives/quality_control/sec7_sub-001_ses-01_task-nback_ica_variance_removed.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/derivatives/quality_control/sec7_sub-001_ses-01_task-nback_ica_report.json
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/sec7_sub-001_ses-01_task-nback_removed_components.png
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/sec7_sub-001_ses-01_task-nback_raw_minimal_ica.png
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/sec7_sub-001_ses-01_task-nback_variance_removed.png
**Outputs checked:**
  - eye components
  - ECG alignment
  - variance removed (good samples)
**Sanity checks passed:**
  - same_shape_as_minimal
  - same_channels_and_order
  - all_values_finite
  - excluded_within_cap
  - every_exclusion_has_a_reason
  - minimal_stays_primary
**Errors found:**
  - E-010 revised
**Errors solved:**
  - F6/F7 flags explained
**Open problems:**
  - E-006 missing recordings
  - E-010 stimulus-locked activity
  - E-007 Drive storage
  - E-011 unrated recording
**Scientific decisions:**
  - D-019
  - D-020
**Next required input:** Printed output of Section 8
**Next phase:** Phase 6 / Section 8: window generation
<!-- END SECTION 07 -->

<!-- BEGIN SECTION 08 -->
## Section 8
**Phase:** Phase 6 (Notebook Section 8)
**Status:** Completed (pending your real output)
**Date:** 2026-10-12
**Objective:** Leakage-safe window metadata for all recordings; demo subset preprocessed with signal checks.
**Completed tasks:**
  - event timing audit
  - anchor rule (D-021)
  - window metadata (rating, no label)
  - demo preprocessing
  - BAD_ overlap rejection
  - alignment check
  - stimulus-locked QC
**Files created:**
  - /content/drive/MyDrive/CMx7_SI_DyGraph/derivatives/window_metadata/windows_all_recordings.parquet
  - /content/drive/MyDrive/CMx7_SI_DyGraph/derivatives/window_metadata/windows_demo.parquet
  - /content/drive/MyDrive/CMx7_SI_DyGraph/metadata/event_timing_with_anchor.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/derivatives/quality_control/sec8_demo_recording_qc.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/derivatives/quality_control/sec8_demo_stimulus_locked.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec8_stimulus_locked_summary.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/sec8_example_window.png
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/sec8_stimulus_locked_by_task.png
**Outputs checked:**
  - windows per recording
  - anchors
  - demo QC
  - alignment
  - stimulus-locked amplitude per task
**Sanity checks passed:**
  - no_label_column_written
  - window_ids_unique
  - fixed_window_length
  - windows_inside_task_period
  - windows_inside_recording
  - one_subject_per_recording
  - every_window_recording_in_inventory
  - no_more_than_expected_per_recording
  - alignment_shapes_ok
  - alignment_values_ok
**Errors found:** None
**Errors solved:** None
**Open problems:**
  - E-007 storage before full run
  - E-010 stimulus-locked activity
**Scientific decisions:**
  - D-021
  - D-022
**Next required input:** Printed output and two figures of Section 8
**Next phase:** Section 9: processed-data storage (continuous float32 + window index, lazy loading)
<!-- END SECTION 08 -->

<!-- BEGIN SECTION 09 -->
## Section 9
**Phase:** Phase 6 (Notebook Section 9)
**Status:** Completed (pending your real output) -- full build not yet run
**Date:** 2026-10-12
**Objective:** Choose a memory-efficient storage format, build the store, test lazy loading.
**Completed tasks:**
  - format benchmark
  - rule-based choice
  - demo store
  - window table with offsets
  - lazy-loading test
  - storage projection
  - resumable full build (guarded)
**Files created:**
  - /content/drive/MyDrive/CMx7_SI_DyGraph/derivatives/window_metadata/store_index.parquet
  - /content/drive/MyDrive/CMx7_SI_DyGraph/derivatives/window_metadata/windows_store.parquet
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec9_storage_benchmark.csv
**Outputs checked:**
  - format sizes/speeds
  - exactness
  - lazy read speed
  - storage projection
**Sanity checks passed:**
  - chosen_format_is_exact_and_lazy
  - every_demo_recording_stored
  - array_shapes_match_index
  - offsets_inside_arrays
  - lazy_windows_match_fif
  - lazy_batch_shape
  - no_normalisation_applied
  - no_label_column
**Errors found:**
  - lazy_read_below_20ms_per_window
  - full_store_built
**Errors solved:** None
**Open problems:**
  - lazy_read_below_20ms_per_window
  - full_store_built
  - E-012 amplitude outliers (if any)
**Scientific decisions:**
  - D-023
**Next required input:** Printed output of 8.4, 8.11 and Section 9; then run the full build
**Next phase:** Section 10: leakage-free subject splits (LOSO folds)
<!-- END SECTION 09 -->

<!-- BEGIN SECTION 10 -->
## Section 10
**Phase:** Phase 7 (Notebook Section 10)
**Status:** Completed (pending your real output)
**Date:** 2026-10-12
**Objective:** Leakage-free LOSO and cross-session splits with training-only label thresholds.
**Completed tasks:**
  - recording table
  - LOSO folds
  - cross-session folds
  - training-only thresholds
  - task-only reference
  - leakage proofs incl. perturbation test
**Files created:**
  - /content/drive/MyDrive/CMx7_SI_DyGraph/metadata/folds/folds_recordings.parquet
  - /content/drive/MyDrive/CMx7_SI_DyGraph/metadata/folds/fold_label_thresholds.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/metadata/folds/fold_summary.json
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec10_task_only_reference.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/sec10_folds_and_task_only.png
**Outputs checked:**
  - fold composition
  - threshold values
  - task-only reference
**Sanity checks passed:**
  - loso_every_subject_tested_once
  - loso_subjects_disjoint
  - loso_val_size
  - loso_each_subject_val_n_times
  - every_labelled_recording_once_per_fold
  - no_recording_in_two_splits
  - cross_session_test_is_one_session
  - cross_session_train_val_subjects_disjoint
  - thresholds_from_training_only
  - unlabelled_recordings_excluded
  - labels_in_0_1_2
  - no_label_in_window_table
**Errors found:** None
**Errors solved:** None
**Open problems:**
  - E-013 subject amplitude
**Scientific decisions:**
  - D-024
  - D-025
**Next required input:** Printed output of 9.12 and Section 10 + both figures
**Next phase:** Section 11: training-only normalisation (and the E-013 amplitude decision)
<!-- END SECTION 10 -->

<!-- BEGIN SECTION 11 -->
## Section 11
**Phase:** Phase 7 (Notebook Section 11)
**Status:** Completed (pending your real output)
**Date:** 2026-10-12
**Objective:** Training-only normalisation and the E-013 decision.
**Completed tasks:**
  - label-free recording summaries
  - E-013 diagnosis with fixed rule
  - folds per subject set
  - fold statistics (2 modes)
  - exact + perturbation + window checks
**Files created:**
  - /content/drive/MyDrive/CMx7_SI_DyGraph/derivatives/normalization/recording_stats.parquet
  - /content/drive/MyDrive/CMx7_SI_DyGraph/metadata/folds/folds_recordings_by_subject_set.parquet
  - /content/drive/MyDrive/CMx7_SI_DyGraph/derivatives/normalization/fold_norm_summary.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/derivatives/normalization/recording_scales.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec11_e013_subject_diagnosis.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/sec11_e013_signal_diagnosis.png
  - /content/drive/MyDrive/CMx7_SI_DyGraph/derivatives/normalization/norm_stats_all_train_global.npz
  - /content/drive/MyDrive/CMx7_SI_DyGraph/derivatives/normalization/norm_stats_all_recording_scaled.npz
**Outputs checked:**
  - E-013 table
  - fold statistics
  - amplitude spread
  - normalised windows
**Sanity checks passed:**
  - summaries_for_every_stored_recording
  - summaries_match_arrays_exactly
  - stats_use_training_recordings_only
  - all_stats_finite
  - all_stds_positive
  - every_fold_and_mode_has_stats
  - all_set_labels_match_section10
  - normalised_windows_finite
  - normalised_train_windows_near_0_mean_1_std
  - excluded_subjects_absent_from_eeg_ok
**Errors found:**
  - train_global_amplitude_spread_below_4x
**Errors solved:**
  - E-013
**Open problems:**
  - train_global_amplitude_spread_below_4x
**Scientific decisions:**
  - D-026
  - D-027
**Next required input:** Printed output of Section 11 + the E-013 figure
**Next phase:** Section 12: lazy-loading PyTorch Dataset and DataLoader
<!-- END SECTION 11 -->

<!-- BEGIN SECTION 12 -->
## Section 12
**Phase:** Phase 8 (Notebook Section 12)
**Status:** Completed (pending your real output)
**Date:** 2026-10-12
**Objective:** Lazy, leakage-safe data loading.
**Completed tasks:**
  - local store copy
  - Dataset + sampler
  - fold loader builder
  - batch tests
  - leakage assertions
**Files created:**
  - /content/drive/MyDrive/CMx7_SI_DyGraph/configs/dataloader_config.json
**Outputs checked:**
  - batch shape
  - normalised values
  - throughput
**Sanity checks passed:**
  - batch_shape_is_batch_x_32_x_1000
  - float32_and_finite
  - normalised_batches_near_0_mean
  - train_recordings_equal_fold_train_split
  - no_test_or_val_recording_in_train
  - test_subject_only_in_test
  - test_uses_all_valid_windows
  - train_epoch_has_k_per_recording
  - epochs_draw_different_windows
  - local_store_complete
**Errors found:** None
**Errors solved:** None
**Open problems:** None
**Scientific decisions:**
  - D-028
**Next required input:** Section 12 + 13 output
**Next phase:** Section 13: Temporal CNN baseline
<!-- END SECTION 12 -->

<!-- BEGIN SECTION 13 -->
## Section 13
**Phase:** Phase 8 (Notebook Section 13)
**Status:** Completed (pending your real output)
**Date:** 2026-10-12
**Objective:** First EEG model under strict LOSO.
**Completed tasks:**
  - model
  - mode selection on validation
  - 30 LOSO folds
  - comparison with task-only reference
  - within-task preview
**Files created:**
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec13_tcnn_fold_results.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec13_tcnn_test_predictions.parquet
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec13_mode_selection.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/sec13_tcnn_vs_task_only.png
**Outputs checked:**
  - fold results
  - pooled metrics
  - within-task preview
**Sanity checks passed:**
  - all_loso_folds_finished
  - every_test_recording_predicted_once
  - predictions_match_fold_labels
  - probabilities_sum_to_1
  - metrics_finite
  - mode_chosen_on_validation_only
**Errors found:** None
**Errors solved:** None
**Open problems:** None
**Scientific decisions:**
  - D-029
  - D-030
**Next required input:** Section 12 + 13 output and the figure
**Next phase:** Section 14: EEGNet baseline (same folds, loaders and protocol)
<!-- END SECTION 13 -->

<!-- BEGIN SECTION 14 -->
## Section 14
**Phase:** Phase 8 (Notebook Section 14)
**Status:** Completed (pending your real output)
**Date:** 2026-10-12
**Objective:** EEGNet baseline + diagnosis of the Temporal CNN.
**Completed tasks:**
  - TCNN diagnosis
  - EEGNet LOSO
  - three-way comparison
**Files created:**
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec14_eegnet_fold_results.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec14_eegnet_test_predictions.parquet
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec14_tcnn_diagnosis.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/sec14_eegnet_vs_tcnn_vs_task_only.png
**Outputs checked:**
  - fold results
  - pooled metrics
  - within-task preview
**Sanity checks passed:**
  - all_loso_folds_finished
  - every_test_recording_predicted_once
  - predictions_match_fold_labels
  - same_test_recordings_as_tcnn
  - probabilities_sum_to_1
  - same_normalisation_as_tcnn
**Errors found:**
  - E-014
**Errors solved:** None
**Open problems:**
  - E-014 subject shift / class collapse
**Scientific decisions:**
  - D-031
**Next required input:** Section 14 output and the figure
**Next phase:** Section 15: fixed-graph GCN baseline
<!-- END SECTION 14 -->

<!-- BEGIN SECTION 15 -->
## Section 15
**Phase:** Phase 8 (Notebook Section 15)
**Status:** Completed (pending your real output)
**Date:** 2026-10-12
**Objective:** Fixed-graph GCN baseline under strict LOSO.
**Completed tasks:**
  - electrode kNN graph
  - GCN model
  - LOSO
  - comparison with all baselines
**Files created:**
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec15_gcn_fold_results.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec15_gcn_test_predictions.parquet
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec15_fixed_graph_adjacency.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/sec15_gcn_vs_baselines.png
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/sec15_fixed_graph.png
**Outputs checked:**
  - fold results
  - pooled metrics
  - within-task preview
**Sanity checks passed:**
  - graph_symmetric_with_self_loops
  - graph_from_geometry_only
  - every_node_has_k_neighbours
  - all_loso_folds_finished
  - every_test_recording_predicted_once
  - predictions_match_fold_labels
  - same_test_recordings_as_tcnn
  - probabilities_sum_to_1
**Errors found:** None
**Errors solved:** None
**Open problems:**
  - E-014 subject shift / class collapse
**Scientific decisions:**
  - D-032
**Next required input:** Section 15 output and both figures
**Next phase:** Section 16: static learnable graph baseline
<!-- END SECTION 15 -->

<!-- BEGIN SECTION 16 -->
## Section 16
**Phase:** Phase 8 (Notebook Section 16)
**Status:** Completed (pending your real output)
**Date:** 2026-10-12
**Objective:** Static learnable graph baseline under strict LOSO.
**Completed tasks:**
  - learnable sparse graph
  - LOSO
  - learned-graph stability analysis
  - comparison with all baselines
**Files created:**
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec16_static_graph_fold_results.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec16_static_graph_test_predictions.parquet
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec16_learned_graphs.npz
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec16_learned_edge_frequency.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/sec16_learned_static_graph.png
**Outputs checked:**
  - fold results
  - pooled metrics
  - graph stability
**Sanity checks passed:**
  - all_loso_folds_finished
  - every_test_recording_predicted_once
  - predictions_match_fold_labels
  - same_test_recordings_as_tcnn
  - probabilities_sum_to_1
  - learned_graphs_symmetric
  - learned_graphs_sparse_topk
  - one_graph_per_fold
**Errors found:** None
**Errors solved:** None
**Open problems:**
  - E-014 subject shift / class collapse
**Scientific decisions:**
  - D-033
**Next required input:** Section 16 output and the figure
**Next phase:** Section 17: epoch-specific dynamic graph (proposed model core)
<!-- END SECTION 16 -->

<!-- BEGIN SECTION 17 -->
## Section 17
**Phase:** Phase 9 (Notebook Section 17)
**Status:** Completed (pending your real output)
**Date:** 2026-10-12
**Objective:** Epoch-specific dynamic graph model under strict LOSO.
**Completed tasks:**
  - per-window sparse graph generator
  - LOSO
  - graph dynamics on validation subjects
  - comparison with all baselines
**Files created:**
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec17_dynamic_graph_fold_results.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec17_dynamic_graph_test_predictions.parquet
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec17_graph_dynamics_validation.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec17_dynamic_edge_frequency_validation.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/sec17_dynamic_graph_analysis.png
**Outputs checked:**
  - fold results
  - pooled metrics
  - graph dynamics
  - workload vs subject separation
**Sanity checks passed:**
  - all_loso_folds_finished
  - every_test_recording_predicted_once
  - predictions_match_fold_labels
  - same_test_recordings_as_tcnn
  - probabilities_sum_to_1
  - graph_analysis_on_all_folds
  - graph_analysis_used_validation_subjects_only
  - graphs_change_between_windows
  - edge_usage_is_a_share
**Errors found:** None
**Errors solved:** None
**Open problems:**
  - E-014 subject shift / class collapse
**Scientific decisions:**
  - D-034
**Next required input:** Section 17 output and the figure
**Next phase:** Section 18: graph consistency and separation
<!-- END SECTION 17 -->

<!-- BEGIN SECTION 18 -->
## Section 18
**Phase:** Phase 9 (Notebook Section 18)
**Status:** Completed (pending your real output)
**Date:** 2026-10-12
**Objective:** Graph consistency and separation loss on the dynamic graph model.
**Completed tasks:**
  - graph loss W/(W+B)
  - λ choice on validation
  - LOSO
  - graph comparison Section 17 vs 18 on validation subjects
**Files created:**
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec18_lambda_selection.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec18_graph_consistency_fold_results.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec18_graph_consistency_test_predictions.parquet
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec18_graph_comparison_validation.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/sec18_graph_consistency.png
**Outputs checked:**
  - fold results
  - pooled metrics
  - subject vs workload information in the graphs
**Sanity checks passed:**
  - lambda_chosen_on_validation_only
  - every_candidate_tried_on_selection_folds
  - all_loso_folds_finished
  - every_test_recording_predicted_once
  - predictions_match_fold_labels
  - same_test_recordings_as_tcnn
  - probabilities_sum_to_1
  - graph_comparison_on_all_folds
  - graph_comparison_used_validation_subjects_only
  - graph_share_in_0_1
**Errors found:** None
**Errors solved:** None
**Open problems:**
  - E-014 subject shift / class collapse
**Scientific decisions:**
  - D-035
**Next required input:** Section 18 output and the figure
**Next phase:** Section 19: subject-adversarial learning
<!-- END SECTION 18 -->

<!-- BEGIN SECTION 19 -->
## Section 19
**Phase:** Phase 9 (Notebook Section 19)
**Status:** Completed (pending your real output)
**Date:** 2026-10-12
**Objective:** Subject-adversarial learning on top of the graph-consistency model.
**Completed tasks:**
  - gradient reversal subject head
  - β choice on validation
  - LOSO
  - identity / workload probes on validation subjects
**Files created:**
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec19_beta_selection.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec19_subject_adv_fold_results.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec19_subject_adv_test_predictions.parquet
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec19_embedding_probes_validation.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/sec19_subject_adversarial_probes.png
**Outputs checked:**
  - fold results
  - pooled metrics
  - subject-identity probe
  - workload probe
**Sanity checks passed:**
  - beta_chosen_on_validation_only
  - every_candidate_tried_on_selection_folds
  - all_loso_folds_finished
  - every_test_recording_predicted_once
  - predictions_match_fold_labels
  - same_test_recordings_as_tcnn
  - probabilities_sum_to_1
  - probes_on_all_folds
  - probes_used_validation_subjects_only
  - probe_values_in_0_1
**Errors found:** None
**Errors solved:** None
**Open problems:**
  - E-014 subject shift / class collapse
**Scientific decisions:**
  - D-036
**Next required input:** Section 19 output and the figure
**Next phase:** Section 20: task-adversarial learning (TCAI, novelty N1)
<!-- END SECTION 19 -->

<!-- BEGIN SECTION 20 -->
## Section 20
**Phase:** Phase 9 (Notebook Section 20)
**Status:** Completed (pending your real output)
**Date:** 2026-10-12
**Objective:** Task-adversarial learning: plain task GRL vs TCAI (N1) on identical LOSO folds.
**Completed tasks:**
  - task adversary (plain / rating-conditioned)
  - γ choice per variant on validation
  - LOSO
  - within-task ρ with bootstrap CI
  - unconditional and conditional task probes
**Files created:**
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec20_gamma_selection.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec20_task_adv_fold_results.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec20_task_adv_test_predictions.parquet
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec20_within_task_rho.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec20_task_probes_validation.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/sec20_tcai_vs_plain.png
**Outputs checked:**
  - fold results
  - macro-F1
  - within-task ρ
  - task probes
**Sanity checks passed:**
  - gamma_chosen_on_validation_only_per_variant
  - every_candidate_tried_on_selection_folds
  - all_loso_folds_finished_both_variants
  - every_test_recording_predicted_once_per_variant
  - identical_test_recordings_A_B_C
  - predictions_match_fold_labels
  - probabilities_sum_to_1
  - eligible_tasks_from_training_ratings_only
  - prediction_uses_eeg_only
  - probes_on_all_folds_validation_only
**Errors found:** None
**Errors solved:** None
**Open problems:**
  - E-014 subject shift / class collapse
**Scientific decisions:**
  - D-037
**Next required input:** Section 20 output and the figure
**Next phase:** Section 21: full model training
<!-- END SECTION 20 -->

<!-- BEGIN SECTION 21 -->
## Section 21
**Phase:** Phase 10 (Notebook Section 21)
**Status:** Completed (pending your real output)
**Date:** 2026-10-12
**Objective:** Full model v1 (3 seeds) + model v2 subject-alignment candidates; final model fixed.
**Completed tasks:**
  - attention pooling
  - 3 seeds
  - per-subject alignment (z-score / Euclidean)
  - validation-based final-model rule
  - linear probes
**Files created:**
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec21b_v2_fold_results.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec21b_v2_test_predictions.parquet
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec21b_probes_validation.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/final_model.json
  - /content/drive/MyDrive/CMx7_SI_DyGraph/derivatives/normalization/subject_alignment_stats.npz
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/sec21b_model_v2.png
**Outputs checked:**
  - v1 vs v2 test table
  - probes
  - final_model.json
**Sanity checks passed:**
  - alignment_stats_label_free
  - alignment_stats_all_subjects
  - all_candidates_all_folds_finished
  - every_test_recording_once_per_candidate
  - same_test_recordings_as_v1
  - decision_from_validation_only
  - probes_validation_only_all_folds
  - probabilities_sum_to_1
**Errors found:** None
**Errors solved:** None
**Open problems:**
  - E-014 subject shift / class collapse
**Scientific decisions:**
  - D-038
  - D-039
  - D-040
**Next required input:** Section 21B and 22 outputs
**Next phase:** Section 22: LOSO evaluation + N2 protocol
<!-- END SECTION 21 -->

<!-- BEGIN SECTION 22 -->
## Section 22
**Phase:** Phase 11 (Notebook Section 22)
**Status:** Completed (pending your real output)
**Date:** 2026-10-12
**Objective:** LOSO benchmark (N3) and the complete confound-controlled protocol (N2).
**Completed tasks:**
  - benchmark table with task-only Δ
  - within-task permutation
  - stimulus-rhythm test
  - N2 summary
**Files created:**
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec22_benchmark_table.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec22_benchmark_fold_bal_acc.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec22_permutation_results.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec22_permutation_predictions.parquet
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec22_rhythm_features.parquet
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec22_rhythm_test.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec22_n2_summary.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/sec22_benchmark_and_n2.png
**Outputs checked:**
  - benchmark
  - permutation
  - rhythm
  - N2 summary
**Sanity checks passed:**
  - task_only_matches_section10
  - every_model_same_test_recordings
  - permutation_only_train_val
  - permutation_moved_labels
  - permutation_runs_finished
  - permutation_tested_on_true_labels
  - rhythm_features_label_free_all_recordings
  - final_model_unchanged
**Errors found:** None
**Errors solved:** None
**Open problems:**
  - E-014 subject shift / class collapse
**Scientific decisions:**
  - D-041
**Next required input:** Section 22 output and the figure
**Next phase:** Section 23: cross-session evaluation
<!-- END SECTION 22 -->

<!-- BEGIN SECTION 23 -->
## Section 23
**Phase:** Phase 11 (Notebook Section 23)
**Status:** Completed (pending your real output)
**Date:** 2026-10-12
**Objective:** N1 on EEGNet (22B) and cross-session benchmark (23).
**Completed tasks:**
  - TCAI on EEGNet with pre-registered verdict
  - cross-session 8 models
  - KSS confound
**Files created:**
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec22b_gamma_selection.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec22b_fold_results.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec22b_test_predictions.parquet
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec22b_probes_validation.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec22b_n1_eegnet_summary.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec23_fold_results.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec23_test_predictions.parquet
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec23_cross_session_table.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec23_kss_analysis.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/sec22b_tcai_eegnet.png
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/sec23_cross_session.png
**Outputs checked:**
  - N1 verdict
  - cross-session table
  - KSS
**Sanity checks passed:**
  - rule_saved_before_results
  - gamma_chosen_on_validation_per_variant
  - all_folds_finished
  - identical_test_recordings_A_B_C
  - every_test_recording_once
  - prediction_uses_eeg_only
  - probes_validation_only_all_folds
  - three_cross_session_folds
  - all_models_all_folds_finished
  - every_test_recording_once_per_model
  - test_is_one_unseen_session
  - alignment_from_training_sessions_only
  - hyperparameters_from_validation
**Errors found:** None
**Errors solved:** None
**Open problems:**
  - E-014 subject shift / class collapse
**Scientific decisions:**
  - D-042b
  - D-043
  - D-044
**Next required input:** Sections 22B-24 output
**Next phase:** Section 24: ablation
<!-- END SECTION 23 -->

<!-- BEGIN SECTION 24 -->
## Section 24
**Phase:** Phase 11 (Notebook Section 24)
**Status:** Completed (pending your real output)
**Date:** 2026-10-12
**Objective:** Ablation study of the final model.
**Completed tasks:**
  - leave-one-out
  - build-up table
  - low-amplitude sensitivity
  - seed-noise reference
**Files created:**
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec24_ablation_fold_results.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec24_ablation_predictions.parquet
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec24_ablation_table.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec24_buildup_table.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec24_low_amplitude_sensitivity.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/sec24_ablation.png
**Outputs checked:**
  - ablation table
  - build-up table
**Sanity checks passed:**
  - ablations_and_sensitivity_finished
  - same_test_recordings_as_final
  - every_test_recording_once
  - one_component_removed_each
  - buildup_complete
**Errors found:** None
**Errors solved:** None
**Open problems:**
  - E-014 subject shift / class collapse
**Scientific decisions:**
  - D-045
**Next required input:** Sections 22B-24 output and figures
**Next phase:** Section 25: XAI
<!-- END SECTION 24 -->

<!-- BEGIN SECTION 25 -->
## Section 25
**Phase:** Phase 12 (Notebook Section 25)
**Status:** Completed (pending your real output)
**Date:** 2026-10-12
**Objective:** Explain EEGNet and the final model; artefact shortcut audit.
**Completed tasks:**
  - occlusion
  - Integrated Gradients
  - deletion test
  - attention
  - learned graphs
  - artefact audit
**Files created:**
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec25_fold_rows.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec25_channel_importance.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec25_region_importance.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec25_band_importance.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec25_task_group_regions.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec25_deletion.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec25_graph_edges.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec25_shortcut_audit.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/sec25_xai_overview.png
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/sec25_learned_graphs.png
**Outputs checked:**
  - region importance
  - band importance
  - shortcut audit
  - graph edges
**Sanity checks passed:**
  - both_models_all_folds
  - only_held_out_test_subjects
  - regions_cover_every_channel_once
  - attention_sums_to_one
  - deletion_k0_equals_baseline
  - graphs_for_all_folds
  - no_nan_in_importance
**Errors found:** None
**Errors solved:** None
**Open problems:** None
**Scientific decisions:**
  - D-047
**Next required input:** Section 25-27 output and figures
**Next phase:** Section 26: statistics
<!-- END SECTION 25 -->

<!-- BEGIN SECTION 26 -->
## Section 26
**Phase:** Phase 12 (Notebook Section 26)
**Status:** Completed (pending your real output)
**Date:** 2026-10-12
**Objective:** Statistical testing of every thesis claim.
**Completed tasks:**
  - 4 Holm families
  - bootstrap CIs
  - effect sizes
  - Friedman/Nemenyi
  - claims ledger
**Files created:**
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec26_loso_summary.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec26_family_tests.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec26_cross_session_summary.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec26_friedman.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/results/sec26_claims_ledger.csv
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/sec26_statistics.png
**Outputs checked:**
  - LOSO summary
  - family tests
  - claims ledger
**Sanity checks passed:**
  - same_test_recordings_every_model
  - one_test_subject_per_fold
  - holm_never_below_raw_p
  - ci_contains_delta
  - effect_sizes_in_range
  - families_defined_before_p_values
  - claims_ledger_complete
**Errors found:** None
**Errors solved:** None
**Open problems:** None
**Scientific decisions:**
  - D-048
**Next required input:** Section 25-27 output and figures
**Next phase:** Section 27: final report
<!-- END SECTION 26 -->

<!-- BEGIN SECTION 27 -->
## Section 27
**Phase:** Phase 12 (Notebook Section 27)
**Status:** Completed (pending your real output)
**Date:** 2026-10-12
**Objective:** Final results and reproducibility report.
**Completed tasks:**
  - FINAL_REPORT.md
  - config_final.json
  - final_manifest.json
  - results bundle
**Files created:**
  - /content/drive/MyDrive/CMx7_SI_DyGraph/reports/FINAL_REPORT.md
  - /content/drive/MyDrive/CMx7_SI_DyGraph/configs/config_final.json
  - /content/drive/MyDrive/CMx7_SI_DyGraph/reports/final_manifest.json
  - /content/drive/MyDrive/CMx7_SI_DyGraph/reports/CMx7_SI_DyGraph_results_bundle.zip
**Outputs checked:**
  - claims ledger
  - all report tables
**Sanity checks passed:**
  - report_written_and_nonempty
  - claims_ledger_in_report
  - every_listed_figure_exists
  - manifest_hashes_match
  - bundle_contains_report_and_logs
  - bundle_has_no_checkpoints_or_eeg
  - config_saved
**Errors found:** None
**Errors solved:** None
**Open problems:**
  - COG-BCI external validation (planned)
**Scientific decisions:**
  - D-049
**Next required input:** Section 25-27 output, FINAL_REPORT.md and the bundle
**Next phase:** External validation (COG-BCI)
<!-- END SECTION 27 -->

<!-- BEGIN SECTION 28 -->
## Section 28
**Phase:** Phase 12 (Notebook Section 28)
**Status:** Completed (pending your real output)
**Date:** 2026-10-12
**Objective:** Publication-ready figures, LaTeX tables and captions.
**Completed tasks:**
  - fig01_label_structure
  - fig02_loso_benchmark
  - fig03_task_shortcut
  - fig04_n1_tcai
  - fig05_cross_session
  - fig06_ablation
  - fig07_xai_regions_bands
  - fig08_scalp_maps
  - fig09_learned_graph
  - fig10_planned_comparisons
  - table1_loso_benchmark
  - table2_cross_session
  - table3_planned_comparisons
**Files created:**
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/paper/fig01_label_structure.pdf
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/paper/fig02_loso_benchmark.pdf
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/paper/fig03_task_shortcut.pdf
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/paper/fig04_n1_tcai.pdf
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/paper/fig05_cross_session.pdf
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/paper/fig06_ablation.pdf
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/paper/fig07_xai_regions_bands.pdf
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/paper/fig08_scalp_maps.pdf
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/paper/fig09_learned_graph.pdf
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/paper/fig10_planned_comparisons.pdf
  - /content/drive/MyDrive/CMx7_SI_DyGraph/reports/paper_tables/table1_loso_benchmark.tex
  - /content/drive/MyDrive/CMx7_SI_DyGraph/reports/paper_tables/table2_cross_session.tex
  - /content/drive/MyDrive/CMx7_SI_DyGraph/reports/paper_tables/table3_planned_comparisons.tex
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/paper/FIGURE_CAPTIONS.md
  - /content/drive/MyDrive/CMx7_SI_DyGraph/figures/paper/paper_figures_manifest.json
**Outputs checked:**
  - all Section 22-27 result tables
**Sanity checks passed:**
  - all_figures_drawn
  - pdf_and_png_written
  - png_resolution_at_least_dpi
  - fig02_values_equal_table
  - fig03_one_point_per_subject
  - fig04_values_equal_table
  - label_figure_covers_all_test_recordings
  - latex_tables_complete
  - captions_for_every_figure
  - result_files_unchanged
  - outputs_only_in_paper_folders
**Errors found:** None
**Errors solved:** None
**Open problems:** None
**Scientific decisions:**
  - D-050
**Next required input:** Section 28 output and the 10 figures
**Next phase:** COG-BCI external results (Kaggle FINAL notebook)
<!-- END SECTION 28 -->
