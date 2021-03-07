# Machine-Learning - Exoplanet Exploration

Over a period of nine years in deep space, the NASA Kepler space telescope has been out on a planet-hunting mission to discover hidden planets outside of our solar system.
To help process this data, you will create machine learning models capable of classifying candidate exoplanets from the raw dataset.

## Preprocess the Data

* Preprocess the dataset prior to fitting the model.
* Perform feature selection and remove unnecessary features.
* Use `MinMaxScaler` to scale the numerical data.
* Note: all of the cleaning and separating of the data is done in the ETL.ipynb file. This is so that the steps do not have to be repeated for each model.
* Separate the data into training and testing data. This is done with each model; there does not seem to be a way to do this in a separate file.

## Tune Model Parameters

* Use `GridSearch` to tune model parameters.
* Tune and compare at least two different classifiers.

## Analysis

### Model-1 Logistic Regression

* Using `StandardScaler` resulted in better scores that `MinMaxScaler`.
* For feature selection, all of the supplied features are used. It is noticed that a dramatic drop off in accuracy occurs if any features are left out.
* The results are:
  * Training: 0.548
  * Testing: 0.565
* Using `GridSearch` and attempting to tune `C` and `max_iter` improved the results to 0.658.

### Model-2 Random Forest

* Using `MinMaxScaler` resulted in slightly better results versus the `StandardScaler`.
* For feature selection, all of the supplied features are used. It is noticed that a dramatic drop off in accuracy occurs if any features are left out.
* The results are:
  * Training: 0.489
  * Testing: 0.481
* Using `GridSearch` and attempting to tune `n_estimators`, `max_features`, `max_depth`, `min_samples_split`, `min_samples_leaf`, `bootstrap` improved the results to 0.891.

### Model-3 SVM

* Using `MinMaxScaler` resulted in slightly better results versus the `StandardScaler`.
* For feature selection, all of the supplied features are used. It is noticed that a dramatic drop off in accuracy occurs if any features are left out.
* The results are:
  * Training: 0.495
  * Testing: 0.520
* Using `GridSearch` and attempting to tune `C` and `gamma` improved the results to 0.608.

## Final analysis:

* All of the models, prior to GridSearch, started off at roughly 0.500 which is selecting the correct result half of the time.
* `GridSearch` helped all three models to a greater or lesser degree.
* Random Forest shows the largest benefit from the `GridSearch`, achieving a final score of ~0.900. The score significantly beats out the other two models.
* Random Forest might be a good enough model to predict new exoplanets. A concern is that Random Forests tend to be brittle and may need frequent re-training. Neural Nets should be the next line of analysis, preferably with two or more hidden layers.
