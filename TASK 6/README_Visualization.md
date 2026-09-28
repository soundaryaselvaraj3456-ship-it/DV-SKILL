# Healthcare Data Analysis and Visualization

## Project Overview

This project performs **Healthcare Data Analysis and Visualization** using Python. The dataset contains patient information such as age, medical condition, admission date, discharge date, insurance provider, and billing amount.

The project focuses on data understanding, data cleaning, feature engineering, statistical analysis, and visualization to identify useful patterns in healthcare data.

## Objectives

- Understand the healthcare dataset
- Identify missing values
- Convert date columns into datetime format
- Calculate the number of days each patient stayed in the hospital
- Analyze billing amounts by medical condition and insurance provider
- Analyze monthly patient admissions
- Study the relationship between age, hospital stay, and billing amount
- Visualize healthcare data using different charts

## Technologies Used

- Python
- Pandas
- Matplotlib
- Seaborn
- Jupyter Notebook / Google Colab

## Dataset Features

The dataset contains healthcare-related information such as:

| Feature | Description |
|---|---|
| `Name` | Patient name |
| `Age` | Patient age |
| `Gender` | Patient gender |
| `Medical Condition` | Patient's medical condition |
| `Date of Admission` | Date of hospital admission |
| `Discharge Date` | Date of discharge |
| `Insurance Provider` | Patient's insurance provider |
| `Billing Amount` | Hospital billing amount |

### Engineered Features

| Feature | Description |
|---|---|
| `No_of_days_stay` | Number of days the patient stayed in the hospital |
| `Admission Month` | Month in which the patient was admitted |

## 🔍 Data Understanding

The dataset is loaded using Pandas:

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

df = pd.read_csv("Healthcare.csv")
```

### Output

<!-- Add your output screenshots below, e.g. ![Output 1](images/output1.png) -->

![Output 1](images/output1.png)
![Output 2](images/output2.png)
![Output 3](images/output3.png)
![Output 4](images/output4.png)
![Output 5](images/output5.png)

### View Column Names

```python
print(df.columns)
```

### Check Missing Values

```python
print(df.isnull().sum())
```

This identifies the number of missing values in each column.

## Data Cleaning

The admission and discharge date columns are converted into datetime format:

```python
df['Date of Admission'] = pd.to_datetime(df['Date of Admission'])
df['Discharge Date'] = pd.to_datetime(df['Discharge Date'])
```
