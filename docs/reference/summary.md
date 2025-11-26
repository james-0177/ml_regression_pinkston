
| Model Type                 | Features Used    | Train R^2 | Test R^2 | Test RMSE | Test MAE |
| -------------------------- | ---------------- | -------- | ------- | --------- | -------- |
| Linear Regression          | age, bmi, smoker | 0.739    | 0.778   | 5874.76   | 4260.56  |
| Pipeline 1 (StandardScaler)     | age, bmi, smoker | 0.739    | 0.778   | 5874.76   | 4260.56  |
| Pipeline 2 (Polynomial Features, degree=3) | age, bmi, smoker | 0.836    | 0.861   | 4637.02   | 2838.44  |
