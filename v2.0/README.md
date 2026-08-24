# Dynamic Safe Screening for Robust Support Vector Machines — Version 2.0

This directory contains the revised implementation, experimental results,
statistical analyses, and figures associated with Version 2.0 of the paper
on Dynamic Safe Screening for Robust Support Vector Machines (R-SVM).

Version 2.0 contains the updated code and results corresponding to the
revised experimental study. It is organized separately from Version 1.0,
which preserves the previous implementation and experimental results.

The supplied experimental result files allow the reported analyses and
figures to be reproduced without rerunning the complete optimization
benchmark.

---

## Version 2.0 Structure

v2.0/
├── README.md
│   └── Documentation and reproduction instructions for Version 2.0.
│
├── code/
│   └── Paper_SS-RSVM_final.ipynb
│       └── Final notebook containing the R-SVM implementation,
│           dynamic safe screening method, experiments,
│           statistical analyses, and visualization.
│
├── requirements.txt
│   └── Python dependencies required to run the notebook.
│
├── data/
│   └── Dataset-related files used by the experiments,
│       when applicable.
│
├── results/
│   ├── master_results.csv
│   │   └── Complete experimental results across datasets,
│   │       solvers, parameters, methods, and random seeds.
│   │
│   ├── fastness_results.csv
│   │   └── Aggregated computational-efficiency results.
│   │
│   ├── objective_accuracy_results.csv
│   │   └── Objective-value and predictive-performance
│   │       comparisons between baseline and screened R-SVM.
│   │
│   └── objective_accuracy_results_summary.csv
│       └── Summary of the predictive-equivalence analysis.
│
└── figures/
    ├── performance_analysis.pdf
    ├── objective_difference.pdf
    ├── accuracy_difference.pdf
    ├── auc_difference.pdf
    └── f1_difference.pdf
        └── Figures generated from the Version 2.0 results.
---

# 1. Method

Version 2.0 implements Robust Support Vector Machine (R-SVM) together
with the proposed Dynamic Safe Screening method.

The screening procedure identifies training samples whose optimal dual
variables can be safely determined to lie at their boundary values.
These samples can then be excluded from the subsequent optimization
problem without changing the optimal solution, subject to the numerical
accuracy of the optimization solver.

The implementation provides two compared methods:

1. R-SVM (Baseline)

   The original R-SVM optimization without safe screening.

2. R-SVM + Safe Screening

   The R-SVM implementation equipped with the proposed Dynamic Safe
   Screening procedure.

---

# 2. Experimental Setup

## 2.1 Datasets

Three benchmark binary-classification datasets are used in Version 2.0:

| Dataset | Samples | Features |
|:--|--:|--:|
| svmguide1 | 3,089 | 4 |
| phishing | 11,055 | 68 |
| ijcnn1 | 49,990 | 22 |

The datasets are loaded and preprocessed using the procedures implemented
in the notebook.

---

## 2.2 Data Preprocessing

The input features are standardized using `StandardScaler`.

For each random seed, the data are divided into:

- Training set: 64%
- Validation set: 16%
- Test set: 20%

The validation set is used for model-related procedures implemented in
the notebook, while the test set is used for final predictive evaluation.

---

## 2.3 Random Seeds

Each experimental configuration is evaluated over 30 random seeds.

The random seed is explicitly stored in `master_results.csv`, allowing
the baseline and screened R-SVM results to be paired using identical
data splits.

---

## 2.4 Optimization Solvers

Two optimization solvers are evaluated:

- SCS
- CVXOPT

Both solvers are applied to the same R-SVM formulation and screening
procedure.

---

## 2.5 Initialization Strategies

Two initialization strategies are considered:

- Cold-start: the solver starts without reusing a previous solution.
- Warm-start: the solver is allowed to reuse a previous solution when
  applicable.

---

## 2.6 Regularization Parameter

The following values of the regularization parameter are evaluated:

