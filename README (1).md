# Credit Card Default Prediction

## Project Overview

This project explores a credit card customer dataset and prepares it for a machine learning classification task: predicting whether a customer will default on their next month's payment.

The notebook uses Python for data loading, inspection, cleaning, visualization, preprocessing, feature selection, and preparation of classification models.

## Dataset

The notebook expects a CSV file named **`creditcard.csv`** in the same folder as the Jupyter Notebook.

The columns used in the notebook include:

- Customer information: `LIMIT_BAL`, `SEX`, `EDUCATION`, `MARRIAGE`, `AGE`
- Repayment status: `PAY_0`, `PAY_2` to `PAY_6`
- Bill amounts: `BILL_AMT1` to `BILL_AMT6`
- Previous payment amounts: `PAY_AMT1` to `PAY_AMT6`
- Target: `default payment next month`

The target column indicates whether the customer defaulted on the next month's payment.

> Make sure the CSV file has the expected dataset and column names. The notebook contains more than one data-loading approach, so the CSV header format must match the section being run.

## Technologies and Libraries

- Python
- Jupyter Notebook
- NumPy
- Pandas
- Matplotlib
- Seaborn
- Scikit-learn

## Installation

Install the required libraries:

```bash
pip install numpy pandas matplotlib seaborn scikit-learn jupyter
```

If you are using the notebook's optional Excel-reading setup, install `xlrd` as well:

```bash
pip install xlrd
```

## How to Run

1. Download or place `creditcard.csv` in the project folder.
2. Place the notebook in the same folder.
3. Install the required Python libraries.
4. Open the notebook:

   ```bash
   jupyter notebook
   ```

5. Open `Untitled(1).ipynb`.
6. Run the cells in order, checking that the dataset columns match the names expected by each section.

## Project Workflow

### 1. Data Loading and Inspection

- Load the CSV dataset using Pandas.
- Display the first and last rows.
- Check the dataset shape, column names, data types, and descriptive statistics.
- Inspect missing values and duplicate rows.

### 2. Data Cleaning

- Remove unnecessary or unnamed index columns.
- Convert selected columns to numeric data types.
- Check the dataset structure and column names.

### 3. Outlier Treatment

The notebook applies the Interquartile Range (IQR) method to selected numerical columns.

- Calculate the first quartile (Q1) and third quartile (Q3).
- Calculate IQR = Q3 - Q1.
- Calculate the lower and upper limits using 1.5 × IQR.
- Clip values outside these limits.
- Display a boxplot after outlier treatment.

### 4. Data Visualization

The notebook uses Seaborn and Matplotlib to create visualizations, including:

- Boxplots for numerical features.
- A correlation heatmap for selected features.

### 5. Feature and Target Separation

- `X` contains the independent features.
- `y` contains the target column, `default payment next month`.
- The customer ID column is excluded from the predictors.

### 6. Data Preprocessing

The notebook prepares numerical and categorical features separately.

**Numerical features:**
- Missing values are handled using median imputation.
- Features are standardized using `StandardScaler`.

**Categorical features:**
- Missing values are handled using most-frequent imputation.
- Categories are encoded using `OneHotEncoder`.

A `ColumnTransformer` combines these preprocessing steps.

### 7. Feature Selection

The notebook uses `SelectKBest` with the `f_classif` scoring function to identify features with higher statistical scores for the classification task. It displays the selected features and their scores.

### 8. Train-Test Split

The dataset is split into:

- 80% training data
- 20% testing data

The split uses `random_state=42` and stratification to preserve the target-class proportions.

### 9. Classification Models

The notebook defines the following classification algorithms:

- Logistic Regression
- Decision Tree Classifier
- Random Forest Classifier

The notebook currently shows model definitions, but does not include a complete model-fitting and evaluation section.

## Evaluation Metrics Imported

The notebook imports these Scikit-learn metrics:

- Accuracy
- Precision
- Recall
- F1-score

These can be used to evaluate the classification models after training.

## Important Notes

- The notebook contains repeated and alternative data-loading and preprocessing cells. Run the intended workflow consistently rather than mixing sections that expect different CSV header formats.
- The notebook uses both `PAY_0` and a renamed `PAY_1` column in different sections. Keep the feature names consistent throughout the workflow.
- In the scaling section, the test data should be transformed using the scaler fitted on the training data (`scaler.transform(X_test)`), not fitted again on the test data.
- Feature selection is currently fitted on the full `X` dataset before the train-test split in one section. For a reliable evaluation, fit feature selection only on the training data, ideally as part of a Scikit-learn pipeline.
- Model training and final metric comparisons still need to be added.

## Project Status

**Exploratory data analysis and preprocessing:** Present in the notebook.

**Classification model setup:** Model objects are defined.

**Model training and evaluation:** Not completed in the current notebook.
