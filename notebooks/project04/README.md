# Titanic Fare Prediction: Linear Regression Analysis

## Project Overview
This project explores linear regression techniques to predict Titanic passenger fares using various features from the dataset. The analysis compares multiple regression approaches and feature combinations to identify the most effective predictive model.

## Dataset
- **Source**: Titanic passenger data
- **Target Variable**: Fare (ticket price in dollars)
- **Features Explored**: Age, family size, passenger class, survival status

## Methodology

### Feature Engineering
- Created `pclass_survival` feature combining passenger class and survival status
- Tested four feature combinations:
  - Case 1: Age only
  - Case 2: Family size only
  - Case 3: Age + family size
  - Case 4: Pclass_survival + family size (best performing)

### Models Tested
1. **Linear Regression** (baseline)
2. **Ridge Regression** (L2 regularization)
3. **Elastic Net** (L1 + L2 regularization)
4. **Polynomial Regression** (degree 3 and 7)

## Key Findings

### Model Comparison 
| Model Type | Case | Features Used | R² | RMSE ($) | MAE ($) | Notes |
|------------|------|---------------|-----|----------|---------|-------|
| Linear Regression | Case 4 | pclass_survival + family_size | 0.193 | 34.17 | 22.82 | Baseline model |
| Ridge Regression | Case 4 | pclass_survival + family_size | 0.193 | 34.16 | 22.81 | Minimal regularization benefit |
| Elastic Net | Case 4 | pclass_survival + family_size | 0.217 | 33.66 | 22.12 | Slight improvement over linear |
| Polynomial (degree=3) | Case 4 | pclass_survival + family_size | 0.425 | 28.84 | 15.58 | **Best performing - 2 features** |
| Polynomial (degree=3) | Single Feature | pclass_survival only | 0.240 | 34.30 | 20.98 | Single feature comparison |
| Polynomial (degree=7) | Single Feature | pclass_survival only | 0.240 | 34.30 | 20.98 | No improvement over degree=3 |

### Best Model Performance
- **Polynomial Regression (degree=3)** achieved the best results:
  - R²: 0.425
  - RMSE: $28.84
  - MAE: $15.58

### Feature Importance
- `pclass_survival` was the most predictive feature, capturing the relationship between passenger class, survival rates, and ticket prices
- Adding `family_size` improved model performance
- `Age` alone was a poor predictor (R² = 0.003)

### Model Complexity Insights
- Polynomial features significantly improved predictions by capturing nonlinear relationships
- Regularization (Ridge, Elastic Net) provided minimal benefit, suggesting models weren't overfitting
- Higher-order polynomials (degree=7) showed no improvement over cubic (degree=3)

## Challenges
- Fare prediction remained moderately difficult (best R² = 0.425), with 57.5% of variance unexplained
- High variation in fares within the same passenger class
- Outliers (luxury tickets $150-$260) were consistently underpredicted
- Missing pricing factors: cabin location, embarkation port, purchase timing

## Technologies Used
- Python
- pandas, numpy
- scikit-learn
- matplotlib

## Conclusions
The nonlinear relationship between passenger class, survival, family size, and fare requires polynomial regression for adequate modeling. While the polynomial model performed well, substantial fare variation remains unexplained, suggesting additional features would be needed for more accurate predictions.