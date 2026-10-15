# Data Science Case Study 2026

## 1. Project Overview

The goal of this project was to predict kit completion dates for sales orders using historical order data. More accurate predictions could help improve production scheduling and planning.

## 2. Data Preparation

I used Python and pandas to load and explore the training and inference datasets. I calculated kit duration by subtracting `kit_start` from `kit_end`.

I identified 734 records with negative kit durations and excluded them from the initial modeling process. I also created date-based features and converted categorical variables into numerical columns for modeling.

## 3. Modeling Approach

I trained a Random Forest Regressor to predict kit duration in days. I evaluated the model using both a random 80/20 train/test split and a time-based split to assess performance on later orders.

I compared the model against a simple baseline that predicted the average kit duration from the training data.

## 4. Results

### Random Train/Test Split

- Random Forest MAE: approximately 0.522 days.
- Baseline MAE: approximately 0.913 days.

The Random Forest performed better than the baseline on the random test split.

### Time-Based Split

- Random Forest MAE: approximately 1.540 days.
- Baseline MAE: approximately 1.003 days.

The Random Forest performed worse than the baseline on the time-based test set. This suggests that random-split results may overstate the model's ability to predict future orders.

### Inference Predictions

The project generated 12,069 predicted kit completion dates, matching the number of inference records.

The submitted `predictions.npy` currently uses a simple baseline that predicts completion one day after each order's kit start date.

## 5. Limitations

- Negative kit durations require further investigation.
- Time-based evaluation showed that the Random Forest did not outperform the baseline.
- The supplementary capacity and expected-minutes datasets were not fully explored.
- The current inference predictions use a simple one-day rule and have not been established as the optimal approach.

## 6. Recommendations

1. Investigate records with negative kit durations to understand their cause.
2. Use time-based validation to evaluate performance on future orders.
3. Explore additional features from the capacity and expected-minutes datasets.
4. Compare prediction errors across sites and order types where meaningful.
5. Improve and validate the prediction approach before using it for production planning.

## 7. Conclusion

The Random Forest performed better than the baseline on the random test split but worse on the time-based test split. The project generated completion-date predictions for all 12,069 inference records. Further feature exploration, data-quality investigation, and time-based validation are recommended before relying on the predictions for operational planning.

## 8. AI Assistance

OpenAI ChatGPT was used as an AI-assisted tool to support code explanations, debugging, interpretation of model evaluation results, and README drafting. The analysis and reported results were based on the project's code and outputs. All AI assistance should be reviewed and verified before submission.