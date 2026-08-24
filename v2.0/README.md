# Dynamic Safe Screening for Robust Support Vector Machines

This repository contains the implementation, experimental results, statistical analyses, and figures for the paper on Dynamic Safe Screening for Robust Support Vector Machines (R-SVM).

The repository is designed to facilitate reproducibility of the reported experiments. The complete experimental results are provided in the `results/` directory, allowing the reported analyses and figures to be reproduced without rerunning the full optimization benchmark.

---

## Repository Structure

Paper_SS-RSVM/
|
|-- Paper_SS-RSVM_final.ipynb
|   `-- Final notebook containing the R-SVM implementation,
|       dynamic safe screening method, experiments,
|       statistical analyses, and visualization.
|
|-- README.md
|   `-- Documentation and reproduction instructions.
|
|-- requirements.txt
|   `-- Python dependencies required to run the notebook.
|
|-- data/
|   `-- Dataset-related files used by the experiments,
|       when applicable.
|
|-- results/
|   |
|   |-- master_results.csv
|   |   `-- Complete experimental results across all
|   |       datasets, solvers, parameters, methods, and seeds.
|   |
|   |-- fastness_results.csv
|   |   `-- Aggregated computational-efficiency results.
|   |
|   |-- objective_accuracy_results.csv
|   |   `-- Objective-value and predictive-performance
|   |       comparisons between baseline and screened R-SVM.
|   |
|   `-- objective_accuracy_results_summary.csv
|       `-- Summary of the statistical equivalence analysis.
|
`-- figures/
    |
    |-- performance_analysis.pdf
    |-- objective_difference.pdf
    |-- accuracy_difference.pdf
    |-- auc_difference.pdf
    `-- f1_difference.pdf
        `-- Figures generated from the experimental results.

---

## Method

This repository implements Robust Support Vector Machine (R-SVM) together with the proposed Dynamic Safe Screening method.

The screening procedure identifies training samples whose optimal dual variables can be safely determined to be at their boundary values. These samples can then be excluded from the subsequent optimization problem without changing the optimal solution, up to numerical solver tolerance.

The implementation supports both the baseline R-SVM formulation and the proposed R-SVM with safe screening.

---

# Experimental Setup

## Datasets

Three benchmark binary-classification datasets are used:

| Dataset | Samples | Features |
|:--|--:|--:|
| svmguide1 | 3,089 | 4 |
| phishing | 11,055 | 68 |
| ijcnn1 | 49,990 | 22 |

The datasets are loaded using the procedures implemented in the notebook and are preprocessed before optimization.

---

## Data Preprocessing

The input features are standardized using StandardScaler.

For each random seed, the data are divided into:

- Training set: 64%
- Validation set: 16%
- Test set: 20%

The validation set is used for model-related procedures implemented in the notebook, while the test set is used for final predictive evaluation.

---

## Random Seeds

Each experimental configuration is evaluated over 30 random seeds.

The random seed is explicitly stored in `master_results.csv`, allowing baseline and screened R-SVM results to be paired using the same data split.

---

## Optimization Solvers

Two optimization solvers are evaluated:

- SCS
- CVXOPT

Both solvers are used for the same R-SVM formulation and screening procedure.

---

## Initialization Strategies

Two initialization strategies are considered:

- Cold-start: the solver starts without reusing a previous solution.
- Warm-start: the solver is allowed to reuse a previous solution when applicable.

---

## Regularization Parameter

The following values of the regularization parameter are evaluated:

C ∈ {0.01, 0.05, 0.1}

---

## Uncertainty Radius

The following uncertainty-radius values are evaluated:

rho ∈ {0.0, 0.05}

The case rho = 0.0 corresponds to the nominal setting, while rho = 0.05 represents the robust setting considered in the experiments.

---

## Compared Methods

Each experimental configuration compares:

1. R-SVM (Baseline)

   The original R-SVM optimization without safe screening.

2. R-SVM + Safe Screening

   The proposed R-SVM implementation equipped with dynamic safe screening.

---

## Experimental Configurations

The benchmark considers:

- 3 datasets
- 2 solvers
- 2 initialization strategies
- 3 values of C
- 2 values of rho
- 2 methods
- 30 random seeds

Thus, the complete benchmark contains:

3 × 2 × 2 × 3 × 2 × 2 × 30 = 4320

individual experimental runs.

---

## Solver Settings

The optimization experiments use:

- Maximum iterations: 4,000
- Solver tolerance: 1e-6

The exact solver configuration and optimization model are implemented in:

Paper_SS-RSVM_final.ipynb

---

# Evaluation Metrics

The experiments evaluate both computational efficiency and predictive performance.

## Computational Metrics

The following computational metrics are recorded:

