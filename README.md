# Kaggle House Prices: improving my first model

This is my project for the [Housing Prices Competition for Kaggle Learn Users](https://www.kaggle.com/c/home-data-for-ml-course). It uses the Iowa house prices data.

I made my first version after the Intro to ML course. It was a Random Forest with 7 columns and a validation MAE of 21,857. Then I finished the Intermediate Machine Learning course and came back to make it better.

## What I did

1. Used all the columns instead of only 7.
2. Filled in the missing values. For number columns I used the median. For text columns I used the word "None", because a missing value usually means the house doesn't have that thing (like no pool or no alley).
3. Turned the text columns into numbers with one-hot encoding.
4. Used pipelines so the validation data never touches the training.
5. Made 4 new columns: total square feet, house age, years since the last remodel, and total bathrooms.
6. Trained XGBoost on the log of the price, and used early stopping to pick the number of trees.
7. Compared all the models with a validation split and with 5-fold cross-validation.
8. Trained the best model on all the training data and made `submission.csv`.

## Results

MAE is the average difference between my predicted price and the real price, in dollars. Lower is better.

| Model | Validation MAE | 5-fold CV MAE |
|---|---|---|
| Old model (Random Forest, 7 columns) | 21,857 | 22,918 |
| Random Forest, all number columns | 16,712 | 18,039 |
| + text columns | 16,468 | 17,740 |
| + new columns | 16,334 | 17,231 |
| XGBoost on log price (max_depth 3, 558 trees) | 13,691 | 14,548 |

The error went down by about 37%. The cross-validation number is the more reliable one. The validation number for XGBoost is a little too good, because early stopping used the same validation data to pick the number of trees.

**Kaggle score:** 14,281.63 (this is the MAE on the competition's test data). I was in 313th place when I submitted.

## What I learned

- How to handle missing values and text columns instead of ignoring them.
- Why pipelines are useful.
- Why cross-validation is better than one validation split.
- How XGBoost works and how early stopping picks the number of trees.
- Small things can help a lot, like filling missing text with "None" and predicting the log of the price.

## How to run it

1. Download `train.csv` and `test.csv` from the [competition page](https://www.kaggle.com/c/home-data-for-ml-course/data) and put them in the same folder as the notebook. I didn't add them here because Kaggle doesn't allow sharing the data.
2. Install the libraries: `pip install -r requirements.txt`
3. Open `house-prices.ipynb` and run all the cells.

If you run it on Kaggle, change the file paths in the first code cell to `../input/home-data-for-ml-course/train.csv` and `test.csv`.

## What I want to try next

- Put the quality columns (like `ExterQual` and `KitchenQual`) in order, from poor to excellent.
- Try more XGBoost hyperparams.
- Combine XGBoost with another model.

## Tools

Python, pandas, scikit-learn, XGBoost, Jupyter