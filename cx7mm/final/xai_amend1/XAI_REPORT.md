# XAI report, amendment 1 (exploratory; protocol cx7mm/xai_prereg + final/xai_amend1/xai_amendment_1.json)

Run finished 2026-10-13T13:36:13.032303+00:00 | pre-registration SHA-256 verified | v4 lock = d_v3_ls

## H-X0 gates
| dataset   | role   |   H-X0a_p | H-X0a_pass   |   H-X0b_median_rho | H-X0b_pass   | gates_pass   |
|:----------|:-------|----------:|:-------------|-------------------:|:-------------|:-------------|
| cmx7      | M_base |    0.0853 | False        |             0.4637 | True         | False        |
| cmx7      | M_prop |    0.0006 | True         |             0.2168 | True         | True         |
| cmx7      | M_ref  |    0.0349 | True         |             0.2551 | True         | True         |
| cog       | M_base |    0.0002 | True         |             0.3702 | True         | True         |
| cog       | M_prop |    0      | True         |             0.4648 | True         | True         |
| cog       | M_ref  |    0      | True         |             0.4311 | True         | True         |

## Primary family (one-sided Wilcoxon over subjects, Holm over 7 tests)
| test     | dataset   | direction       |   n_subjects |   mean_A |   mean_B |   mean_diff_A_minus_B | ci95_diff                                 |   wins |   losses |   rank_biserial_r |      p | gates_pass   |   p_holm | verdict                 |
|:---------|:----------|:----------------|-------------:|---------:|---------:|----------------------:|:------------------------------------------|-------:|---------:|------------------:|-------:|:-------------|---------:|:------------------------|
| H-X1     | cog       | M_prop < M_ref  |           29 |   0.6437 |   0.6379 |                0.0057 | (np.float64(-0.0326), np.float64(0.0402)) |      9 |       13 |            0.0514 | 0.584  | True         |   1      | NOT SUPPORTED           |
| H-X2a    | cmx7      | M_prop < M_base |           30 |   0.1946 |   0.1491 |                0.0455 | (np.float64(0.0069), np.float64(0.0851))  |     10 |       20 |            0.4538 | 0.9861 | False        |   1      | NOT EVALUABLE           |
| H-X2b    | cmx7      | M_prop < M_base |           30 |   0.1388 |   0.0582 |                0.0807 | (np.float64(0.0521), np.float64(0.1066))  |      4 |       26 |            0.7978 | 1      | False        |   1      | NOT EVALUABLE           |
| H-X3-cmx | cmx7      | M_prop > M_base |           30 |   0.0846 |   0.0725 |                0.0121 | (np.float64(-0.0191), np.float64(0.0348)) |     23 |        7 |            0.5613 | 0.0031 | False        |   0.0186 | NOT EVALUABLE           |
| H-X3-cog | cog       | M_prop > M_base |           29 |   0.1779 |   0.1075 |                0.0704 | (np.float64(0.0482), np.float64(0.0943))  |     26 |        3 |            0.908  | 0      | True         |   0      | SUPPORTED (exploratory) |
| H-X4-cmx | cmx7      | M_prop > M_ref  |           30 |   0.5513 |   0.5649 |               -0.0135 | (np.float64(-0.0514), np.float64(0.0256)) |     13 |       17 |           -0.1656 | 0.786  | True         |   1      | NOT SUPPORTED           |
| H-X4-cog | cog       | M_prop > M_ref  |           29 |   0.6964 |   0.705  |               -0.0086 | (np.float64(-0.0456), np.float64(0.0299)) |     15 |       14 |           -0.0989 | 0.6804 | True         |   1      | NOT SUPPORTED           |

**XAI novelty claim:** NOT made (H-X1 not SUPPORTED)