C ∈ {0.01, 0.05, 0.1}

---

## 2.7 Uncertainty Radius

The following uncertainty-radius values are evaluated:

rho ∈ {0.0, 0.05}

The case rho = 0.0 corresponds to the nominal setting, while rho = 0.05
represents the robust setting considered in the experiments.

---

## 2.8 Compared Methods

For every experimental configuration, the following methods are compared:

- R-SVM (Baseline)
- R-SVM + Safe Screening

The baseline method solves the complete optimization problem, whereas
the screened method applies Dynamic Safe Screening before solving the
reduced problem.

---

# 3. Experimental Configurations

The Version 2.0 benchmark considers:

- 3 datasets
- 2 solvers
- 2 initialization strategies
- 3 values of C
- 2 values of rho
- 2 methods
- 30 random seeds

Therefore, the complete benchmark contains:

3 × 2 × 2 × 3 × 2 × 2 × 30 = 4320

individual experimental runs.

---

# 4. Solver Settings

The optimization experiments use:

- Maximum iterations: 4,000
- Solver tolerance: 1e-6

The exact optimization model, screening procedure, and solver calls are
implemented in:

code/Paper_SS-RSVM_final.ipynb

---

# 5. Evaluation Metrics

The experiments evaluate both computational efficiency and predictive
performance.

## 5.1 Computational Metrics

The following metrics are recorded:

- Training/solve time
- Safe-screening time
- Total screening time
- Speedup
- Screening rate
- Number of solver iterations

The speedup is defined as:

Speedup = Baseline time /
          (Screening solve time + Screening overhead time)

where:

- Baseline time is the training time of the baseline R-SVM.
- Screening solve time is the optimization time after safe screening.
- Screening overhead time is the time required to perform the screening
  procedure.

---

## 5.2 Predictive Metrics

The following predictive metrics are reported:

- Objective value
- Accuracy
- AUC
- F1-score

These metrics are evaluated for both the baseline and screened R-SVM
methods.

---

# 6. Statistical Analysis

## 6.1 Computational Efficiency

The computational performance of the baseline and screened methods is
compared using paired statistical testing across matched random seeds.

The pairing is performed using the same:

- Dataset
- Solver
- Initialization strategy
- C
- rho
- Random seed

This ensures that the computational comparison is based on matched
experimental runs.

---

## 6.2 Predictive Equivalence

Predictive equivalence between the baseline and screened methods is
evaluated using paired Two One-Sided Tests (TOST).

The analysis considers:

- Objective value
- Accuracy
- AUC
- F1-score

The equivalence margins used in Version 2.0 are specified directly in
the notebook.

The resulting p-values and summary statistics are stored in:

results/objective_accuracy_results.csv

results/objective_accuracy_results_summary.csv

---

# 7. Provided Results

Version 2.0 provides the processed experimental results required to
reproduce the reported analyses.

## 7.1 master_results.csv

This is the main experimental result file.

It contains results for individual experimental runs, including:

- Dataset
- Solver
- Warm-start setting
- C
- rho
- Method
- Random seed
- Objective
- Accuracy
- AUC
- F1-score
- Screening rate
- Training time
- Screening time
- Number of iterations
- Solver status

---

## 7.2 fastness_results.csv

This file contains aggregated computational-efficiency results.

It includes:

- Baseline time
- Screening solve time
- Screening overhead
- Total screening time
- Speedup
- Screening rate
- Iteration statistics
- Paired statistical-test results

---

## 7.3 objective_accuracy_results.csv

This file contains paired comparisons between baseline R-SVM and
screened R-SVM for:

- Objective value
- Accuracy
- AUC
- F1-score

The file also contains the corresponding statistical equivalence-test
results.

---

## 7.4 objective_accuracy_results_summary.csv

This file provides a compact summary of the predictive-equivalence
analysis, including the proportion of experimental configurations that
satisfy the specified equivalence criteria.

---

# 8. Figures

