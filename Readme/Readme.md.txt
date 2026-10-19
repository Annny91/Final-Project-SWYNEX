# SWYNEX — Hotel Booking Cancellation Prediction

## Project Overview

This project was completed as part of my Data Analysis / Data Engineering Internship at SWYNEX Technologies.

The objective of this project is to build and evaluate a baseline machine learning model to predict whether a hotel booking will be cancelled.

The project uses the prepared Hotel Booking Demand dataset and compares two Logistic Regression models to understand their prediction performance.

## Objectives

- Prepare input features and the prediction target.
- Split the dataset into training and testing sets.
- Build a preprocessing pipeline.
- Train a baseline Logistic Regression model.
- Evaluate model performance using suitable metrics.
- Compare the original and balanced models.
- Visualize model performance.
- Discuss model limitations and possible improvements.

## Business Problem

Hotel booking cancellations can affect room availability, revenue planning, and operational decisions.

The business question for this project is:

**Can we use historical booking information to predict whether a hotel booking will be cancelled?**

A cancellation prediction model could help hotels identify bookings that may require further attention. However, the usefulness of the model depends on its evaluation results and the business cost of incorrect predictions.

## Dataset

The project uses the prepared Hotel Booking Demand dataset from the previous data preparation task.

- Records: 87,396
- Columns: 33
- Target variable: `is_canceled`

Target variable interpretation:

- `0` — Booking was not cancelled.
- `1` — Booking was cancelled.

## Features Used

The model uses four input features:

- `hotel`
- `lead_time`
- `deposit_type`
- `market_segment`

The target variable is `is_canceled`.

These features were selected based on patterns observed during the previous exploratory data analysis task.

## Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- Jupyter Notebook
- Git and GitHub

## Modeling Workflow

1. Load the prepared dataset.
2. Select input features and target variable.
3. Split the data into training and testing sets.
4. Preprocess numerical and categorical features.
5. Train the original Logistic Regression model.
6. Evaluate the original model.
7. Compare its accuracy with a simple baseline.
8. Train a second Logistic Regression model using `class_weight="balanced"`.
9. Evaluate and compare both models.
10. Document findings and limitations.

The dataset was split into 80% training data and 20% testing data. The split used `random_state=42` and stratification on the target variable.

The resulting datasets contained 69,916 training records and 17,480 testing records.

## Model Evaluation

The models were evaluated using accuracy, precision, recall, F1-score, and confusion matrices.

### Original Logistic Regression

| Metric | Result |
|---|---:|
| Accuracy | 73.99% |
| Precision for cancellations | 62.49% |
| Recall for cancellations | 13.49% |
| F1-score for cancellations | 22.18% |

The original model achieved 73.99% accuracy but detected only a small proportion of actual cancellations.

### Balanced Logistic Regression

The second model used `class_weight="balanced"` to give more weight to the cancellation class during training.

| Metric | Result |
|---|---:|
| Accuracy | 60.34% |
| Precision for cancellations | 38.86% |
| Recall for cancellations | 77.17% |
| F1-score for cancellations | 51.69% |

The balanced model detected substantially more actual cancellations but produced more false-positive predictions.

## Simple Baseline Comparison

A simple baseline that predicts every booking as not cancelled achieved 72.51% accuracy.

| Model | Accuracy |
|---|---:|
| Simple baseline | 72.51% |
| Original Logistic Regression | 73.99% |
| Balanced Logistic Regression | 60.34% |

The original model improved accuracy by 1.48 percentage points over the simple baseline.

This comparison demonstrates why accuracy alone is insufficient for evaluating a cancellation prediction model.

## Confusion Matrix — Balanced Model

The balanced model produced the following confusion matrix:

| Actual / Predicted | Not Cancelled | Cancelled |
|---|---:|---:|
| Not Cancelled | 6,840 | 5,835 |
| Cancelled | 1,097 | 3,708 |

The model correctly identified 3,708 cancelled bookings and missed 1,097 actual cancellations. It also incorrectly flagged 5,835 bookings as cancellations.

## Key Findings

1. The original model achieved 73.99% accuracy but only 13.49% recall for cancellations.
2. The balanced model increased cancellation recall to 77.17%.
3. The balanced model's precision decreased to 38.86%, indicating many false-positive predictions.
4. The balanced model achieved a higher cancellation F1-score: 51.69% compared with 22.18%.
5. The original model's accuracy was only 1.48 percentage points higher than the simple baseline.
6. Model selection should consider business requirements and multiple evaluation metrics rather than accuracy alone.

## Visualizations

The notebook includes:

- Confusion matrix heatmap for the balanced Logistic Regression model.
- Model performance comparison chart for accuracy, precision, recall, and F1-score.

These visualizations help communicate prediction errors and the trade-off between detecting cancellations and generating false alarms.

## Model Limitations

- Only four input features were used.
- The balanced model generates many false-positive predictions.
- The original model misses many actual cancellations.
- Historical patterns may not represent future booking behavior.
- Other algorithms, features, and parameter settings have not been comprehensively compared.
- The model has not been validated in a real hotel operation.
- Further validation is required before using predictions for business decisions.

## Conclusion

This project demonstrates a baseline machine learning workflow for hotel booking cancellation prediction.

Two Logistic Regression models were trained and evaluated. The original model achieved higher accuracy, while the balanced model detected a larger proportion of actual cancellations.

The results highlight the trade-off between precision and recall and demonstrate the importance of choosing evaluation metrics based on business needs.

The models are useful as a learning and experimentation baseline but are not yet ready for production use.

## Project Structure

```text
SWYNEX Baseline Model/
├── Data/
│   └── cleaned_data.csv
├── Notebook/
│   └── Baseline_model.ipynb
├── Readme/
│   └── README.md
└── requirements.txt
```

## How to Run

Clone the repository:

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
```

Install the required libraries:

```bash
pip install -r requirements.txt
```

Open the notebook in Jupyter Notebook or Visual Studio Code and run the cells in order.

## Previous Project

This project builds on the previous Hotel Booking Data Preparation and Exploratory Data Analysis tasks.

## Author

**Aniket Sharma**

Aspiring Data Engineer

### Skills Demonstrated

- Python
- Pandas and NumPy
- Data preprocessing
- Machine learning fundamentals
- Logistic Regression
- Model evaluation
- Data visualization
- Git and GitHub
