# Hotel Booking Cancellation Prediction — End-to-End Data Science Project

## Project Overview
This project analyzes hotel booking data to understand booking cancellations and build a machine learning model to identify bookings that may be cancelled.

The project covers data preparation, exploratory data analysis (EDA), model training, evaluation, and business insights using Python.

## Business Problem
Hotel booking cancellations can affect room availability, revenue planning, and hotel operations. This project explores cancellation patterns and tests whether historical booking information can help identify cancellation risk.

## Project Objectives
- Clean and prepare hotel booking data.
- Explore cancellation patterns using charts and summary statistics.
- Train a machine learning model to predict booking cancellations.
- Compare model performance using appropriate evaluation metrics.
- Explain findings and model limitations in business terms.

## Dataset
- Dataset: Hotel Booking Demand dataset
- Cleaned records: 87,396
- Columns: 33
- Target column: `is_canceled`
  - `0` = Booking not cancelled
  - `1` = Booking cancelled

## Project Workflow

### 1. Data Preparation
- Checked missing values and duplicate records.
- Handled invalid values, including negative average daily rates (ADR).
- Corrected data types and prepared the cleaned dataset for analysis.

### 2. Exploratory Data Analysis
Key findings:
- Overall cancellation rate: 27.49%.
- City Hotel cancellation rate: 30.04%.
- Resort Hotel cancellation rate: 23.48%.
- Cancellation rate for bookings made 181 or more days in advance: 39.74%.
- Cancellation rate for bookings with a Non Refund deposit type: 94.70%.

These results show patterns in historical bookings. They do not prove that any single factor causes cancellations.

### 3. Machine Learning
Logistic Regression was trained using these features:
- Hotel type
- Lead time
- Deposit type
- Market segment

The data was split into training and testing sets. Categorical features were encoded, and the numeric feature was scaled using a preprocessing pipeline.

Two models were compared:
- Original Logistic Regression
- Logistic Regression with balanced class weights

### 4. Model Evaluation

| Metric | Original Model | Balanced Model |
|---|---:|---:|
| Accuracy | 73.99% | 60.34% |
| Precision | 62.49% | 38.86% |
| Recall | 13.49% | 77.17% |
| F1-score | 22.18% | 51.69% |

The original model has higher accuracy but identifies relatively few cancelled bookings. The balanced model identifies more cancellations, but it also incorrectly flags more bookings as likely to be cancelled.

## Business Insights
- City Hotel bookings had a higher cancellation rate than Resort Hotel bookings in this dataset.
- Bookings made further in advance showed higher cancellation rates.
- Non Refund bookings had a very high historical cancellation rate in this dataset, which should be investigated before making business decisions.
- Hotels should consider the cost of missed cancellations and false alarms when choosing a prediction model.

## Limitations
- The models use only four input features.
- The balanced model produces many false positives.
- The models are preliminary and require further validation.
- Results from historical data may not generalize to every hotel or future booking period.
- These models should not be used for operational decisions without additional testing.

## Conclusion
This project demonstrates an end-to-end data science workflow, from cleaning data and exploring patterns to training and evaluating machine learning models. The balanced Logistic Regression model improves cancellation recall, but further feature engineering, threshold tuning, and validation are needed before practical use.

## Tools and Technologies
- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- Jupyter Notebook
- GitHub

## Author
Aniket Sharma
