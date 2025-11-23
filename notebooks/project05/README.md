# Project 5: Ensemble Machine Learning - Wine Quality Prediction

## Overview
This project implements and compares ensemble machine learning models to predict wine quality categories using the UCI Wine Quality Dataset.

## Dataset
- **Source**: [UCI Machine Learning Repository - Wine Quality Dataset](https://archive.ics.uci.edu/ml/datasets/Wine+Quality)
- **Size**: 1,599 red wine samples
- **Features**: 11 physicochemical properties (acidity, sugar, pH, alcohol, etc.)
- **Target**: Quality categories (low: 3-4, medium: 5-6, high: 7-8)

## Models Evaluated
- **Random Forest (100 trees)**: Bagging approach with parallel tree training
- **Gradient Boosting (100 trees)**: Sequential boosting with error correction

## Key Results
| Model | Test Accuracy | Test F1 Score | Accuracy Gap |
|-------|---------------|---------------|--------------|
| Random Forest | 88.75% | 0.8661 | 0.1125 |
| Gradient Boosting | 85.62% | 0.8411 | 0.1039 |

## Files
- `ml05_webb.ipynb`: Main Jupyter notebook with analysis
- `winequality-red.csv`: Wine quality dataset
- `README.md`: This file

## Technologies Used
- Python 3.x
- pandas, numpy, matplotlib
- scikit-learn (ensemble methods, metrics)

## Author
Adrianna Webb - November 23, 2025