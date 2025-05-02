# Red Wine Quality Classification

Do you like wine? Can we guess the score of wine without tasting it? In the competitive wine industry, accurately assessing wine quality is critical for producers, distributors, and retailers to ensure customer satisfaction and optimize market positioning. This project leverages a Random Forest Classifier to predict whether a red wine is "tasty" (high quality) or not based on its physicochemical properties, such as alcohol content, acidity, and sulfur dioxide levels.

## Overview

This project focuses on building a binary classification model to predict red wine quality, specifically whether a wine is "tasty" (quality >/7) or not (quality \< 7), using the `wineQualityReds.csv` dataset from the UCI Machine Learning Repository. 

## Objectives

- **Exploratory Data Analysis (EDA)**: Analyze the distribution and relationships of wine features and the target variable to identify key predictors of wine quality.  
- **Model Development**: Implement and train a Random Forest Classifier to predict whether a wine is tasty or not based on its physicochemical properties.  
- **Evaluation**: Assess model performance using accuracy, confusion matrix, and classification report to evaluate classification effectiveness.  
- **Business Insights**: Provide recommendations for wine production and marketing based on model results and feature importance.

## Dataset

The dataset, `wineQualityReds.csv`, contains 1,599 red wine samples with 13 columns, including 11 physicochemical features, an index column, and the target variable. It is sourced from the UCI Machine Learning Repository ([https://archive.ics.uci.edu/ml/datasets/wine+quality](https://archive.ics.uci.edu/ml/datasets/wine+quality)).   
Key columns include:

- `Unnamed: 0`: Index column (1 to 1,599, likely redundant).  
- `fixed.acidity`: Fixed acidity (g/L, tartaric acid, 4.6 to 15.9).  
- `volatile.acidity`: Volatile acidity (g/L, acetic acid, 0.12 to 1.58).  
- `citric.acid`: Citric acid (g/L, 0.0 to 1.0).  
- `residual.sugar`: Residual sugar (g/L, 0.9 to 15.5).  
- `chlorides`: Chloride content (g/L, sodium chloride, 0.012 to 0.611).  
- `free.sulfur.dioxide`: Free sulfur dioxide (mg/L, 1 to 72).  
- `total.sulfur.dioxide`: Total sulfur dioxide (mg/L, 6 to 289).  
- `density`: Density (g/cm^3, 0.99007 to 1.00369).  
- `pH`: pH level (2.74 to 4.01).  
- `sulphates`: Sulphate content (g/L, potassium sulphate, 0.33 to 2.0).  
- `alcohol`: Alcohol content (% vol, 8.4 to 14.9).  
- `quality`: Original target variable, wine quality score (3 to 8, integer, based on sensory evaluation).

**Derived Target**:

- The notebook uses a binary target variable `tasty`, likely derived from `quality` (e.g., `tasty = 1` if `quality` >/7, `tasty = 0` otherwise). The distribution shows 1,382 non-tasty (0) and 217 tasty (1) samples, indicating an imbalanced dataset.

**Key Details**:

- **Data Volume**: 1,599 samples.  
- **Number of Features**: 12 (including `Unnamed: 0`, though likely dropped during modeling).  
- **Data Types**: 11 float64 (physicochemical features), 2 int64 (`Unnamed: 0`, `quality`).  
- **Missing Values**: None (all columns have 1,599 non-null entries).  
- **Value Ranges** (from `df.describe()`):  
  - `fixed.acidity`: 4.6 to 15.9 (mean: 8.32, median: 7.9).  
  - `volatile.acidity`: 0.12 to 1.58 (mean: 0.53, median: 0.52).  
  - `citric.acid`: 0.0 to 1.0 (mean: 0.27, median: 0.26).  
  - `residual.sugar`: 0.9 to 15.5 (mean: 2.54, median: 2.2).  
  - `chlorides`: 0.012 to 0.611 (mean: 0.087, median: 0.079).  
  - `free.sulfur.dioxide`: 1 to 72 (mean: 15.87, median: 14).  
  - `total.sulfur.dioxide`: 6 to 289 (mean: 46.47, median: 38).  
  - `density`: 0.99007 to 1.00369 (mean: 0.99675, median: 0.99675).  
  - `pH`: 2.74 to 4.01 (mean: 3.31, median: 3.31).  
  - `sulphates`: 0.33 to 2.0 (mean: 0.66, median: 0.62).  
  - `alcohol`: 8.4 to 14.9 (mean: 10.42, median: 10.2).  
  - `quality`: 3 to 8 (mean: 5.64, median: 6).  
- **Class Imbalance**: The `tasty` variable is imbalanced (86.4% non-tasty, 13.6% tasty), which may affect model performance.

---

