# Midterm Project: Classification Analysis

**Author:**  James Pinkston<br>
**Date:**  November 11, 2025

[Project File](https://github.com/james-0177/ml_classification_pinkston/blob/main/notebooks/classification_pinkston.ipynb)

[Documentation](https://james-0177.github.io/ml_classification_pinkston/)

[Peer Review](https://github.com/james-0177/ml_classification_pinkston/blob/main/peer_review.md)

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

notebooks/classification_pinkston.ipynb

## Project Details

### Dataset

- Source: data/train.csv
- Key Features: Age, Fare, Pclass, Sex, FamilySize, Alone
- Target Variable: Survived

### Data Exploration

- Scatter matrix for numeric features (Age, Fare, Pclass)
- Boxplots for numeric feature distributions
- Count plots for categorical variables (Sex, Embarked)
- Histograms to identify patterns, outliers, and anomalies
- Missing values imputed:
  - Age - median
  - Embarked - mode
- Categorical variables encoded numerically

### Feature Engineering

- FamilySize = SibSp + Parch + 1
- Alone = 1 if FamilySize = 1, else 0

### Models

1. Decision Tree
2. Random Forest

### Train/Test Split

- Test Size: 20%
- Train_Test_Split used to split the data into a training set and a test set

### Evaluation

Metrics on test set: accuracy, precision, recall, F1-score

| Model Type      | Features Used                   | Accuracy | Precision | Recall | F1-Score | Notes                               |
|-----------------|---------------------------------|----------|-----------|--------|-----------|------------------------------------|
| Decision Tree   | Age, Fare, Pclass, Sex, FamilySize, Alone | 57%      | 54%      | 54%   | 54%      | Overfits training set; performs better on non-survivors |
| Random Forest   | Age, Fare, Pclass, Sex, FamilySize, Alone | 60%      | 58%      | 58%   | 58%      | Slight improvement over Decision Tree; still struggles with survivors |

## Reflections

- Decision Tree shows overfitting; Random Forest slightly mitigates this.
- Features Age, Fare, Pclass, Sex, FamilySize, Alone are informative for survival prediction
- Further improvements could include hyperparameter tuning and feature selection.
