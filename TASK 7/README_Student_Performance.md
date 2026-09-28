# Student Performance Data Analysis

## Project Overview

This project focuses on understanding, cleaning, and analyzing a **Student Performance Dataset** using Python and Pandas.

The dataset contains information about students' demographic and educational background along with their Math, Reading, and Writing scores.

The project performs:

- Data understanding
- Data inspection
- Missing value checking
- Categorical feature cleaning
- Feature engineering
- Statistical analysis
- Basic data visualization preparation

## Objectives

- Understand the structure of the student performance dataset
- Identify the rows, columns, and data types
- Check for missing values
- Clean categorical features
- Create new features such as total score and average score
- Calculate statistical measures for subject scores
- Prepare the data for visualization and further analysis

## Technologies Used

- Python
- Pandas
- NumPy
- Jupyter Notebook / Google Colab

## Dataset Features

The dataset contains the following main features:

| Feature | Description |
|---|---|
| `gender` | Student's gender |
| `race/ethnicity` | Student's race/ethnicity group |
| `parental level of education` | Parent's education level |
| `lunch` | Type of lunch received |
| `test preparation course` | Whether the student completed test preparation |
| `math score` | Mathematics score |
| `reading score` | Reading score |
| `writing score` | Writing score |

### Engineered Features

| Feature | Description |
|---|---|
| `average_score` | Average of Math, Reading and Writing scores |
| `total_score` | Total of Math, Reading and Writing scores |

## Data Understanding

The following commands are used to understand the dataset:

```python
print(df.head())
print(df.info())
print(df.shape)
print(df.columns)
```

## Missing Value Check

```python
print(df.isnull().sum())
```

This identifies the number of missing values in each column.

## Statistical Summary

```python
print(df.describe())
```

This provides statistical information such as:

- Count
- Mean
- Standard deviation
- Minimum
- Maximum
- Quartiles

## Data Cleaning

The categorical columns are cleaned using `strip()` and `title()`.

```python
categorical_cols = [
    'gender',
    'race/ethnicity',
    'parental level of education',
    'lunch',
    'test preparation course'
]

for col in categorical_cols:
    df[col] = df[col].str.strip().str.title()

print(df[categorical_cols].head())
```
