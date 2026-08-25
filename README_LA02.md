# Applied Machine Learning — Lab Assignment 2

**Course:** CSAI2017P — Applied Machine Learning (Lab)\
**Name:** Abhishek Bhatt\
**SAP ID:** 590028847\
**Batch:** B-05

## Objective

To build and evaluate linear regression models for predicting California housing prices, compare regression models using different evaluation metrics, study the effect of polynomial features, and identify situations where the model performs poorly.

## A1 — Simple Linear Regression

A linear regression model was trained using **Median Income (`MedInc`)** as the only predictor for **Median House Value (`MedHouseVal`)**.

| Parameter | Value |
|-----------|------:|
| Slope | 0.4203 |
| Intercept | 0.4432 |
| Test R² | 0.4466 |

**Observation:**\
The model uses only `MedInc` to predict house prices. The positive slope indicates that house prices generally increase as median income increases. The test R² of approximately **0.45** shows that median income alone explains a moderate amount of the variation in house prices.

---

## A2 — Multiple Linear Regression

A multiple linear regression model was trained using all eight features inside a `Pipeline` with `StandardScaler`.

| Metric | Value |
|--------|------:|
| MAE | 0.5351 |
| RMSE | 0.7273 |
| R² | 0.5943 |

**Observation:**\
Using all eight features improved the prediction accuracy compared to simple linear regression. The predicted values generally follow the actual values, although larger prediction errors are still observed for some districts, particularly those with extreme house prices.

---

## B1 — Polynomial Features and Over-fitting

Polynomial regression models with degree 1, 2 and 3 were trained and evaluated using training and testing RMSE.

| Degree | Train RMSE | Test RMSE |
|--------|-----------:|----------:|
| 1 | 0.7235 | 0.7273 |
| 2 | 0.6478 | 1.6625 |
| 3 | 0.5880 | 596.1594 |

**Observation:**\
Increasing the polynomial degree reduces the training RMSE because the model becomes more flexible and fits the training data more closely. However, the testing RMSE increases dramatically for degrees 2 and 3, indicating severe over-fitting. Degree 1 provides the best balance between training and testing performance for this dataset.

---

## C1 — Where the Model Fails

The 20 test districts with the largest prediction errors were identified using the best-performing regression model.

**Observation:**\
The largest prediction errors mainly occur for districts with very high or very low house values. These locations are likely influenced by factors that are not available in the dataset. Additional information such as neighbourhood quality, crime rate, school ratings, distance to workplaces, and nearby facilities could improve the model's prediction accuracy.

---

## Conclusion

The experiment demonstrated the application of simple and multiple linear regression for housing price prediction. Multiple linear regression achieved better accuracy than simple linear regression by using all available features. Polynomial regression showed that increasing model complexity can lead to severe over-fitting, resulting in poor performance on unseen data. The analysis of prediction errors also highlighted the importance of additional real-world features for improving housing price prediction.