# Paper experiment map

| Paper element | Code | Reference result |
|---|---|---|
| Main i.i.d. table and rank table | `code/harness/run_all.py` | `code/harness/results_final`, `code/harness/results_knn` |
| Frozen-feature vision comparison | `code/harness/run_all.py`, `code/harness/scripts/extract_features.py` | `code/harness/results_vision`, `results_vision_knn` |
| Shifted tabular comparison | same split-aware harness | `code/harness/results_final`, `results_knn` |
| Leave-class OOD comparison | `code/harness/ood_eval.py` | `results_ood`, `results_ood_knn`, `results_ood_rerun` |
| Learned/frozen/identity/shared/single-prototype/no-reg/no-temp ablations | `code/harness/run_ablation.py` | `code/harness/results_ablation` |
| Per-dataset metric gain figure | `code/harness/make_fig_b4_26.py` | `results_final/fig_b4_data_26.csv` |
| `H_ER` metric-selection rule | `code/metric_selection/*.py` | `results/metric_selection`; `results/paper_inputs/fig_6_4_6_5_data.csv` |
| Manuscript aggregate tables | `compute7.py`, `compute_block_means.py` | `reports/ch6/*.json` |
| Main figures and supplementary curves | `make_pr_figures.py` | `figures/pr` after prediction files are regenerated |

## Methods included

The paper comparison contains:

- LPEM
- Mahalanobis OOD
- Weighted kNN
- Conformal Risk Control (CRC)
- Dirichlet calibration
- DUQ
- SelectiveNet

Only the Gaussian evidence member is included. The rational-kernel branch,
GBDT experiments, ImageNette, Omniglot and image OOD experiments are not part of
the submitted paper and are excluded.
