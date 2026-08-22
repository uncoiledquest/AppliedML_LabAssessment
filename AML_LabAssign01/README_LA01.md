# Applied Machine Learning --- Lab Assignment 1

**Course:** CSAI2017P --- Applied Machine Learning (Lab)\
**Name:** Abhishek Bhatt\
**SAP ID:** 590028847\
**Batch:** B-05

## Objective

To set up a reproducible Python environment, inspect the California
Housing dataset, and examine the effect of feature scaling on KNN
regression performance.

## A1 --- Environment Proof

  Software       Version
  -------------- ---------
  Python         3.14.2
  NumPy          2.5.2
  Pandas         3.0.5
  Scikit-learn   1.9.0
  Matplotlib     3.11.1
  Seaborn        0.13.2

**Observation:**\
All required libraries were installed and imported successfully. Version
pinning helps ensure that the same code behaves consistently when the
work is run on another system.

## A2 --- First Look at the Data

  Property         Result
  ---------------- ---------------
  Rows             20,640
  Features         8
  Target           `MedHouseVal`
  Target units     \$100,000
  Missing values   None

**Observation:**\
The dataset contains 20,640 rows and 8 features. The target is
`MedHouseVal`, measured in \$100,000 units. `Population` is on a much
larger scale, with a mean of 1425.48 compared with 28.64 for `HouseAge`
and 5.43 for `AveRooms`. No missing values were found.

## B1 --- Scaling Changes the Answer

The California Housing data was split into 80% training and 20% testing
data using `random_state=0`. A 5-nearest-neighbors regressor was
evaluated before and after feature scaling with `StandardScaler` inside
a `Pipeline`.

  Model                       Test MAE   Approx. error
  ------------------------- ---------- ---------------
  KNN without scaling           0.8142        \$81,416
  KNN with StandardScaler       0.4308        \$43,076

**Observation:**\
The MAE decreased from 0.8142 to 0.4308 after scaling. KNN uses
distances, so features with larger numerical scales can have greater
influence on the distance calculation. StandardScaler puts the features
on a comparable scale, which changes the nearest neighbours and improves
the predictions.

## C1 --- Reproducibility Check

**Observation:**\
After restarting the kernel and running the notebook from top to bottom,
the reported values were reproduced exactly. The fixed `random_state=0`
ensures that the same train/test split is used each time.

## Conclusion

The experiment demonstrated that feature scaling can significantly
affect KNN regression because KNN relies on distance calculations.
StandardScaler reduced the test MAE from 0.8142 to 0.4308.
