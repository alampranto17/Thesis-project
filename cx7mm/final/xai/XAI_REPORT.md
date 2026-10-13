# XAI report (pre-registered: cx7mm/xai_prereg, commit cf38ad9)

Run finished 2026-10-13T07:22:24.693182+00:00 | pre-registration SHA-256 verified | v4 lock = d_v3_ls

## H-X0 gates
| dataset   | role   |   H-X0a_p | H-X0a_pass   |   H-X0b_median_rho | H-X0b_pass   | gates_pass   |
|:----------|:-------|----------:|:-------------|-------------------:|:-------------|:-------------|
| cmx7      | M_base |    0.0853 | False        |             0.4637 | True         | False        |
| cmx7      | M_prop |    0.3395 | False        |             0.9875 | False        | False        |
| cmx7      | M_ref  |    0.8612 | False        |             0.9879 | False        | False        |
| cog       | M_base |    0.0002 | True         |             0.3702 | True         | True         |
| cog       | M_prop |    0.4367 | False        |             0.9875 | False        | False        |
| cog       | M_ref  |    0.1934 | False        |             0.9877 | False        | False        |

## Primary family (one-sided Wilcoxon over subjects, Holm over 7 tests)
| test     | dataset   | direction       |   n_subjects |   mean_A |   mean_B |   mean_diff_A_minus_B | ci95_diff                                  |   wins |   losses |   rank_biserial_r |      p | gates_pass   |   p_holm | verdict       |
|:---------|:----------|:----------------|-------------:|---------:|---------:|----------------------:|:-------------------------------------------|-------:|---------:|------------------:|-------:|:-------------|---------:|:--------------|
| H-X1     | cog       | M_prop < M_ref  |           29 |   0.8525 |   0.8352 |                0.0172 | (np.float64(-0.0019), np.float64(0.0383))  |      4 |        8 |            0.5256 | 0.9488 | False        |   1      | NOT EVALUABLE |
| H-X2a    | cmx7      | M_prop < M_base |           30 |   0.1983 |   0.1491 |                0.0491 | (np.float64(0.0163), np.float64(0.0796))   |      7 |       23 |            0.6129 | 0.9988 | False        |   1      | NOT EVALUABLE |
| H-X2b    | cmx7      | M_prop < M_base |           30 |   0.1388 |   0.0582 |                0.0807 | (np.float64(0.0521), np.float64(0.1066))   |      4 |       26 |            0.7978 | 1      | False        |   1      | NOT EVALUABLE |
| H-X3-cmx | cmx7      | M_prop > M_base |           30 |   0.0788 |   0.0725 |                0.0063 | (np.float64(-0.0216), np.float64(0.0269))  |     24 |        6 |            0.5699 | 0.0027 | False        |   0.0188 | NOT EVALUABLE |
| H-X3-cog | cog       | M_prop > M_base |           29 |   0.0834 |   0.1075 |               -0.0241 | (np.float64(-0.0404), np.float64(-0.0073)) |     11 |       18 |           -0.5034 | 0.9921 | False        |   1      | NOT EVALUABLE |
| H-X4-cmx | cmx7      | M_prop > M_ref  |           30 |   0.6938 |   0.6968 |               -0.0029 | (np.float64(-0.0077), np.float64(0.0017))  |     12 |       17 |           -0.2552 | 0.885  | False        |   1      | NOT EVALUABLE |
| H-X4-cog | cog       | M_prop > M_ref  |           29 |   0.793  |   0.8044 |               -0.0114 | (np.float64(-0.03), np.float64(0.0062))    |      8 |       21 |           -0.4759 | 0.9874 | False        |   1      | NOT EVALUABLE |

**XAI novelty claim:** NOT made (H-X1 not SUPPORTED)