The `figures/` directory contains the figures generated from the
Version 2.0 experimental results.

## performance_analysis.pdf

Comparison of computational performance and safe-screening rates across
the experimental configurations.

## objective_difference.pdf

Differences in objective values between baseline R-SVM and screened
R-SVM.

## accuracy_difference.pdf

Differences in predictive accuracy between the two methods.

## auc_difference.pdf

Differences in AUC between the two methods.

## f1_difference.pdf

Differences in F1-score between the two methods.

---

# 9. Reproducing the Version 2.0 Analysis

The Version 2.0 directory provides the processed CSV result files.
Therefore, the complete optimization benchmark does not need to be
rerun to reproduce the reported analyses and figures.

## Step 1: Install dependencies

From the Version 2.0 directory, install the required Python packages:

    pip install -r requirements.txt

The main dependencies include:

- NumPy
- Pandas
- SciPy
- scikit-learn
- CVXPY
- SCS
- CVXOPT
- Matplotlib
- Seaborn

---

## Step 2: Open the notebook

Open:

    code/Paper_SS-RSVM_final.ipynb

The notebook contains:

- R-SVM implementation
- Dynamic Safe Screening implementation
- Experimental procedures
- Result-processing procedures
- Statistical analyses
- Visualization code

---

## Step 3: Use the provided results

The following files are already provided:

    results/master_results.csv
    results/fastness_results.csv
    results/objective_accuracy_results.csv
    results/objective_accuracy_results_summary.csv

These files contain the experimental results used for the reported
analyses.

Consequently, users can reproduce the statistical analyses and figures
without rerunning all optimization experiments.

---

# 10. Re-running the Full Benchmark

Users who want to independently reproduce the raw experimental results
can rerun the complete experimental pipeline implemented in:

    code/Paper_SS-RSVM_final.ipynb

The full pipeline performs:

1. Dataset loading.
2. Data preprocessing.
3. Train/validation/test splitting.
4. R-SVM optimization.
5. Dynamic Safe Screening.
6. Baseline R-SVM training.
7. Screened R-SVM training.
8. Predictive evaluation.
9. Computational-time measurement.
10. Statistical analysis.
11. Result aggregation.
12. Figure generation.

The full benchmark is substantially more computationally expensive than
reproducing the analysis from the supplied CSV files.

The provided `master_results.csv` therefore serves as the stored
experimental record used to generate the Version 2.0 analyses.

---

# 11. Reproducibility Checklist

Version 2.0 provides:

- [x] Final implementation
- [x] R-SVM baseline implementation
- [x] Dynamic Safe Screening implementation
- [x] Dataset configuration
- [x] Solver configuration
- [x] Experimental parameters
- [x] Random-seed information
- [x] Raw experimental results
- [x] Aggregated computational results
- [x] Predictive-performance results
- [x] Statistical analysis
- [x] Generated figures
- [x] Python dependency list

---

# 12. Computational Environment

The experiments were conducted using Google Colab with a Python CPU
runtime.

The experimental runtime provided approximately 12.7 GB of available
RAM.

The experiments were also developed and tested on a system equipped
with:

- CPU: Intel Core i5-12500H
- CPU frequency: 2.50 GHz
- RAM: 8 GB

The required software dependencies are listed in:

    requirements.txt

---

# 13. Relation to Version 1.0

Version 2.0 is the revised version of the computational study.

The repository keeps Version 1.0 and Version 2.0 separately so that the
previous implementation and results remain preserved and can be compared
with the revised study.

Version 1.0 contains the earlier code, results, and associated materials.

Version 2.0 contains the updated implementation, experimental results,
statistical analyses, and figures corresponding to the revised paper.

This README documents Version 2.0 only.

---

# 14. Citation

If you use the Version 2.0 implementation or experimental results, please
cite the corresponding paper.

The final bibliographic information will be added after publication.

---

# 15. License

The Version 2.0 materials are provided for research and reproducibility
purposes.
