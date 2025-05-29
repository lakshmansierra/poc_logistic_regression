# Resignation Predictor
- Uses Binary Classification Algorithm

# Feature Selection
## resources_workday
| Feature                                 | Use in Model?                | Reason                                       |
| --------------------------------------- | ---------------------------- | -------------------------------------------- |
| `Employee_ID`                           | ❌ No                         | Just an ID                                   |
| `Employee Annual Salary$`               | ✅ Yes                        | Pay level affects attrition                  |
| `TAXES$`                                | ❌ No                         | Derived from salary                          |
| `Monthly Medical/Dental/Vision contrib` | ✅ Maybe                      | Indicates benefits and deductions            |
| `Bonus $`                               | ✅ Yes                        | May influence satisfaction                   |
| `OVERHEAD (Laptop; Desk...)`            | ❌ No                         | Fixed overhead unlikely to vary per employee |
| `Years_Of_Service`                      | ✅ Yes                        | Strong indicator of retention                |
| `Last_Promoted`                         | ✅ Yes (calculate time since) | Lack of promotion = turnover risk            |
| `Department`                            | ✅ Yes                        | Some departments have higher attrition       |
| `Location`                              | ✅ Yes                        | Geography again matters                      |
| `Manager`                               | ❌ No                         | Too specific — high cardinality              |
| `Gender`                                | ✅ Yes                        | Sometimes correlated, handle carefully       |
| `Employee HR rate`                      | ✅ Yes                        | Shows skill level / performance measure      |
| `# of Hours per week`                   | ✅ Yes                        | Workload affects burnout                     |
| `Calculated Column - Fully Loaded Cost` | ❌ No                         | Likely redundant with salary/bonus/etc       |


## resources_s4
| Feature           | Use in Model?                             | Reason                                     |
| ----------------- | ----------------------------------------- | ------------------------------------------ |
| `SAP Personnel #` | ❌ No                                      | Just an ID                                 |
| `Company Code`    | ✅ Yes                                     | Might indicate location/policy differences |
| `Hire_Date`       | ❌ No (Years_Of_Service available)         | Used to calculate experience               |
| `Current_Role`    | ✅ Yes                                     | Job role might impact retention            |
| `Cost Center`     | ❌ No                                      | Too granular or redundant with department  |
| `City` / `State`  | ✅ Yes                                     | Geography may affect turnover              |
| `Birthdate`       | ✅ Yes (convert to age)                    | Age may correlate with turnover            |

# Accuracy
```bash
Positive = 1 = left 
Negative = 0 = stay 
```

```bash
TN = 17   (actually stay & Predicted stay)
FP = 0    (actually stay & Predicted left)
FN = 1    (actually left & Predicted stay)
TP = 2    (actually left & Predicted left)
```

```bash
[[TN FP]
 [FN TP]]
```

```bash
Accuracy = (TP + TN) / (TP + TN + FP + FN)
= (2 + 17) / 20 = 19 / 20 = 0.95 → 95%

Precision = TP / (TP + FP)
= 2 / (2 + 0) = 1.0

Recall = TP / (TP + FN)
= 2 / (2 + 1) = 0.6667 → 66.67%

F1 Score = 2 * (Precision * Recall) / (Precision + Recall)
= 2 * (1 * 0.6667) / (1 + 0.6667)
= 1.3334 / 1.6667 ≈ 0.8 → 80%
```
