# Safe Screening for Robust Support Vector Machines

This repository contains the source code, experimental results, figures,
and supplementary materials associated with the paper on safe screening
for Robust Support Vector Machines (R-SVM).

Two versions of the project are preserved in this repository to maintain
transparency and reproducibility.

---

## Repository Versions

### Version 1.0 — Previous Version

The `v1.0/` directory contains the original implementation, experimental
code, and results corresponding to the previous version of the study.

This version is preserved for archival and reproducibility purposes.
It is not the version used for the revised manuscript.

### Version 2.0 — Current Revised Version

The `v2.0/` directory contains the updated implementation, experimental
results, generated figures, and the revised manuscript.

**Version 2.0 is the current version of the study and should be used
for reproducing the results reported in the revised paper.**

The implementation and experiments in v2.0 use the following benchmark
configuration:

- **Datasets:** `svmguide1`, `phishing`, `ijcnn1`
- **Solvers:** SCS, CVXOPT
- **Initialization:** cold-start and warm-start
- **Regularization parameter \(C\):** 0.01, 0.05, 0.1
- **Uncertainty radius \(\rho\):** 0.0, 0.05
- **Methods:** R-SVM and R-SVM + Safe Screening
- **Random seeds:** 30
- **Train/validation/test split:** 64% / 16% / 20%

---

## Current Paper

The revised manuscript corresponding to the current implementation is
located in:

`v2.0/paper/`

Please use the materials in `v2.0/` when referring to the current version
of the paper.

---

## Repository Structure

```text
Paper_SS-RSVM/
│
├── LICENSE
├── README.md
│
├── v1.0/
│   ├── README.md
│   ├── src/
│   │   └── Original implementation
│   │
│   ├── image/
│       └── Original figures/images
│
└── v2.0/
    ├── README.md
    │
    ├── code/
    │   └── Paper_SS-RSVM_final.ipynb
    │
    ├── paper/
    │   └── Revised manuscript
    │
    ├── results/
    │   ├── master_results.csv
    │   ├── fastness_results.csv
    │   ├── objective_accuracy_results.csv
    │   └── objective_accuracy_results_summary.csv
    │
    └── figures/
        ├── performance_analysis.pdf
        ├── objective_difference.pdf
        ├── accuracy_difference.pdf
        ├── auc_difference.pdf
        └── f1_difference.pdf
