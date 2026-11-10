# Final Project
    Course: CSC17104 - Programming for Data Science
    Group name: UongMilo

## Group Members

| Student ID | Full Name |
| --- | --- |
| 24127021 | Nguyễn Thành Đạt |
| 24127024 | Trần Huỳnh Mạnh Đạt |
| 24127095 | Vũ Duy Nhất |

## Question Ownership

| Question ID | Research Question | Owner | Type |Supporting Members |
| --- | --- | --- | --- |
| Q1 | TBD | TBD | TBD |
| Q2 | TBD | TBD | TBD |
| Q3 | TBD | TBD | TBD |

## Task Breakdown

| Task | Description | Assignee | Deliverable | Status |
| --- | --- | --- | --- | --- |
| Data collection | Collect the dataset and document its source. | TBD | Raw dataset and source documentation | To do |
| Data exploration and cleaning | Explore data quality and prepare the dataset for analysis. | TBD | Exploration notebook and cleaned dataset | To do |
| Question analysis | Analyze the research questions and visualize findings. | TBD | Analysis notebook | To do |
| Machine learning | Build and evaluate models for the machine learning question. | TBD | Modeling notebook and evaluation results | To do |
| Documentation and review | Summarize findings and review project deliverables. | TBD | Completed README and final notebooks | To do |

Replace `TBD` with the agreed research questions and member names, and update task statuses as work progresses.

## Dataset Description

This project uses **National SBA**, a historical dataset of U.S. Small Business Administration (SBA) guaranteed loans. The SBA guarantees part of a loan to help small businesses obtain financing while reducing the lending bank's exposure to losses. Each row represents a loan, with information about the borrower, lender, business characteristics, loan terms, financing amounts, and repayment outcome.

The dataset accompanies Min Li, Amy Mickel, and Stanley Taylor's (2018) paper, [“Should This Loan be Approved or Denied?”: A Large Dataset with Class Assignment Guidelines](https://doi.org/10.1080/10691898.2018.1434342), published in *Journal of Statistics Education*, 26(1), 55–66. The paper uses historical loan outcomes to teach credit risk assessment: students estimate default probabilities, validate a classification model, and explain a lending recommendation.

### Dataset Overview

| Item | Description |
| --- | --- |
| Local file | [`data/raw/SBAnational.csv`](data/raw/SBAnational.csv) |
| Size | 899,164 records and 27 columns, verified from the local CSV |
| Observation | One SBA-guaranteed loan |
| Geographic scope | The 50 U.S. states and Washington, D.C., as described in the paper |
| Time coverage | The paper describes historical data from 1987–2014; the local `ApprovalFY` column also contains earlier years and the nonstandard value `1976A`, which require investigation during cleaning |
| Target variable | `MIS_Status`: `P I F` means paid in full; `CHGOFF` means charged off/defaulted |
| Local target counts | 739,609 paid in full; 157,558 charged off; 1,997 missing outcomes |
| Main analytical purpose | Explore factors associated with loan repayment and predict default risk |

The columns describe several aspects of each loan:

| Information Group | Example Variables |
| --- | --- |
| Borrower and lender | `Name`, `City`, `State`, `Zip`, `Bank`, `BankState` |
| Business characteristics | `NAICS` (industry), `NoEmp`, `NewExist`, `FranchiseCode`, `UrbanRural` |
| Employment impact | `CreateJob`, `RetainedJob` |
| Loan terms and programs | `ApprovalDate`, `ApprovalFY`, `Term` (months), `RevLineCr`, `LowDoc` |
| Financing amounts | `GrAppv` (bank-approved amount), `SBA_Appv` (SBA-guaranteed amount), `DisbursementGross` |
| Repayment and default | `MIS_Status`, `ChgOffDate`, `ChgOffPrinGr`, `BalanceGross` |

These are outcomes of loans already granted, rather than labels for accepted and rejected applications. Predictions therefore estimate repayment risk within the historical lending population. The paper also provides a separate 2,102-record **SBA Case** subset for California businesses in the real estate and rental and leasing sector; this project uses the full National SBA file.

Before modeling, the data require checks for missing values, inconsistent category codes, currency formatting, and date interpretation. Paid-in-full loans substantially outnumber defaults, so evaluation should account for class imbalance. Predictors must also be available at the intended decision time: default dates and charged-off amounts would reveal the outcome and cause target leakage. Historical coverage and selection of previously granted loans limit how broadly results can be generalized.

