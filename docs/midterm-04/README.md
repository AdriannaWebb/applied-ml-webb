# Project 4: Mushroom Classification

## Overview

This project performs exploratory data analysis and classification modeling on the UCI Mushroom Dataset. The goal is to predict whether a mushroom is edible or poisonous based on its physical characteristics using a Decision Tree Classifier.

## Dataset

The Mushroom dataset was loaded directly from the UCI Machine Learning Repository and contains 8,124 observations with categorical features describing attributes such as cap shape, odor, gill color, habitat, and more. The target variable is poisonous, indicating whether a mushroom is safe to eat or not.

## Project Structure

ml04_webb_midterm.ipynb: Main Jupyter notebook containing the full analysis

README.md: Project documentation

## Key Steps
1. Data Import and Inspection
   1. Load the mushroom dataset from the UCI repository
   2. Inspect structure, feature names, and data types
   3. Check for missing values and describe overall dataset composition

2. Data Exploration and Preparation
   1. Visualize feature distributions using count plots
   2. Identify outliers and patterns in categorical variables
   3. Handle missing values (imputed stalk-root using mode)
   4. Drop uninformative column (veil-type)
   5. Encode categorical features using label encoding

3. Feature Selection
   1. Selected five key predictors: odor, spore-print-color, gill-color, population, and habitat
   2. Defined target variable: poisonous
   3. Justified feature choice based on interpretability and biological relevance

4. Model Training and Evaluation
   1. Trained a Decision Tree Classifier using stratified train/test split
   2. Evaluated model performance with accuracy, precision, recall, F1-score, and confusion matrix
   3. Initial model achieved 100% accuracy, revealing potential feature leakage

5. Model Tuning and Interpretation
   1. Removed suspected leakage features (odor and spore-print-color)
   2. Re-trained Decision Tree achieving 94% accuracy with balanced precision and recall
   3. Visualized tuned tree and interpreted top decision nodes (gill-color, stalk-shape, habitat)

6. Summary and Insights
   1. Discussed the impact of feature leakage on model performance
   2. Compared original and tuned model accuracy and generalization
   3. Reflected on lessons learned about data preprocessing, model interpretability, and evaluation

## Technologies Used

Python 3.x

pandas

numpy

matplotlib

seaborn

scikit-learn

## Requirements

All libraries used are included in standard data science environments (e.g., Anaconda or Jupyter). No additional installations are required beyond scikit-learn, matplotlib, and seaborn.