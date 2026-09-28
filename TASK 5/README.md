# Healthcare Dataset Analysis

## Project Overview

This project performs **Healthcare Dataset Analysis** using Python. The dataset contains patient-related information such as medical conditions, admission and discharge dates, admission types, gender, medical codes, and billing amounts.

The project covers data understanding, data cleaning, exploratory data analysis, and feature engineering to identify useful patterns in healthcare data.

## Objectives

- Load and understand the healthcare dataset
- Inspect dataset columns and structure
- Identify missing values
- Check missing values in specific columns
- Convert admission and discharge dates into datetime format
- Clean categorical data
- Analyze different admission types
- Analyze billing amounts statistically
- Calculate hospital stay duration
- Analyze the relationship between medical conditions and gender

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Jupyter Notebook / Google Colab

## Dataset

The project uses `healthcare_dataset.csv`, which contains healthcare-related patient information.

### Important Features

| Feature | Description |
|---|---|
| `Medical_Code` | Code associated with the medical record |
| `Admission_Date` | Date on which the patient was admitted |
| `Discharge_Date` | Date on which the patient was discharged |
| `Admission_Type` | Type of hospital admission |
| `Gender` | Patient gender |
| `Medical_Condition` | Patient's medical condition |
| `Billing_Amount` | Amount billed for healthcare services |

### Engineered Feature

| Feature | Description |
|---|---|
| `Hospital_Stay_Days` | Number of days between admission and discharge |

## Project Workflow

```
Healthcare Dataset
       ↓
Load Dataset
       ↓
Understand Data
       ↓
Check Columns
       ↓
Check Missing Values
       ↓
Convert Date Columns
       ↓
Clean Admission Type
       ↓
Analyze Admission Types
       ↓
Analyze Billing Amount
       ↓
Calculate Hospital Stay
       ↓
Analyze Medical Condition vs Gender
```

## Implementation

### 1. Import Libraries

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

- **Pandas** – data manipulation and analysis
- **NumPy** – numerical operations
- **Matplotlib** – data visualization
- **Seaborn** – statistical visualization

### 2. Load the Dataset

```python
df = pd.read_csv("healthcare_dataset.csv")
```

The CSV file is loaded into a Pandas DataFrame called `df`.

### 3. Data Understanding

View the first five records:

```python
df.head()
```

Display column names:

```python
df.columns
```

### 4. Missing Value Analysis

```python
# Check for missing values
df.isnull()

# Count missing values in each column
df.isnull().sum()

# Check a specific column
df['Medical_Code'].isnull().sum()
```

This identifies the number of missing values, including those in the `Medical_Code` column.

### 5. Date Conversion

```python
df['Admission_Date'] = pd.to_datetime(df['Admission_Date'])
df['Discharge_Date'] = pd.to_datetime(df['Discharge_Date'])
```

Converting to datetime format allows date calculations and time-based analysis.

### 6. Cleaning Admission Type

```python
df['Admission_Type'] = (
    df['Admission_Type']
    .str.strip()
    .str.lower()
)
```

- `str.strip()` removes unnecessary spaces
- `str.lower()` converts all text to lowercase

Example:

```
" Emergency " → "emergency"
"Urgent"      → "urgent"
```

This makes categorical values consistent.

### 7. Admission Type Analysis

Cross-tabulation of admission types across admission dates:

```python
pd.crosstab(df['Admission_Type'], df['Admission_Date'])
```

Frequency of each admission type:

```python
df["Admission_Type"].value_counts()
```

### 8. Billing Amount Analysis

```python
df["Billing_Amount"].describe()
```

This provides count, mean, standard deviation, minimum, 25th percentile, median, 75th percentile, and maximum.

### 9. Feature Engineering – Hospital Stay

```python
df['Hospital_Stay_Days'] = (
    df['Discharge_Date'] - df['Admission_Date']
).dt.days
```

Example:

```
Admission Date : 2025-01-01
Discharge Date : 2025-01-06
Hospital Stay  : 5 days
```

Statistical summary of hospital stay duration:

```python
display(df['Hospital_Stay_Days'].describe())
```

### 10. Medical Condition and Gender Analysis

```python
pd.crosstab(df["Medical_Condition"], df["Gender"])
```

This produces a frequency table showing the number of patients of each gender for each medical condition.

Example structure (actual values depend on the dataset):

| Medical_Condition | Female | Male |
|---|---|---|
| Diabetes | 120 | 115 |
| Asthma | 105 | 110 |
| Cancer | 130 | 125 |

## Analysis Summary

| Analysis | Method |
|---|---|
| Dataset inspection | `head()`, `columns` |
| Missing value analysis | `isnull().sum()` |
| Date processing | `pd.to_datetime()` |
| Categorical cleaning | `str.strip()`, `str.lower()` |
| Admission analysis | `value_counts()` |
| Billing analysis | `describe()` |
| Hospital stay | Date difference |
| Medical condition vs gender | `pd.crosstab()` |

## Project Structure

```
Healthcare-Data-Analysis/
│
├── healthcare_dataset.csv
├── Healthcare_Analysis.ipynb
└── README.md
```

## Conclusion

This project demonstrates a basic healthcare data analysis workflow using Python. The dataset is inspected for structure and missing values, date columns are converted into a usable format, admission types are cleaned, billing statistics are analyzed, hospital stay duration is calculated, and medical conditions are compared across gender.

The resulting dataset can be used for further exploratory data analysis and visualization.
