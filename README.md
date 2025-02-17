# Dementia Data Analysis and Model Evaluation

## Repository Files

- **Gradient_Boosting.ipynb**: Gradient Boosting model implementation for dementia dataset analysis.
- **Random_forest.ipynb**: Random Forest model for dementia detection.
- **SVC.ipynb**: Support Vector Classifier (SVC) implementation.
- **visualization.ipynb**: Visualizations of dementia data, including class distribution and correlation heatmaps.

## Overview

This project focuses on analyzing dementia data, processing and engineering features, and evaluating machine learning models using K-Fold Cross-Validation, feature selection, and data visualization.

---

## Project Structure

### Data Processing (`data_processing.py`)

This module preprocesses and cleans data:

- **`preprocess_data(df)`**  
  - Handles missing values for categorical and numerical data.
  - Encodes categorical features with `LabelEncoder`.
  
- **`select_chi_square_features(X, y, k='all')`**  
  - Selects features based on Chi-square scores and returns them in a DataFrame.

### Model Evaluation (`model_evaluation.py`)

This module provides model evaluation using K-Fold Cross-Validation:

- **`k_fold_cross_validation(model, X, y, k=5)`**  
  - Trains and evaluates the model with K-Fold Cross-Validation, returning an aggregated classification report.

### Feature Engineering (`feature_engineering.py`)

This module creates new features and scales data to improve model performance:

1. **`remove_high_corr_features(df, threshold=0.9)`**: Removes highly correlated features.
2. **`create_interaction_features(df, features)`**: Creates interaction terms between features.
3. **`create_polynomial_features(df, features, degree=2)`**: Generates polynomial features.
4. **`scale_features(df, features)`**: Standardizes selected features.
5. **`bin_continuous_features(df, feature_bins)`**: Bins continuous features based on provided ranges.

### Data Visualization (`visualization.ipynb`)

This notebook includes data visualizations to better understand the dementia dataset:

1. **Class Distribution**: Bar plot showing distribution across dementia groups.
2. **Missing Values Heatmap**: Highlights missing values in the dataset.
3. **Correlation Heatmap**: Displays correlations among features.
4. **Box Plots**: Visualizes outliers in each feature.

---

## Example Workflow

1. **Preprocess Data and Select Features**:
   ```python
   from data_processing import preprocess_data
   data = pd.read_csv('dementia_dataset.csv')
   X = preprocess_data(data.iloc[:, 3:])
   y = data.iloc[:, 2].values
  ```
2. **Apply Feature Engineering:**
  ```python
  from feature_engineering import apply_feature_engineering
  X = apply_feature_engineering(X)
  ```

3. **Train and Evaluate Model:**
  ```python
  from sklearn.ensemble import RandomForestClassifier
  from model_evaluation import k_fold_cross_validation

  model = RandomForestClassifier()
  avg_accuracy = k_fold_cross_validation(model, X, y)
  ```
---

## Dependencies

To install the dependencies for this project, please ensure you have Python installed (recommended version 3.6 or higher). The required libraries are listed in the `requirements.txt` file. You can install them using the following command:

```bash
pip install -r requirements.txt
```

- Python 3.x
- pandas
- scikit-learn
- numpy
- seaborn
- matplotlib

