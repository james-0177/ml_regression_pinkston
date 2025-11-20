
# Binary Classification Guide

> This page provides a general guide for identifying and designing a binary classification project.

You have a binary classification problem when:

- You are predicting a **single target variable**.
- The target has **exactly two possible values**.
- Those two values represent **distinct outcomes**, such as:
  - yes vs no
  - fraud vs not fraud
  - churn vs stay
  - pass vs fail
- There are no additional categories like "unknown", "pending", or "n/a" that would require separate handling.

If all the above are true, you are working on a binary classification task.

The following lists key tasks for binary classification projects.

---

## 1. Identify the Target Variable

- What is the exact name of the target variable:
- What are the two allowable class values:
- Confirm the values mutually exclusive and collectively exhaustive:
- Confirm no unexpected values such as blanks or missing that cannot be classified:

## 2. Define the Positive Class

- Which class should be treated as the "positive" class (label = 1):
- Why is that the correct choice for this domain:
- How will choosing this class affect how precision, recall, or other metrics should be interpreted:


## 3. Check Class Distribution

- What percentage of the dataset belongs to each class:
- Is the dataset imbalanced:
- If so, does the imbalance affect your choice of metrics or modeling approach:


## 4. Understand the Costs of Errors

Binary classification always produces four outcomes:

- True Positive
- True Negative
- False Positive
- False Negative

Key questions:

- Describe a true positive:
- In this application, is it worse to produce a false positive (e.g. wrongly denying a loan) or a false negative (e.g. missed fraud):
- Why:
- In this application, should the project prioritize sensitivity, specificity, or a balanced tradeoff:
- Why:


## 5. Select an Appropriate Decision Threshold

- Is the default threshold of 0.5 appropriate:
- Why or why not:
- What threshold makes sense in this application:
- Why:
- Should the threshold be tuned for precision, recall, or cost sensitivity:
- Why:
- Who determines the acceptable tradeoff (stakeholders, domain experts, regulations):
- Why:

### Default Threshold Behavior (Important)

Most binary classification models in scikit-learn follow the same pattern:

- The model produces a score or probability for the positive class.
- The `.predict_proba(X)` method returns two columns:
  - column 0: P(class 0 | X)
  - column 1: P(class 1 | X)
- The `.predict(X)` method applies an **implicit threshold of 0.5**, meaning:
  - if P(class 1 | X) >= 0.5 then: predict class 1
  - else:  predict class 0

This threshold of 0.5 is only a **default**. You can replace it by:
- creating a threshold variable, e.g. `threshold = 0.5`
- getting probabilities with `.predict_proba(X)`, e.g. `proba = nn_model3.predict_proba(np.c_[xx.ravel(), yy.ravel()])[:, 1]`
- applying your own threshold: `Z = (proba >= threshold).astype(int)`.
- continuing with this Z (for example, `plt.contourf(xx, yy, Z, cmap=cmap_background, alpha=0.7)`)
- where Z is the prediction grid: a 2-D array of class labels (0 or 1) computed for every point in the meshgrid so the decision surface can be plotted.

Discuss your choice of threshold in your project summary.

## 6. Review the Features

- What features are available:
- Which features are allowed (given ethical, legal, policy constraints):
- Are there any variables that could introduce target leakage:
- Provide an example of possible target leakage in this application:
- Are time-dependent features handled correctly:
- Why or why not:
- Do any features come from a time after the outcome occurs:
- How are these handled:


## 7. Choose Evaluation Metrics

- What primary metric will define project success (the classifier works as intended):
- Why is this metric appropriate:
- What secondary metrics should also be reported:
- Discuss:
- Do you need ROC-AUC, PR-AUC, F1, or domain-specific metrics:
- Discuss:


## 8. Establish Baseline Performance

- What accuracy is achieved by always predicting the majority class:
- How did you determine this:
- What accuracy is achieved with random guessing:
- How did you determine this:
- What is the minimum threshold your model must beat to be considered useful:
- How did you determine this:


## 9. Define Data Splitting and Validation

- Will you use a train/test split or cross-validation:
- Why:
- Is time order relevant (time-based split vs random split):
- Discuss:
- Could any leakage occur across splits (duplicates, shared identifiers, events out of order):
- Discuss:


## 10. Clarify Real-World Use

- Who might use this binary classifier model:
- What decision or action would a "positive" prediction trigger:
- What are the consequences of false positives incorrect predictions:
- What are the consequences of true negative incorrect predictions:
- How might this binary classifier impact real people or systems:
