# AlphaCare Insurance Solutions (ACIS) - Car Insurance Analytics

This repository contains the data analysis and predictive modeling work for optimizing car insurance marketing and risk assessment for AlphaCare Insurance Solutions (ACIS) in the South African market.

## Project Overview

The primary goal of this project is to leverage historical insurance claim data to derive actionable insights that can:

1.  **Optimize Marketing Strategy:** Identify low-risk customer segments and geographic areas to target with competitive premium rates.
2.  **Enhance Risk Assessment:** Build predictive models to more accurately price premiums based on a client's risk profile.
3.  **Improve Profitability:** Ensure that premiums collected are sufficient to cover claims and generate a healthy profit margin.

This project is built with reproducibility and compliance in mind, utilizing **Git** for code versioning and **Data Version Control (DVC)** for managing large datasets.

## Table of Contents

- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation and Setup](#installation-and-setup)
- [How to Run the Analysis](#how-to-run-the-analysis)
- [Data Pipeline with DVC](#data-pipeline-with-dvc)

## Project Structure

```
acis-analytics-project/
├── .dvc/                   # DVC metadata and configuration
├── data/
│   └── MachineLearningRating_v3.txt.dvc  # DVC pointer to our raw dataset
├── .gitignore              # Files and directories ignored by Git
├── initial_analysis.py     # Python script for initial hypothesis testing
└── README.md               # This file
```

- **`initial_analysis.py`**: Contains the code for data cleaning, feature engineering, and initial A/B hypothesis testing.
- **`data/`**: This directory holds the DVC pointer files. The actual data is stored in a separate DVC remote storage.

## Getting Started

Follow these instructions to set up the project on your local machine for analysis and development.

### Prerequisites

You will need the following software installed on your system:

- [Git](https://git-scm.com/)
- [Python](https://www.python.org/downloads/) (version 3.8 or higher)
- [pip](https://pip.pypa.io/en/stable/installation/) (Python's package installer)

### Installation and Setup

1.  **Clone the Git Repository:**

    ```bash
    git clone <your-repository-url>
    cd acis-analytics-project
    ```

2.  **Install Python Dependencies:**
    This project uses `pandas` for data manipulation and `scipy` for statistical analysis. Install them using the provided `requirements.txt` file (or manually if one isn't present).

    ```bash
    pip install pandas scipy dvc
    ```

3.  **Pull the Data with DVC:**
    The dataset is version-controlled with DVC. To download the data tracked by the current Git commit, run:
    ```bash
    dvc pull
    ```
    This command will read the `.dvc` file in the `data/` directory and download the corresponding version of `MachineLearningRating_v3.txt` from the configured remote storage.

## How to Run the Analysis

Once the setup is complete, you can run the initial analysis script to see the results of the hypothesis tests.

```bash
python initial_analysis.py
```

The script will output the results of the statistical tests directly to your console, indicating whether there are significant differences in risk and profitability across provinces, zip codes, and genders.

## Data Pipeline with DVC

This project uses DVC to manage the large dataset (`MachineLearningRating_v3.txt`), which is too large to be stored in Git.

- **How it Works:** Git tracks a small "pointer" file (`.dvc` file) that contains a unique hash of the data. DVC uses this hash to retrieve the correct version of the data from a remote storage location (e.g., a local directory, Google Drive, or an S3 bucket).

- **Updating the Data:** If you modify the dataset or add a new one, follow this workflow:
  1.  **Track the new data:** `dvc add data/<your-data-file>`
  2.  **Commit the pointer file to Git:** `git add data/<your-data-file>.dvc` and `git commit -m "feat: Add new version of dataset"`
  3.  **Push the data to remote storage:** `dvc push`

This ensures that our data versions are always synchronized with our code versions, making every result fully reproducible for auditing and compliance.
