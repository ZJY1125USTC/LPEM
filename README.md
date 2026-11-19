# LPEM
A probabilistic head that couples multiple learnable prototypes with class-specific low-rank metrics and monotone distance-to-evidence functions.
# LPEM

Research code and datasets used in the Pattern Recognition submission
"Learnable Prototype Evidence Machine" (LPEM).

## Layout

- `code/harness`: main experiment harness, LPEM implementation, seven compared
  methods, OOD evaluation, ablations, frozen-feature extraction, and the frozen
  result CSVs used by the manuscript.
- `code/metric_selection`: fold-wise class-geometry analysis and the
  effective-rank heterogeneity (`H_ER`) prescreen used in Section 6.5.
- `datasets/data`: the 26 tabular datasets used in the paper.
- `datasets/features`: frozen ResNet-18 512-dimensional features for MNIST,
  CIFAR-10 and CUB-200-2011.
- `results/metric_selection`: reference metric-selection outputs and figures.
- `results/paper_inputs`: frozen per-dataset outcomes used to construct the metric-selection analysis.
- `MANIFEST.csv`: source path, destination path, byte size and SHA-256 for every
  copied dataset file.
- `PAPER_EXPERIMENT_MAP.md`: mapping from paper experiments to code and result
  files.

## Dataset scope

The package contains only datasets used in the manuscript:

- 22 i.i.d. tabular datasets
- 4 shifted tabular datasets: Vowel, HAR, Gas Sensor Drift, Occupancy Detection
- 3 frozen-feature vision datasets: MNIST, CIFAR-10, CUB-200-2011
- 5 leave-class OOD tasks, constructed from Optical Digits, Segment, Vehicle,
  Vowel and HAR

Vision dataset raw files are included because `code/harness/scripts/extract_features.py`
is the code that produced the frozen features. ImageNette, Omniglot, the image OOD
sets and all excluded or pilot datasets are not included.

## Environment

Use Python 3.11 and install the pinned environment:

```powershell
python -m pip install -r E:\LPEM\requirements.txt
```

Run harness commands from `E:\LPEM\code\harness` so the relative data root in
`datasets.yaml` resolves correctly.

```powershell
Set-Location E:\LPEM\code\harness
```

## Main experiment

```powershell
python run_all.py `
  --groups tabular_small tabular_medical tabular_credit tabular_multiclass tabular_large risk `
  --folds 5 --seeds 0 1 2 3 4 `
  --results-dir results_final --pred-dir predictions_final

python run_all.py `
  --groups vision --folds 5 --seeds 0 1 2 3 4 `
  --results-dir results_vision --pred-dir predictions_vision
```

`run_all.py` runs Mahalanobis, wkNN, CRC, Dirichlet calibration, LPEM, DUQ and
SelectiveNet through the same split, preprocessing and metric pipeline.

## Ablation

The default ablation list in `run_ablation.py` is the 26-dataset tabular sweep.

```powershell
python run_ablation.py `
  --variants full no_temp single_proto fixed_metric fixed_identity shared_metric no_reg `
  --folds 5 --seeds 0 1 2
```

## OOD evaluation

```powershell
python ood_eval.py `
  --dataset optical_digits segment vehicle vowel har `
  --holdout 2 --method mahalanobis crc dirichlet lpem duq selective `
  --score evidence --seeds 0 1 2 3 4 --results-dir results_ood

python ood_eval.py `
  --dataset optical_digits segment vehicle vowel har `
  --holdout 2 --method wknn --score negdist --seeds 0 1 2 3 4 `
  --results-dir results_ood_knn
```

LPEM uses its raw evidence score. wkNN uses the negative nearest-neighbour
distance, matching the submitted table.

## Metric selection

```powershell
python E:\LPEM\code\metric_selection\run_metric_selection_geometry.py
python E:\LPEM\code\metric_selection\analyze_metric_selection.py
python E:\LPEM\code\metric_selection\summarize_metric_selection.py
```

These scripts compute fold-wise Ledoit-Wolf covariance geometry, dataset-level
`H_ER`, Spearman/bootstrap/leave-one-dataset-out analysis, quartiles, and the
LODO prescreen. The dataset, not an individual fold or seed, is the independent
unit.

## Frozen reference results

`code/harness/results_*` contains the CSV results used to produce the manuscript
tables and figures. Re-running the commands overwrites these directories. To
preserve the submitted numbers, copy them before rerunning.

`results/metric_selection` contains the reference metric-selection CSVs, reports
and figures.
