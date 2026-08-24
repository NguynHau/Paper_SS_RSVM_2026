# Safe Screening for Robust Support Vector Machines

This repository contains the implementation of the proposed safe screening
method for Robust Support Vector Machines (R-SVM) and the code used to
reproduce the experiments reported in the paper.

## Datasets

The experiments use the following benchmark binary classification datasets:

- SVMguide1
- Phishing
- Ijcnn1

The datasets are publicly available from the LIBSVM dataset repository.

## Implementation

The main implementation and experimental workflow are provided in:

`Paper_SS-RSVM_final.ipynb`

The notebook contains the implementation of:

- Robust Support Vector Machine (R-SVM)
- Safe screening method
- Baseline and screening-based training
- Cold-start and warm-start initialization
- SCS and CVXOPT solvers
- Experimental evaluation and result analysis

## Reproducibility

The notebook is intended to provide the computational procedures used in the
paper. Experimental settings, including datasets, regularization parameters,
uncertainty radii, solvers, initialization strategies, and random seeds, are
specified in the notebook.

## License

The source code is provided for research and academic use.
