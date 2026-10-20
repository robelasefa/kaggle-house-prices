# Kaggle House Prices: Random Forest Baseline

My first end-to-end machine learning project: predicting house sale prices for the [Housing Prices Competition for Kaggle Learn Users](https://www.kaggle.com/c/home-data-for-ml-course) (Iowa housing data).

Built as the final exercise of Kaggle Learn's [Intro to Machine Learning](https://www.kaggle.com/learn/intro-to-machine-learning) course.

## What I did

1. Loaded the training data with pandas and picked 7 numeric features.
2. Split the data into training and validation sets (`train_test_split`, `random_state=1`).
3. Trained a `RandomForestRegressor` and measured it on the held-out validation set.
4. Retrained the model on all of the training data.
5. Predicted prices for the test set and generated `submission.csv` for the competition.

## Results

| Item | Value |
|---|---|
| Model | `RandomForestRegressor(random_state=1)` |
| Validation MAE | **21,857** |
| Kaggle leaderboard score | _add your score here_ |

MAE is the mean absolute error, so on average the model's predictions on unseen validation houses are about $21.9k away from the real sale price.

## Features used

`LotArea`, `YearBuilt`, `1stFlrSF`, `2ndFlrSF`, `FullBath`, `BedroomAbvGr`, `TotRmsAbvGrd`

## What I learned

- Why a model must be evaluated on data it was not trained on (validation set), and how a random forest compares to a single decision tree.
- How to go from a trained model to a real competition submission file.

## Running it

- The notebook is made to run on Kaggle, where the data is already available. Open it there, or download the data from the [competition page](https://www.kaggle.com/c/home-data-for-ml-course/data) and update the file paths.
- The competition data is not included in this repo, since Kaggle's rules don't allow re-sharing it.
- The first cell imports `learntools`, which only exists on Kaggle. It is only for the course's answer checking and can be removed to run the notebook elsewhere.

## Next steps

- [ ] Add more features and see how the validation MAE changes
- [ ] Handle missing values and categorical columns (Intermediate Machine Learning course)
- [ ] Try cross-validation and gradient boosting (XGBoost)

## Tools

Python, pandas, scikit-learn, Jupyter