### Source and License

- **Original source:** U.S. Small Business Administration, distributed with the [Li, Mickel, and Taylor (2018) paper](https://doi.org/10.1080/10691898.2018.1434342).
- **Dataset distribution:** [Should This Loan be Approved or Denied? on Kaggle](https://www.kaggle.com/datasets/mirbektoktogaraev/should-this-loan-be-approved-or-denied), published by Mirbek Toktogaraev.
- **Dataset license:** The Kaggle distribution lists [Creative Commons Attribution-ShareAlike 4.0 International (CC BY-SA 4.0)](https://creativecommons.org/licenses/by-sa/4.0/). Reuse requires appropriate attribution, a license link, and an indication of changes; shared adaptations must follow the ShareAlike terms.
- **Paper license:** The accompanying article states CC BY 4.0, separately from the Kaggle dataset's listed license.

### Related Public Notebooks

The team noted approximately 40 related public notebooks on Kaggle. These have **not yet been surveyed**, and the count may change. They are available through the dataset's [public notebooks page](https://www.kaggle.com/datasets/mirbektoktogaraev/should-this-loan-be-approved-or-denied/code) for future comparison of cleaning approaches, exploratory analyses, and modeling methods. No notebook-specific findings are claimed here.

## Question List and Key Findings

| Question ID | Research Question | Key Findings | Supporting Evidence | Related Notebook |
| --- | --- | --- | --- | --- |
| Q1 | TBD | Pending analysis | TBD: figure, table, or metric | [Analysis](notebooks/02_analysis.ipynb) |
| Q2 | TBD | Pending analysis | TBD: figure, table, or metric | [Analysis](notebooks/02_analysis.ipynb) |
| Q3 | TBD | Pending analysis | TBD: evaluation metrics and baseline comparison | [Machine learning](notebooks/03_ml_question.ipynb) |

## How to Run the Project

### 1. Prepare the Environment

Install Miniconda or Anaconda and open a terminal with `conda` available (on WSL, use Anaconda Prompt). Navigate to the project root, which contains `environment.yml`:

```powershell
cd /mnt/c/UongMilo-LoanOrNot
```

If your copy is in a different location, adjust the path above. Create and activate the project's Conda environment:

```powershell
conda env create -f environment.yml
conda activate p4ds-finalproject
```

The environment file specifies Python and the dependencies for data processing, visualization, and machine learning. Environment creation requires internet access to download the packages.

### 2. Prepare the Dataset

Ensure `SBAnational.csv` is located at `data/raw/SBAnational.csv`. If it is missing, download and extract it from the [Kaggle dataset page](https://www.kaggle.com/datasets/mirbektoktogaraev/should-this-loan-be-approved-or-denied), then place the CSV in `data/raw/`.

### 3. Launch JupyterLab

With the environment activated, run this command from the project root:

```powershell
jupyter lab
```

Open the local URL printed in the terminal if JupyterLab does not open automatically in your browser. Select the Python kernel belonging to `p4ds-finalproject`. If it is unavailable, register it from the activated environment and refresh JupyterLab:

```powershell
python -m ipykernel install --user --name p4ds-finalproject --display-name "Python (p4ds-finalproject)"
```

### 4. Run the Notebooks

The intended execution order is:

| Order | Notebook | Purpose |
| --- | --- | --- |
| 1 | [`01_collection_exploration.ipynb`](notebooks/01_collection_exploration.ipynb) | Data collection, exploration, and preparation |
| 2 | [`02_analysis.ipynb`](notebooks/02_analysis.ipynb) | Research question analysis and visualizations |
| 3 | [`03_ml_question.ipynb`](notebooks/03_ml_question.ipynb) | Model training and evaluation |

Once the notebooks are implemented, open each one in order and use **Run > Run All Cells** to execute its cells from top to bottom. Save the results before proceeding to the next notebook.

**Current implementation status:** All three notebook files and `src/main.py` are empty placeholders. The steps above describe environment setup and the intended workflow; analysis and model execution will become available after these files are implemented. Empty notebook files must first be saved as valid Jupyter notebooks before they can be opened and executed.

### 5. End the Session

Stop the JupyterLab server with `Ctrl+C` in the terminal and confirm shutdown if prompted. Then deactivate the environment:

```powershell
conda deactivate
```
