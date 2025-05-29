# Logistic Regression
Logistic regression is a **Classification algorithm** that `models the probability of a data point belonging to a particular class` using the **Sigmoid function**.

```bash
Supervised Learning -> Classification Algorithm -> Binary Classification | Multi Classification
```

## Logistic Regression Equation

$$
z = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + \cdots + \beta_n x_n
$$

- z => Dependent Variable
- β₀ => intercept
- β₁, β₂ ... => Weights of each feature
- x₁, x₂ ... => Independent Variables

## Sigmoid Function

$$
y = \sigma(z) \in (0, 1) = \frac{1}{1 + e^{-z}}
$$

- 𝜎 => sigmoid function to predict the probability of an observation being in the class
