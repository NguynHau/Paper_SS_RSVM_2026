# Dynamic Safe Screening for Robust Support Vector Machines

This repository contains the source code, experimental implementations,
results, statistical analyses, and figures associated with the study of
Safe Screening for Robust Support Vector Machines (R-SVM).

Two versions of the computational study are preserved in this repository:

- Version 1.0: Original implementation and experiments.
- Version 2.0: Revised implementation, expanded experiments, updated
  statistical analyses, and results corresponding to the revised paper.

Both versions are preserved to support transparency, historical reference,
and reproducibility.

---

## Repository Structure
```
Paper_SS-RSVM/
│
├── v1.0/
│   │
│   ├── images/
│   │   └── Figures from the original experiments.
│   │
│   ├── src/
│   │   ├── notebooks/
│   │   │   ├── SS_RSVM_breast_cancer.ipynb
│   │   │   ├── SS_RSVM_spambase_email.ipynb
│   │   │   └── SS_RSVM_n_times.ipynb
│   │   │
│   │   └── python/
│   │       ├── ss_rsvm_breast_cancer.py
│   │       └── ss_rsvm_spambase_email.py
│   │
│   └── README.md
│       └── Documentation for Version 1.0.
│
├── v2.0/
│   │
│   ├── code/
│   │   └── Paper_SS-RSVM_final.ipynb
│   │       └── Final implementation and complete experimental pipeline.
│   │
│   ├── data/
│   │   └── Dataset-related files, when applicable.
│   │
│   ├── results/
│   │   ├── master_results.csv
│   │   ├── fastness_results.csv
│   │   ├── objective_accuracy_results.csv
│   │   └── objective_accuracy_results_summary.csv
│   │
│   ├── figures/
│   │   ├── performance_analysis.pdf
│   │   ├── objective_difference.pdf
│   │   ├── accuracy_difference.pdf
│   │   ├── auc_difference.pdf
│   │   └── f1_difference.pdf
│   │
│   ├── requirements.txt
│   └── README.md
│       └── Documentation for Version 2.0.
│
├── README.md
│   └── Overview of the complete repository.
│
├── LICENSE
│   └── Repository license.
│
└── .gitignore
    └── Ignored files and directories.
```
---

# Version 1.0

Version 1.0 preserves the original SS-RSVM implementation and
experimental study.

The original experiments focus on the Breast Cancer and Spambase
datasets and include experiments for evaluating screening rates,
computational time, and repeated-run performance.

The main materials are located in:

    v1.0/

The Version 1.0 documentation is available in:

    v1.0/README.md

Version 1.0 is retained for historical reference and reproducibility of
the original experiments.

---

# Version 2.0

Version 2.0 contains the revised implementation and experimental study
corresponding to the revised paper.

The updated study includes:

- Robust Support Vector Machine (R-SVM)
- Dynamic Safe Screening
- Multiple benchmark datasets
- Multiple optimization solvers
- Cold-start and warm-start initialization
- Multiple regularization parameters
- Multiple uncertainty-radius settings
- Computational-efficiency evaluation
- Predictive-performance evaluation
- Paired statistical analyses
- Predictive-equivalence analysis
- Reproducible experimental result files
- Generated figures

The main materials are located in:

    v2.0/

The Version 2.0 documentation is available in:

    v2.0/README.md

For the revised paper and current experimental results, Version 2.0
should be considered the primary version of the repository.

---

# Version Comparison

| Feature | Version 1.0 | Version 2.0 |
|:--|:--|:--|
| Purpose | Original study | Revised study |
| R-SVM | Yes | Yes |
| Safe Screening | Yes | Dynamic Safe Screening |
| Datasets | Breast Cancer, Spambase | svmguide1, phishing, ijcnn1 |
| Solvers | Original implementation | SCS, CVXOPT |
| Cold-start | Original experiments | Yes |
| Warm-start | Original experiments | Yes |
| Statistical analysis | Original analysis | Updated analysis |
| Predictive equivalence | No | Yes |
| Stored experimental results | Limited | Complete |
| Generated figures | Yes | Yes |
| Final revised study | No | Yes |

---

# Reproducibility

The repository distinguishes between two levels of reproducibility.

## Reproducing Version 1.0

See:

    v1.0/README.md

The original notebooks and Python implementations are provided under
`v1.0/src/`.

## Reproducing Version 2.0

See:

    v2.0/README.md

Version 2.0 provides the processed experimental results required to
reproduce the reported statistical analyses and figures without
rerunning the complete optimization benchmark.

The main stored result files are:

    v2.0/results/master_results.csv
    v2.0/results/fastness_results.csv
    v2.0/results/objective_accuracy_results.csv
    v2.0/results/objective_accuracy_results_summary.csv

The final notebook is:

    v2.0/code/Paper_SS-RSVM_final.ipynb

Users who wish to independently reproduce the raw optimization
experiments can rerun the complete experimental pipeline from the
Version 2.0 notebook.

---

# Getting Started

## Version 1.0

Navigate to:

    v1.0/

Then follow the instructions in:

    v1.0/README.md

## Version 2.0

Navigate to:

    v2.0/

Then follow the instructions in:

    v2.0/README.md

---

# Requirements

The required Python dependencies for Version 2.0 are provided in:

    v2.0/requirements.txt

Version 1.0 contains its original implementation and experimental
requirements as documented in:

    v1.0/README.md

---

# Computational Environment

The Version 2.0 experiments were conducted using Google Colab with a
Python CPU runtime.

The experimental runtime provided approximately 12.7 GB of available
RAM.

The experiments were also developed and tested on a system equipped
with:

- CPU: Intel Core i5-12500H
- CPU frequency: 2.50 GHz
- RAM: 8 GB

Further details are provided in:

    v2.0/README.md

---

# Code and Results

The repository is organized so that the original and revised
experimental studies remain separately identifiable.

The original implementation is preserved under:

    v1.0/

The revised implementation and complete stored experimental results are
provided under:

    v2.0/

This organization prevents the revised implementation from overwriting
the original experimental record.

---

# Citation

If you use the implementation, experimental results, or figures from
this repository, please cite the corresponding paper.

The final bibliographic information will be added after publication.

---

# License

This repository is distributed under the license specified in:

    LICENSE
