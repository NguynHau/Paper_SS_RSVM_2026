# Paper_SS-RSVM — Version 1.0

This directory contains the original implementation and experimental
notebooks for the SS-RSVM algorithm.

Version 1.0 preserves the earlier experimental code, datasets,
visualizations, and implementation used in the initial study.

## Project Structure
```
v1.0/
│
├── images/                         # Figures used in the original study
│   ├── screeningrate_cancer.pdf
│   ├── time_cancer.pdf
│   ├── screeningrate_spam.pdf
│   └── time_spam.pdf
│
├── src/
│   │
│   ├── notebooks/                  # Original experiment notebooks
│   │   ├── SS_RSVM_breast_cancer.ipynb
│   │   ├── SS_RSVM_spambase_email.ipynb
│   │   └── SS_RSVM_n_times.ipynb
│   │
│   └── python/                     # Original Python implementations
│       ├── ss_rsvm_breast_cancer.py
│       └── ss_rsvm_spambase_email.py
│
├── README.md                       # Version 1.0 documentation
├── LICENSE                         # MIT License
└── .gitignore                      # Ignored files
```

## Notebooks

### SS_RSVM_breast_cancer.ipynb

Original experiment using the Breast Cancer dataset.

The notebook contains the implementation of SS-RSVM and the corresponding
experimental evaluation.

### SS_RSVM_spambase_email.ipynb

Original experiment using the Spambase email dataset.

The notebook evaluates the SS-RSVM method on the Spambase dataset and
records the corresponding computational results.

### SS_RSVM_n_times.ipynb

Repeated SS-RSVM experiments used to evaluate average computational
performance.

The experiment runs the model multiple times and aggregates the resulting
performance measurements.


## Python Implementations

The `src/python/` directory contains the original Python implementations
used by the experimental notebooks.

### ss_rsvm_breast_cancer.py

Implementation of SS-RSVM for the Breast Cancer experiment.

### ss_rsvm_spambase_email.py

Implementation of SS-RSVM for the Spambase email experiment.


## Datasets

Version 1.0 uses the following benchmark datasets:

- Breast Cancer
- Spambase

The corresponding dataset-loading and preprocessing procedures are
implemented in the experimental notebooks and Python source files.


## Experimental Evaluation

The original experiments evaluate the computational behavior of SS-RSVM,
including:

- Screening rate
- Computational time
- Repeated-run performance

The figures generated from the original experiments are stored in the
`images/` directory.


## Runtime Notes (Google Colab)

The original notebooks were executed using Google Colab.

Approximate running times are:

- `SS_RSVM_breast_cancer.ipynb`
  Runtime: approximately 1 minute

- `SS_RSVM_spambase_email.ipynb`
  Runtime: approximately 5–6 minutes

- `SS_RSVM_n_times.ipynb`
  Runtime: approximately 80 minutes, depending on the number of iterations

The repeated experiment may take substantially longer because the model
is executed multiple times to estimate average computational performance.


## Environment Setup

Install the required Python packages using:

    pip install -r requirements.txt

The required dependencies depend on the implementation and notebook being
executed.


## Running the Experiments

The notebooks can be opened directly in Google Colab or a compatible
Jupyter environment.

For Google Colab:

1. Open the desired notebook.
2. Install the required dependencies if necessary.
3. Run the notebook cells sequentially.
4. Follow the dataset-loading and experiment instructions provided in the
   notebook.


## Relation to Version 2.0

Version 1.0 contains the original implementation and experimental results
of the SS-RSVM study.

The revised implementation and expanded experimental evaluation are
provided separately in `v2.0/`.

Version 1.0 is preserved for historical reference and reproducibility of
the original experiments, while Version 2.0 contains the updated
implementation and results corresponding to the revised study.


## License

The materials in Version 1.0 are distributed under the MIT License.
