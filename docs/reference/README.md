# Final Project: Regression Analysis

**Author:**  James Pinkston<br>
**Date:**  November 25, 2025

[Project File](https://github.com/james-0177/ml_regression_pinkston/blob/main/notebooks/regression_pinkston.ipynb)

[Documentation]()

[Peer Review]()

## Overview

This project uses a Titanic dataset to build classification models predicting survival. Two models were trained: Decision Tree and Random Forest. Key preprocessing steps, feature engineering, and evaluation metrics are included.

## Usage

Fork this repo and rename it as you see fit. Then clone down to your local machine.

Create a virtual environment:
```shell
uv venv
```

### Run the following test and prepatory commands

```shell
git add .
uvx ruff check --fix
uvx pre-commit autoupdate
uv run pre-commit run --all-files
git add .
```


### Activate Project Virtual Environment

```shell
.\.venv\Scripts\activate
```

### Install dependencies

```shell
uv sync --extra dev --extra docs --upgrade
uv run pytest
```

### Run the Jupyter Notebook

notebooks/regression_pinkston.ipynb

## Project Details

### Dataset

- Source: data/insurance.csv
- Key Features: age, sex, bmi, children, smoker, region, charges
- Target Variable: charges

### Data Exploration

- Scatter matrix for numeric features (age, bmi, children, charges)
- Violin plots for numeric feature distributions (age, bmi)
- Count plots for categorical variables (sex, smoker, region)
- Histograms to identify patterns, outliers, and anomalies
- Categorical variables encoded numerically
  - sex:  male = 0, female = 1
  - smoker:  no = 0, yes = 1
  - region:  northwest = 0, northeast = 1, southwest = 2, southeast = 3

### Feature Selection and Justification

X = [age, bmi, smoker]
y = charges

These features (age, bmi, and smoker) have clear, well-documented relationships with medical costs and represent meaningful predictors of insurance charges.

### Regression Models

1. Linear Regression
2. StandardScaler
3. Polynomial Features

### Evaluation

Linear R^2: 0.778
Linear RMSE: 5874.76
Linear MAE: 4260.56

Pipeline 1 R^2: 0.778
Pipeline 1 RMSE: 5874.76
Pipeline 1 MAE: 4260.56

Pipeline 2 R^2: 0.861
Pipeline 2 RMSE: 4637.02
Pipeline 2 MAE: 2838.44

## Reflections

**<span style="color: darkgreen">This project reinforced that age, BMI, and smoking status are strong predictors of insurance charges. The baseline Linear Regression and Pipeline 1 (StandardScaler) models performed nearly the same, showing that scaling alone does not significantly impact Linear Regression performance. Pipeline 2 (Polynomial Features) improved both training and test R^2 while lowering RMSE and MAE, indicating that capturing non-linear relationships can meaningfully improve model accuracy. Overall, I learned the importance of preprocessing, feature engineering, and carefully evaluating models to balance complexity and generalization.</span>**
