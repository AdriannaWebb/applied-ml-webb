# Project 3: Building a Classifier (Titanic Dataset)

**Author:** Adrianna Webb
**Date:** November 2025
**Course:** Applied Machine Learning

## Project Overview

This project builds and evaluates three classification models (Decision Tree, Support Vector Machine, and Neural Network) to predict passenger survival on the Titanic. The analysis compares model performance across three different feature sets to identify which features and algorithms are most effective for binary classification.

## Dataset

- **Source:** Seaborn library (`sns.load_dataset('titanic')`)
- **Target Variable:** `survived` (0 = died, 1 = survived)
- **Features Used:**
  - `alone`: Binary indicator of whether passenger traveled alone
  - `age`: Passenger age (continuous)
  - `family_size`: Total family members aboard (calculated: sibsp + parch + 1)

## Three Feature Cases

1. **Case 1:** `alone` only (binary feature)
2. **Case 2:** `age` only (continuous feature)
3. **Case 3:** `age + family_size` (two continuous features)

## Models Evaluated

### Decision Tree Classifier
- Tested on all three cases
- Best performance: Case 1 (63% accuracy, balanced)
- Case 3 showed overfitting (77% train → 59% test)

### Support Vector Machine (SVC)
- Tested multiple kernels: RBF, Linear, Polynomial, Sigmoid
- Default RBF kernel struggled with Cases 2 & 3 (only 7% survivor recall)
- **Sigmoid kernel performed best** (55% accuracy, 45% survivor recall)

### Neural Network (MLP)
- Architecture: 3 hidden layers (50, 25, 10 neurons)
- **Best overall model:** 66% accuracy with balanced performance
- Achieved 41% survivor recall vs SVC's 7%

## Key Results Summary

| Model Type | Case | Features Used | Accuracy | Notes |
|------------|------|---------------|----------|-------|
| Decision Tree | 1 | alone | 63% | Balanced, no overfitting |
| Decision Tree | 2 | age | 61% | Poor survivor detection (17% recall) |
| Decision Tree | 3 | age + family_size | 59% | Overfit to training data |
| SVM (RBF) | 3 | age + family_size | 63% | Only 7% survivor recall |
| SVM (Sigmoid) | 3 | age + family_size | 55% | Best SVM - 45% survivor recall |
| Neural Network | 3 | age + family_size | **66%** | **Best overall - 41% survivor recall** |

## Key Findings

1. **Neural Networks outperformed SVMs** due to ability to learn non-linear decision boundaries
2. **Sigmoid kernel was crucial** for SVM to identify survivors effectively
3. **Class imbalance** caused most models to favor predicting deaths over survivors
4. **Simple features can be effective**: The binary "alone" feature performed surprisingly well
5. **Age + family_size** provided the most predictive power when properly modeled

## Visualizations

- Decision tree structures showing split decisions
- Confusion matrices for all models
- Support vector visualizations (1D and 2D scatter plots)
- Neural network decision surface showing survival zones

## Technologies Used

- Python 3.x
- pandas, numpy
- scikit-learn (DecisionTreeClassifier, SVC, MLPClassifier)
- seaborn, matplotlib
- Jupyter Notebook

## Project Structure
```
project03/
├── README.md
└── ml03_webb.ipynb
```

## How to Run

1. Clone the repository
2. Install required packages: `pip install pandas numpy scikit-learn seaborn matplotlib`
3. Open `ml03_webb.ipynb` in Jupyter Notebook
4. Run all cells sequentially

## Challenges & Lessons Learned

- **Class imbalance** can make accuracy misleading; always check precision, recall, and F1-scores per class
- **Default hyperparameters** don't always work; experimentation is essential
- **Overfitting** detection requires comparing training vs test performance
- **Kernel selection** dramatically impacts SVM performance

## Future Improvements

- Add `sex` and `pclass` features (historically strong predictors)
- Implement cross-validation for more robust evaluation
- Use grid search for systematic hyperparameter tuning
- Try ensemble methods (Random Forest, Gradient Boosting)
- Address class imbalance with SMOTE or class weights

## References

- [Titanic Dataset Documentation](https://www.kaggle.com/c/titanic)
- [scikit-learn Documentation](https://scikit-learn.org/)
- Course materials and examples