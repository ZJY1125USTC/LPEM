# Dataset sources used in the LPEM paper

Only datasets used in the submitted manuscript are listed. Users must follow the terms of the original data providers. Full per-dataset provenance is stored in the corresponding `SOURCES.json` file.

| Dataset | Role | Split protocol | Source / access ID | Canonical source |
|---|---|---|---|---|
| Wine | I.i.d. tabular | stratified_kfold | OpenML 187 + UCI 109 | https://archive.ics.uci.edu/dataset/109/wine |
| Iris | I.i.d. tabular | stratified_kfold | OpenML 61 + UCI 53 | https://archive.ics.uci.edu/dataset/53/iris |
| Seeds | I.i.d. tabular | stratified_kfold | OpenML 1499 + UCI 236 | https://archive.ics.uci.edu/dataset/236/seeds |
| Ecoli | I.i.d. tabular | stratified_kfold | OpenML 39 + UCI 39 | https://archive.ics.uci.edu/dataset/39/ecoli |
| Parkinsons | I.i.d. tabular | stratified_kfold | OpenML 1488 + UCI 174 | https://archive.ics.uci.edu/dataset/174/parkinsons |
| Heart Disease | I.i.d. tabular | stratified_kfold | OpenML 53 + UCI 45 | https://archive.ics.uci.edu/dataset/45/heart+disease |
| Breast Cancer Wisconsin (Diagnostic) | I.i.d. tabular | stratified_kfold | OpenML 15 + UCI 17 | https://archive.ics.uci.edu/dataset/17/breast+cancer+wisconsin+diagnostic |
| Thyroid Disease | I.i.d. tabular | stratified_kfold | UCI 102 | https://archive.ics.uci.edu/dataset/102/thyroid+disease |
| Dermatology | I.i.d. tabular | stratified_kfold | OpenML 35 + UCI 33 | https://archive.ics.uci.edu/dataset/33/dermatology |
| Mammographic Mass | I.i.d. tabular | stratified_kfold | UCI 161 | https://archive.ics.uci.edu/dataset/161/mammographic+mass |
| Statlog German Credit | I.i.d. tabular | stratified_kfold | OpenML 31 + UCI 144 | https://archive.ics.uci.edu/dataset/144/statlog+german+credit+data |
| Statlog Australian Credit Approval | I.i.d. tabular | stratified_kfold | OpenML 29 + UCI 143 | https://archive.ics.uci.edu/dataset/143/statlog+australian+credit+approval |
| Bank Marketing | I.i.d. tabular | stratified_kfold | OpenML 1461 + UCI 222 | https://archive.ics.uci.edu/dataset/222/bank+marketing |
| Statlog Vehicle Silhouettes | I.i.d. tabular | stratified_kfold | OpenML 54 + UCI 149 | https://archive.ics.uci.edu/dataset/149/statlog+vehicle+silhouettes |
| Image Segmentation | I.i.d. tabular | stratified_kfold | OpenML 36 + UCI 50 | https://archive.ics.uci.edu/dataset/50/image+segmentation |
| Vowel Recognition | Shifted tabular | group_kfold | OpenML 307 + UCI 152 | https://archive.ics.uci.edu/dataset/152/connectionist+bench+vowel+recognition+deterding+data |
| Optical Recognition of Handwritten Digits | I.i.d. tabular | stratified_kfold | OpenML 28 + UCI 80 | https://archive.ics.uci.edu/dataset/80/optical+recognition+of+handwritten+digits |
| Adult | I.i.d. tabular | stratified_kfold | OpenML 1590 + UCI 2 | https://archive.ics.uci.edu/dataset/2/adult |
| Spambase | I.i.d. tabular | stratified_kfold | OpenML 44 + UCI 94 | https://archive.ics.uci.edu/dataset/94/spambase |
| Human Activity Recognition Using Smartphones | Shifted tabular | group_kfold | UCI 240 | https://archive.ics.uci.edu/dataset/240/human+activity+recognition+using+smartphones |
| Pima Indians Diabetes | I.i.d. tabular | stratified_kfold | UCI 34 | https://archive.ics.uci.edu/dataset/34/diabetes |
| Credit Card Fraud | I.i.d. tabular | stratified_kfold | Kaggle mlg-ulb/creditcardfraud | https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud |
| Lending Club | I.i.d. tabular | stratified_kfold | Kaggle wordsforthewise/lending-club | https://www.kaggle.com/datasets/wordsforthewise/lending-club |
| Home Credit Default Risk | I.i.d. tabular | stratified_kfold | Kaggle rakeshnereduapalli/home-credit-default-risk | https://www.kaggle.com/datasets/rakeshnereduapalli/home-credit-default-risk |
| Occupancy Detection | Shifted tabular | time_series | UCI 357 | https://archive.ics.uci.edu/dataset/357/occupancy+detection |
| Gas Sensor Array Drift | Shifted tabular | group_kfold | UCI 224 | https://archive.ics.uci.edu/dataset/224/gas+sensor+array+drift+dataset |
| MNIST | Frozen-feature vision | stratified_kfold | MNIST distribution (Google CVDF) | https://storage.googleapis.com/cvdf-datasets/mnist/ |
| CIFAR-10 | Frozen-feature vision | stratified_kfold | Original CIFAR-10 + uoft-cs/cifar10 mirror | https://www.cs.toronto.edu/~kriz/cifar.html |
| CUB-200-2011 | Frozen-feature vision | stratified_kfold | Original CUB-200-2011 + bentrevett mirror | https://www.vision.caltech.edu/datasets/cub_200_2011/ |

## Leave-class OOD protocol

The leave-class OOD results are not separate source datasets. They are derived evaluation protocols built from Optical Digits, Segment, Vehicle, Vowel, and HAR. For each seed, two classes are removed before training and used only as out-of-distribution inputs at test time.

## Notes

- Stratified 5-fold cross-validation is used unless another split is shown.
- Vowel uses speaker-disjoint folds; HAR uses subject-disjoint folds; Gas Sensor Drift uses batch-disjoint folds; Occupancy Detection uses a chronological split.
- Credit Card Fraud, Lending Club, and Home Credit were packaged from the mirror URLs stored in the CSV and `SOURCES.json`; their Kaggle references are retained as the canonical source identifiers.
- CIFAR-10 and CUB-200-2011 were packaged from Hugging Face mirrors of the original image collections; the official project pages are listed as canonical sources.
- MNIST, CIFAR-10, and CUB-200-2011 use frozen ResNet-18 ImageNet penultimate features (512 dimensions).
- ImageNette, Omniglot, image OOD sets, and excluded pilot datasets are not part of the manuscript.
