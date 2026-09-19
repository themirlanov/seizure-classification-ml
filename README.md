# Seizure Classification Using Machine Learning

## Overview

This project explores how machine learning can be used to identify seizure events from EEG-related data.

The main goal was to compare several classification approaches and evaluate how much performance could be improved by combining different machine learning techniques. I started with logistic regression as a baseline and then experimented with K-Means clustering, Random Forest, and K-Nearest Neighbors (KNN).

The results showed that Random Forest and KNN performed substantially better than the initial logistic regression model on this dataset.

## Objectives

- Can machine learning accurately distinguish seizure events from non-seizure observations?
- How well does a simple logistic regression model perform as a baseline?
- Can K-Means clustering provide useful additional information for classification?
- Which model performs best on the test data?
- Which predictor variables appear to be most important for the final model?

## Dataset

The dataset contains EEG-related measurements represented by variables `X1` through `X16`, along with seizure labels.

For the binary classification task, the data was divided into:

- 5,600 training observations
- 2,400 test observations

The analysis also included a second classification task involving four seizure-related categories.

The original dataset is not included in this repository because it was provided through course materials and is not being redistributed here.

## Approach

I compared several models throughout the analysis.

### 1. Logistic Regression

I first built a logistic regression model as a baseline.

The model achieved:

- **Accuracy:** 81.0%
- **Balanced Accuracy:** 61.7%

This provided a useful baseline for comparing the more advanced approaches.

### 2. K-Means Clustering

Next, I used K-Means clustering to identify two groups within the observations.

The clustering approach achieved approximately:

- **Accuracy:** 83.88%

I then used the distances to the cluster centers as additional features for logistic regression.

### 3. Logistic Regression + K-Means Features

Adding the K-Means cluster-distance features to logistic regression resulted in:

- **Accuracy:** 97.25%
- **Balanced Accuracy:** 95.86%

This showed that unsupervised learning could provide useful additional information for the supervised classification task.

### 4. Random Forest

I then tuned a Random Forest model using different values of `mtry`.

The Random Forest produced the strongest overall results:

- **Accuracy:** approximately 99.67%
- **Sensitivity:** 99.33%
- **Specificity:** 99.78%
- **Kappa:** 0.9911

I selected Random Forest as the final model for the binary classification task.

### 5. K-Nearest Neighbors

Finally, I tested KNN using different values of `k` with 10-fold cross-validation.

The final model achieved:

- **Accuracy:** 99.54%
- **Balanced Accuracy:** 99.08%
- **Kappa:** 0.9876

KNN also performed extremely well, although Random Forest was selected as the final model because it provided strong performance along with useful feature-importance information.

## Model Comparison

| Model | Accuracy |
|---|---:|
| Logistic Regression | 81.00% |
| K-Means | 83.88% |
| Logistic Regression + K-Means | 97.25% |
| Random Forest | ~99.67% |
| KNN | 99.54% |

The biggest improvement came from moving beyond the basic logistic regression model. Both Random Forest and KNN achieved accuracy above 99% on the test data.

## Feature Importance

The Random Forest model also provided information about which predictor variables contributed most to the classification.

The five most important variables were:

1. `X16`
2. `X6`
3. `X10`
4. `X2`
5. `X15`

This provided additional insight into the model beyond prediction accuracy alone.

## Seizure Type Classification

In addition to the binary seizure classification problem, I also experimented with classifying four different categories:

- Focal
- Generalized
- Healthy subject
- Seizure event

The final Random Forest model achieved:

- **Accuracy:** 96.88%
- **Kappa:** 0.9583

KNN was also tested and achieved **94.62% accuracy**.

## Key Takeaways

A few things stood out from this project:

- A simple baseline model can provide a useful reference point, even when its performance is limited.
- Unsupervised learning can sometimes create useful features for supervised models.
- Random Forest performed extremely well on this dataset.
- KNN also produced very strong results after tuning.
- Model comparison is important because accuracy alone does not tell the whole story.
- Feature importance can provide additional insight into model predictions.

## Tools & Technologies

- R
- R Markdown
- tidyverse
- caret
- randomForest
- ggplot2
- Logistic Regression
- K-Means Clustering
- Random Forest
- K-Nearest Neighbors
- 10-fold Cross-Validation

## Project Structure

```text
seizure-classification-ml/
│
├── .gitignore
├── README.md
├── seizure_analysis.Rmd
├── seizure_analysis.html
└── data/
    └── README.md