## Secondary (no claim)
| dataset   | metric            | pair            |   n |   mean_diff | ci95                                       |   rank_biserial_r |   p_two_sided |
|:----------|:------------------|:----------------|----:|------------:|:-------------------------------------------|------------------:|--------------:|
| cog       | task_decodability | M_prop - M_ref  |  29 |      0.0172 | (np.float64(-0.0019), np.float64(0.0383))  |            0.5256 |        0.1024 |
| cog       | task_decodability | M_prop - M_base |  29 |      0.1111 | (np.float64(0.0785), np.float64(0.1456))   |            0.9674 |        0      |
| cog       | task_decodability | M_ref - M_base  |  29 |      0.0939 | (np.float64(0.0575), np.float64(0.1322))   |            0.8623 |        0.0003 |
| cog       | temporal_share    | M_prop - M_ref  |  29 |     -0.0058 | (np.float64(-0.0132), np.float64(0.0011))  |           -0.3105 |        0.1663 |
| cog       | temporal_share    | M_prop - M_base |  29 |      0.0709 | (np.float64(0.0457), np.float64(0.0937))   |            0.8483 |        0      |
| cog       | temporal_share    | M_ref - M_base  |  29 |      0.0768 | (np.float64(0.0514), np.float64(0.0997))   |            0.8621 |        0      |
| cog       | gamma_share       | M_prop - M_ref  |  29 |     -0.01   | (np.float64(-0.018), np.float64(-0.002))   |           -0.4575 |        0.0308 |
| cog       | gamma_share       | M_prop - M_base |  29 |      0.014  | (np.float64(-0.0133), np.float64(0.0391))  |            0.3793 |        0.076  |
| cog       | gamma_share       | M_ref - M_base  |  29 |      0.024  | (np.float64(-0.0065), np.float64(0.0505))  |            0.5402 |        0.0099 |
| cog       | marker_share      | M_prop - M_ref  |  29 |     -0.0005 | (np.float64(-0.0035), np.float64(0.0027))  |           -0.108  |        0.6239 |
| cog       | marker_share      | M_prop - M_base |  29 |     -0.0241 | (np.float64(-0.0404), np.float64(-0.0073)) |           -0.5034 |        0.0168 |
| cog       | marker_share      | M_ref - M_base  |  29 |     -0.0237 | (np.float64(-0.0403), np.float64(-0.0063)) |           -0.4943 |        0.019  |
| cog       | consistency       | M_prop - M_ref  |  29 |     -0.0114 | (np.float64(-0.03), np.float64(0.0062))    |           -0.4759 |        0.0252 |
| cog       | consistency       | M_prop - M_base |  29 |      0.4374 | (np.float64(0.3724), np.float64(0.5049))   |            1      |        0      |
| cog       | consistency       | M_ref - M_base  |  29 |      0.4488 | (np.float64(0.3767), np.float64(0.519))    |            1      |        0      |
| cmx7      | temporal_share    | M_prop - M_ref  |  30 |     -0.0004 | (np.float64(-0.0085), np.float64(0.0091))  |           -0.1538 |        0.6379 |
| cmx7      | temporal_share    | M_prop - M_base |  30 |      0.0491 | (np.float64(0.0163), np.float64(0.0796))   |            0.6129 |        0.0026 |
| cmx7      | temporal_share    | M_ref - M_base  |  30 |      0.0495 | (np.float64(0.0185), np.float64(0.08))     |            0.5699 |        0.0054 |
| cmx7      | gamma_share       | M_prop - M_ref  |  30 |     -0.0178 | (np.float64(-0.0334), np.float64(-0.0031)) |           -0.4452 |        0.0327 |
| cmx7      | gamma_share       | M_prop - M_base |  30 |      0.0807 | (np.float64(0.0521), np.float64(0.1066))   |            0.7978 |        0      |
| cmx7      | gamma_share       | M_ref - M_base  |  30 |      0.0985 | (np.float64(0.0677), np.float64(0.1275))   |            0.8796 |        0      |
| cmx7      | marker_share      | M_prop - M_ref  |  30 |     -0.0024 | (np.float64(-0.0058), np.float64(0.0008))  |           -0.2063 |        0.3488 |
| cmx7      | marker_share      | M_prop - M_base |  30 |      0.0063 | (np.float64(-0.0216), np.float64(0.0269))  |            0.5699 |        0.0054 |
| cmx7      | marker_share      | M_ref - M_base  |  30 |      0.0087 | (np.float64(-0.0193), np.float64(0.0295))  |            0.6172 |        0.0024 |
| cmx7      | consistency       | M_prop - M_ref  |  30 |     -0.0029 | (np.float64(-0.0077), np.float64(0.0017))  |           -0.2552 |        0.2301 |
| cmx7      | consistency       | M_prop - M_base |  30 |      0.2814 | (np.float64(0.1339), np.float64(0.413))    |            0.6086 |        0.0028 |
| cmx7      | consistency       | M_ref - M_base  |  30 |      0.2843 | (np.float64(0.1337), np.float64(0.4191))   |            0.6129 |        0.0026 |

### CMx7 task-within-class decodability vs permutation null
| role   |   observed |   null_mean |   null_95th |   p_perm |
|:-------|-----------:|------------:|------------:|---------:|
| M_base |     0.2741 |      0.2671 |      0.3038 |   0.3168 |
| M_prop |     0.2897 |      0.2863 |      0.3211 |   0.495  |
| M_ref  |     0.3103 |      0.2865 |      0.3161 |   0.1386 |

### IG vs channel-occlusion agreement
| dataset   | role   |   median_spearman_IG_vs_occlusion |
|:----------|:-------|----------------------------------:|
| cmx7      | M_base |                             0.393 |
| cmx7      | M_prop |                             0.463 |
| cmx7      | M_ref  |                             0.31  |
| cog       | M_base |                             0.38  |
| cog       | M_prop |                             0.293 |
| cog       | M_ref  |                             0.263 |

### CMx7 region shares by task group
| role   | task_group      |   frontal_polar_eye |   frontal |   temporal_emg |   central_motor |   parietal_occipital |
|:-------|:----------------|--------------------:|----------:|---------------:|----------------:|---------------------:|
| M_base | cognitive       |              0.1342 |    0.1581 |         0.138  |          0.2557 |               0.314  |
| M_base | cognitive_motor |              0.1199 |    0.1568 |         0.1467 |          0.211  |               0.3656 |
| M_base | motor           |              0.0944 |    0.1481 |         0.1761 |          0.2547 |               0.3267 |
| M_prop | cognitive       |              0.1988 |    0.1955 |         0.2008 |          0.1994 |               0.2056 |
| M_prop | cognitive_motor |              0.2032 |    0.1977 |         0.1955 |          0.2004 |               0.2032 |
| M_prop | motor           |              0.2001 |    0.2059 |         0.1945 |          0.1991 |               0.2004 |
| M_ref  | cognitive       |              0.202  |    0.1928 |         0.2037 |          0.2005 |               0.2009 |
| M_ref  | cognitive_motor |              0.2054 |    0.1954 |         0.193  |          0.204  |               0.2022 |
| M_ref  | motor           |              0.2022 |    0.2001 |         0.1932 |          0.2019 |               0.2026 |
