# Experiment 3: Regression Techniques in Business Data(Simple Linear Regression)

##  Aim
To implement Simple Linear Regression in Python to study and predict the relationship between two business-related variables.

## Dataset
A sample business dataset representing the relationship between **Advertising Expenditure** (in Lakhs) and **Sales Revenue** (in Crores). The goal is to analyze how changes in advertising investment affect sales performance.

| Index | Advertising (Lakhs) | Sales (Crores) |
| :---: | :---: | :---: |
| 0 | 18 | 12 |
| 1 | 22 | 18 |
| 2 | 25 | 20 |
| 3 | 30 | 24 |
| 4 | 35 | 28 |
| 5 | 40 | 35 |
| 6 | 45 | 38 |
| 7 | 50 | 40 |
| 8 | 55 | 42 |
| 9 | 60 | 45 |

## Algorithm / Steps Followed
1. Import required Python libraries (`numpy`, `pandas`, `matplotlib`, `scikit-learn`).
2. Create and load the dataset into a Pandas DataFrame.
3. Display the dataset.
4. Select independent ($X$) and dependent ($Y$) variables and reshape $X$ into a 2D array.
5. Build a `LinearRegression` model using `sklearn.linear_model`.
6. Fit the model and calculate the intercept ($a$) and slope ($b$).
7. Predict $Y$ values for given $X$ values and evaluate performance using the $R^2$ score.
8. Plot the actual data points alongside the fitted regression line and predict sales for a new advertising budget.

##  Functions and Methods Used

| Category | Function / Method | Purpose / Description |
| :--- | :--- | :--- |
| **Data Creation / Handling** | `np.array()` | Create numerical arrays for regression input data |
| | `pd.DataFrame()` | Create or manage tabular data for regression |
| **Model Building (Scikit-learn)** | `LinearRegression()` | Initialize the Simple Linear Regression model |
| | `model.fit()` | Train the linear regression model using $X$ and $Y$ values |
| | `model.predict()` | Predict $Y$ values for given $X$ inputs using the fitted model |
| | `model.score()` | Calculate model performance ($R^2$ score) |
| **Visualization (Matplotlib)** | `plt.scatter()` | Plot scatter points (actual data points) |
| | `plt.plot()` | Plot regression line (predicted relationship) |
| | `plt.title()`, `plt.xlabel()`, `plt.ylabel()`, `plt.show()` | Configure and display the regression plot |

##  Program & Output
# Experiment 3: Regression Techniques in Business Data (Simple Linear Regression)

## Code

```python
# Simple Linear Regression: Advertising Expenditure vs Sales Revenue

# Step 1: Import required libraries
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.linear_model import LinearRegression

# Step 2: Create the dataset
data = {
    "Advertising": [18, 22, 25, 30, 35, 40, 45, 50, 55, 60],
    "Sales":       [12, 18, 20, 24, 28, 35, 38, 40, 42, 45]
}
df = pd.DataFrame(data)

# Step 3: Display the dataset
print("Dataset:")
print(df)

# Step 4: Select independent (X) and dependent (Y) variables
X = df[["Advertising"]].values      # 2D array (independent variable)
Y = df["Sales"].values              # 1D array (dependent variable)

# Step 5: Build the Linear Regression model
model = LinearRegression()

# Step 6: Fit the model and get intercept (a) and slope (b)
model.fit(X, Y)
a = model.intercept_
b = model.coef_[0]
print(f"\nIntercept (a): {a:.4f}")
print(f"Slope (b)    : {b:.4f}")
print(f"Regression Equation: Sales = {a:.4f} + {b:.4f} x Advertising")

# Step 7: Predict and evaluate using R-squared
Y_pred = model.predict(X)
r2 = model.score(X, Y)
print("\nActual vs Predicted Sales:")
print(pd.DataFrame({"Advertising": df["Advertising"], "Actual": Y,
                    "Predicted": Y_pred.round(2)}))
print(f"\nR-squared (R2) Score: {r2:.4f}")

# Step 8: Plot actual data and regression line
plt.figure(figsize=(8, 5))
plt.scatter(X, Y, color="blue", label="Actual Data")
plt.plot(X, Y_pred, color="red", linewidth=2, label="Regression Line")
plt.title("Advertising Expenditure vs Sales Revenue", fontsize=14, fontweight="bold")
plt.xlabel("Advertising (Lakhs)")
plt.ylabel("Sales (Crores)")
plt.grid(True, linestyle="--", alpha=0.5)
plt.legend()
plt.tight_layout()
plt.savefig("images/regression_plot.png", dpi=150)
plt.show()

# Predict sales for a new advertising budget
new_

Dataset:
   Advertising  Sales
0           18     12
1           22     18
2           25     20
3           30     24
4           35     28
5           40     35
6           45     38
7           50     40
8           55     42
9           60     45

Intercept (a): 0.5812
Slope (b)    : 0.7794
Regression Equation: Sales = 0.5812 + 0.7794 x Advertising

Actual vs Predicted Sales:
   Advertising  Actual  Predicted
0           18      12      14.61
1           22      18      17.73
2           25      20      20.07
3           30      24      23.96
4           35      28      27.86
5           40      35      31.76
6           45      38      35.66
7           50      40      39.55
8           55      42      43.45
9           60      45      47.35

R-squared (R2) Score: 0.9736

Predicted Sales for Advertising = 70 Lakhs: 55.14 Crores
```
<img width="1024" height="765" alt="image" src="https://github.com/user-attachments/assets/1a71d8f4-f7eb-4766-8d29-4914b685b730" />

##  Result
Thus, Simple Linear Regression on the advertising and sales dataset was executed successfully.