## Secondary (no claim)
| dataset   | metric            | pair            |   n |   mean_diff | ci95                                       |   rank_biserial_r |   p_two_sided |
|:----------|:------------------|:----------------|----:|------------:|:-------------------------------------------|------------------:|--------------:|
| cog       | task_decodability | M_prop - M_ref  |  29 |      0.0057 | (np.float64(-0.0326), np.float64(0.0402))  |            0.0514 |        0.832  |
| cog       | task_decodability | M_prop - M_base |  29 |     -0.0977 | (np.float64(-0.1456), np.float64(-0.0517)) |           -0.7721 |        0.0006 |
| cog       | task_decodability | M_ref - M_base  |  29 |     -0.1034 | (np.float64(-0.1533), np.float64(-0.0575)) |           -0.7569 |        0.0009 |
| cog       | temporal_share    | M_prop - M_ref  |  29 |     -0.0028 | (np.float64(-0.0107), np.float64(0.0052))  |           -0.177  |        0.4169 |
| cog       | temporal_share    | M_prop - M_base |  29 |     -0.0349 | (np.float64(-0.061), np.float64(-0.0114))  |           -0.4897 |        0.0203 |
| cog       | temporal_share    | M_ref - M_base  |  29 |     -0.0321 | (np.float64(-0.0584), np.float64(-0.0088)) |           -0.4391 |        0.0386 |
| cog       | gamma_share       | M_prop - M_ref  |  29 |     -0.01   | (np.float64(-0.018), np.float64(-0.002))   |           -0.4575 |        0.0308 |
| cog       | gamma_share       | M_prop - M_base |  29 |      0.014  | (np.float64(-0.0133), np.float64(0.0391))  |            0.3793 |        0.076  |
| cog       | gamma_share       | M_ref - M_base  |  29 |      0.024  | (np.float64(-0.0065), np.float64(0.0505))  |            0.5402 |        0.0099 |
| cog       | marker_share      | M_prop - M_ref  |  29 |      0.0285 | (np.float64(0.0179), np.float64(0.0391))   |            0.7977 |        0.0001 |
| cog       | marker_share      | M_prop - M_base |  29 |      0.0704 | (np.float64(0.0482), np.float64(0.0943))   |            0.908  |        0      |
| cog       | marker_share      | M_ref - M_base  |  29 |      0.0418 | (np.float64(0.0191), np.float64(0.0669))   |            0.577  |        0.0056 |
| cog       | consistency       | M_prop - M_ref  |  29 |     -0.0086 | (np.float64(-0.0456), np.float64(0.0299))  |           -0.0989 |        0.6545 |
| cog       | consistency       | M_prop - M_base |  29 |      0.3408 | (np.float64(0.2595), np.float64(0.4182))   |            0.9494 |        0      |
| cog       | consistency       | M_ref - M_base  |  29 |      0.3494 | (np.float64(0.2607), np.float64(0.4312))   |            0.9356 |        0      |
| cmx7      | temporal_share    | M_prop - M_ref  |  30 |      0.0127 | (np.float64(-0.0042), np.float64(0.0304))  |            0.2731 |        0.1981 |
| cmx7      | temporal_share    | M_prop - M_base |  30 |      0.0455 | (np.float64(0.0069), np.float64(0.0851))   |            0.4538 |        0.0293 |
| cmx7      | temporal_share    | M_ref - M_base  |  30 |      0.0328 | (np.float64(-0.0043), np.float64(0.068))   |            0.3806 |        0.0699 |
| cmx7      | gamma_share       | M_prop - M_ref  |  30 |     -0.0178 | (np.float64(-0.0334), np.float64(-0.0031)) |           -0.4452 |        0.0327 |
| cmx7      | gamma_share       | M_prop - M_base |  30 |      0.0807 | (np.float64(0.0521), np.float64(0.1066))   |            0.7978 |        0      |
| cmx7      | gamma_share       | M_ref - M_base  |  30 |      0.0985 | (np.float64(0.0677), np.float64(0.1275))   |            0.8796 |        0      |
| cmx7      | marker_share      | M_prop - M_ref  |  30 |      0.0018 | (np.float64(-0.0079), np.float64(0.0114))  |            0.1011 |        0.6408 |
| cmx7      | marker_share      | M_prop - M_base |  30 |      0.0121 | (np.float64(-0.0191), np.float64(0.0348))  |            0.5613 |        0.0062 |
| cmx7      | marker_share      | M_ref - M_base  |  30 |      0.0104 | (np.float64(-0.0217), np.float64(0.036))   |            0.4495 |        0.031  |
| cmx7      | consistency       | M_prop - M_ref  |  30 |     -0.0135 | (np.float64(-0.0514), np.float64(0.0256))  |           -0.1656 |        0.44   |
| cmx7      | consistency       | M_prop - M_base |  30 |      0.1389 | (np.float64(0.0659), np.float64(0.2136))   |            0.6    |        0.0032 |
| cmx7      | consistency       | M_ref - M_base  |  30 |      0.1524 | (np.float64(0.0652), np.float64(0.2345))   |            0.5828 |        0.0043 |

### CMx7 task-within-class decodability vs permutation null
| role   |   observed |   null_mean |   null_95th |   p_perm |
|:-------|-----------:|------------:|------------:|---------:|
| M_base |     0.2741 |      0.267  |      0.3038 |   0.3168 |
| M_prop |     0.2283 |      0.2621 |      0.3026 |   0.9505 |
| M_ref  |     0.2513 |      0.2634 |      0.3001 |   0.7129 |

### IG vs channel-occlusion agreement
| dataset   | role   |   median_spearman_IG_vs_occlusion |
|:----------|:-------|----------------------------------:|
| cmx7      | M_base |                             0.393 |
| cmx7      | M_prop |                             0.519 |
| cmx7      | M_ref  |                             0.535 |
| cog       | M_base |                             0.38  |
| cog       | M_prop |                             0.518 |
| cog       | M_ref  |                             0.542 |

### CMx7 region shares by task group
| role   | task_group      |   frontal_polar_eye |   frontal |   temporal_emg |   central_motor |   parietal_occipital |
|:-------|:----------------|--------------------:|----------:|---------------:|----------------:|---------------------:|
| M_base | cognitive       |              0.1342 |    0.1581 |         0.138  |          0.2557 |               0.314  |
| M_base | cognitive_motor |              0.1199 |    0.1568 |         0.1467 |          0.211  |               0.3656 |
| M_base | motor           |              0.0944 |    0.1481 |         0.1761 |          0.2547 |               0.3267 |
| M_prop | cognitive       |              0.1327 |    0.1505 |         0.2055 |          0.2011 |               0.3102 |
| M_prop | cognitive_motor |              0.0964 |    0.1199 |         0.2088 |          0.1987 |               0.3762 |
| M_prop | motor           |              0.1825 |    0.1863 |         0.162  |          0.254  |               0.2153 |
| M_ref  | cognitive       |              0.1286 |    0.1668 |         0.1833 |          0.2224 |               0.2988 |
| M_ref  | cognitive_motor |              0.0968 |    0.1206 |         0.1955 |          0.2165 |               0.3706 |
| M_ref  | motor           |              0.1487 |    0.1655 |         0.1675 |          0.3289 |               0.1894 |
