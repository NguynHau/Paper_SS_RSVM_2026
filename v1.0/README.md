# Paper_SS_RSVM_2026

This repository contains the experimental notebooks used for the SS-RSVM algorithm.

## Project Structure

```
Paper_SS_RSVM_2026
│
├── images/                 # Figures used in the paper
│   ├── screeningrate_cancer.pdf
│   ├── time_cancer.pdf
│   ├── screeningrate_spam.pdf
│   └── time_spam.pdf
│
├── src/                    
│   ├── notebooks          # Experiment notebooks
│   │   ├── SS_RSVM_breast_cancer.ipynb
│   │   ├── SS_RSVM_spambase_email.ipynb
│   │   └── SS_RSVM_n_times.ipynb
│   │
│   └── python
│       ├── ss_rsvm_breast_cancer.py
│       └── ss_rsvm_spambase_email.py
│
├── README.md               # Project description
├── LICENSE                 # MIT License
└── .gitignore              # Ignored files
```


## Notebooks

- `ss_rsvm_breast_cancer.ipynb`  
  Experiment on the Breast Cancer dataset.

- `ss_rsvm_spambase_email.ipynb`  
  Experiment on the Spambase email dataset.

- `ss_svm_n_times.ipynb`  
  Runs the SVM experiment multiple times to evaluate average performance.

## Runtime Notes (Google Colab)

The notebooks were executed on Google Colab.

Approximate running times:

- `ss_rsvm_breast_cancer.ipynb`  
  Runtime: ~1 minute

- `ss_rsvm_spambase_email.ipynb`  
  Runtime: ~5–6 minutes

- `ss_svm_n_times.ipynb`  
  Runtime: ~80 minutes depending on the number of iterations.

Note: `ss_svm_n_times.ipynb` may take significantly longer to run because the experiment is executed 100 times to compute the average performance of the model.



## Environment Setup

Install the required Python packages:

```bash
pip install -r requirements.txt
```