- Training/solve time
- Safe-screening time
- Total screened time
- Speedup
- Screening rate
- Number of solver iterations

The speedup is defined as:

Speedup = Baseline time / (Screening solve time + Screening overhead time)

where:

- Baseline time is the training time of the baseline R-SVM.
- Screening solve time is the optimization time after safe screening.
- Screening overhead time is the time required to perform the screening procedure.

---

## Predictive Metrics

The following predictive metrics are reported:

- Objective value
- Accuracy
- AUC
- F1-score

These metrics are computed for both the baseline and screened R-SVM models.

---

# Statistical Analysis

## Computational Efficiency

The baseline and screened methods are compared using paired statistical testing across matched random seeds.

The pairing is performed using the same:

- Dataset
- Solver
- Initialization strategy
- C
- rho
- Random seed

This ensures that the computational comparison is performed on matched experimental runs.

---

## Predictive Equivalence

Predictive equivalence between the baseline and screened methods is evaluated using paired Two One-Sided Tests (TOST).

The analysis considers:

- Objective value
- Accuracy
- AUC
- F1-score

The equivalence margins used in the experiments are defined directly in the notebook.

The resulting p-values and summary statistics are stored in:

results/objective_accuracy_results.csv

results/objective_accuracy_results_summary.csv

---

# Provided Results

The repository includes the complete experimental results required to reproduce the reported analysis.

## master_results.csv

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

## fastness_results.csv

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

## objective_accuracy_results.csv

This file contains paired comparisons between baseline R-SVM and screened R-SVM for:

- Objective value
- Accuracy
- AUC
- F1-score

The file also contains the corresponding statistical equivalence-test results.

---

## objective_accuracy_results_summary.csv

This file contains a compact summary of the predictive-equivalence analysis, including the proportion of experimental configurations satisfying the specified equivalence criteria.

---

# Figures

The `figures/` directory contains the figures generated from the provided experimental results.

### performance_analysis.pdf

Comparison of computational performance and safe-screening rates across the experimental configurations.

### objective_difference.pdf

Differences in objective values between baseline R-SVM and screened R-SVM.

### accuracy_difference.pdf

Differences in predictive accuracy between the two methods.

### auc_difference.pdf

Differences in AUC between the two methods.

### f1_difference.pdf

Differences in F1-score between the two methods.

---

# Reproducing the Reported Analysis

The repository provides the processed CSV results, so the full optimization benchmark does not need to be rerun to reproduce the reported analysis.

## Step 1: Clone the repository

    git clone https://github.com/NguynHau/Paper_SS-RSVM.git
    cd Paper_SS-RSVM

## Step 2: Install dependencies

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

## Step 3: Open the notebook

Open:

Paper_SS-RSVM_final.ipynb

The notebook contains the implementation, result-processing procedures, statistical analyses, and visualization code.

---

## Step 4: Reproduce the analysis from the provided results

The following files are already included:

- results/master_results.csv
- results/fastness_results.csv
- results/objective_accuracy_results.csv
- results/objective_accuracy_results_summary.csv

Therefore, users can reproduce the reported tables, statistical analyses, and figures using the supplied results without rerunning the complete optimization benchmark.

---

# Re-running the Full Benchmark

Users who want to independently reproduce the raw experimental results can rerun the complete experimental pipeline in the notebook.

The full pipeline performs:

1. Dataset loading.
2. Data preprocessing.
3. Train/validation/test splitting.
4. R-SVM optimization.
5. Dynamic safe screening.
6. Baseline R-SVM training.
7. Screened R-SVM training.
8. Predictive evaluation.
9. Computational-time measurement.
10. Statistical analysis.
11. Result aggregation.
12. Figure generation.

The full benchmark is substantially more computationally expensive than reproducing the analysis from the supplied CSV files.

The provided `master_results.csv` therefore serves as the stored experimental record used to generate the reported analysis.

---

# Reproducibility Checklist

The repository provides:

- [x] Final implementation
- [x] R-SVM baseline implementation
- [x] Dynamic safe screening implementation
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

# Computational Environment

The experiments were conducted using Google Colab with a Python CPU runtime.

The experimental environment provided approximately 12.7 GB of available RAM.

The experiments were also developed and tested on a system equipped with:

- CPU: Intel Core i5-12500H
- CPU frequency: 2.50 GHz
- RAM: 8 GB

The exact software dependencies are listed in:

requirements.txt

---

# Code Availability

The source code and experimental results are publicly available at:

https://github.com/NguynHau/Paper_SS-RSVM

An archived version is also available on Zenodo:

https://doi.org/10.18996767

---

# Citation

If you use this implementation or the experimental results, please cite the corresponding paper.

The final bibliographic information will be added after publication.

---

# License

This repository is provided for research and reproducibility purposes.
