| Model Type      | Features Used                   | Accuracy | Precision | Recall | F1-Score | Notes                               |
|-----------------|---------------------------------|----------|-----------|--------|-----------|------------------------------------|
| Decision Tree   | Age, Fare, Pclass, Sex, FamilySize, Alone | 57%      | 54%      | 54%   | 54%      | Overfits training set; performs better on non-survivors |
| Random Forest   | Age, Fare, Pclass, Sex, FamilySize, Alone | 60%      | 58%      | 58%   | 58%      | Slight improvement over Decision Tree; still struggles with survivors |
