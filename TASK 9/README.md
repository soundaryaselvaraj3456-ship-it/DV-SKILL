# **TASK 9-House Sales Data Understanding, Cleaning & Feature Engineering**

## **Project Overview**

This project focuses on understanding, cleaning, and performing feature engineering on a house sales dataset using Python. The dataset contains information about property prices, bedrooms, bathrooms, living area, lot size, construction year, renovation year, and sale dates.

The main objective is to improve data quality, extract meaningful property-related features, calculate price-per-square-foot metrics, and identify extreme valuation outliers using statistical methods and visualizations.

Python libraries such as **Pandas, NumPy, Matplotlib, and Seaborn** are used for data processing, numerical analysis, and visualization.

## **Objectives**

- **Understand the Dataset:** Explore the structure, columns, data types, and statistical properties of the house sales dataset.
- **Handle Missing Values:** Identify and remove missing entries in important property attributes.
- **Clean Invalid Values:** Handle invalid zero or negative values in bedroom counts, bathroom counts, property prices, and area measurements.
- **Process Sale Dates:** Convert sale dates into a proper datetime format and extract the sales year.
- **Perform Feature Engineering:** Create new features related to property age, renovation status, and years since renovation.
- **Calculate Valuation Metrics:** Compute price per square foot for living area and total lot size.
- **Detect Outliers:** Identify extreme property valuation values using box plots and the Interquartile Range (IQR) method.
- **Export Cleaned Data:** Save the processed dataset with newly engineered features for future analysis.

## **Dataset Description**

The project uses the **King County House Sales Dataset**, which contains property sales information.

Important columns used in this project include:

- **price:** Sale price of the property.
- **bedrooms:** Number of bedrooms in the house.
- **bathrooms:** Number of bathrooms in the house.
- **sqft_living:** Interior living area measured in square feet.
- **sqft_lot:** Total lot size measured in square feet.
- **grade:** Overall construction and design quality grade.
- **yr_built:** Year in which the property was constructed.
- **yr_renovated:** Year in which the property was renovated, if applicable.
- **date:** Date on which the property was sold.

These attributes help analyze property characteristics, calculate valuation metrics, and understand the relationship between property age and sales information.

## **Technologies Used**

- **Python** – Main programming language for data analysis.
- **Pandas** – Dataset loading, cleaning, transformation, and feature engineering.
- **NumPy** – Numerical calculations and data manipulation.
- **Matplotlib** – Creating box plots and visualizing valuation distributions.
- **Seaborn** – Supporting statistical data visualization.
- **Google Colab / Jupyter Notebook** – Executing Python code and analyzing results.

## **Project Workflow**

### **1. Importing Required Libraries**

The project begins by importing the required Python libraries.

- **Pandas** is used to load and manipulate the dataset.
- **NumPy** supports numerical operations.
- **Matplotlib** creates visualizations.
- **Seaborn** provides additional statistical plotting capabilities.

These libraries form the foundation for the data understanding and feature engineering process.

### **2. Loading the Dataset**

The house sales dataset is loaded into a Pandas DataFrame using `pd.read_csv()`.

Initial inspection is performed using the following methods:

- `head()` – Displays the first five records.
- `tail()` – Displays the last five records.
- `info()` – Shows column names, data types, and non-null counts.
- `shape` – Returns the number of rows and columns.
- `describe()` – Generates descriptive statistics for numerical columns.
- `columns` – Displays all column names.

This step provides an overview of the dataset before cleaning and transformation.

### **3. Checking Missing Values and Duplicates**

Missing values and duplicate records are examined to understand the quality of the dataset.

- `isnull().sum()` identifies missing values in each column.
- `duplicated().sum()` counts duplicate rows.

Missing entries in essential columns are handled during the cleaning process. The project removes records that do not contain the required information for property valuation and feature calculations.

This improves the reliability of the dataset used in subsequent analysis.

### **4. Property Feature Inspection**

Important property attributes are selected for detailed inspection.

The selected features include:

- **Bedrooms**
- **Bathrooms**
- **Living Area**
- **Grade**
- **Year Built**

The project displays sample records and descriptive statistics for these columns.

This helps understand the distribution of property characteristics and identify values that may require additional validation.

### **5. Data Cleaning and Invalid Value Handling**

Data cleaning is performed to improve the accuracy and consistency of the dataset.

The following operations are included:

- Replace bedroom counts less than or equal to zero with missing values.
- Replace bathroom counts less than or equal to zero with missing values.
- Remove records with missing values in essential columns such as price, bedrooms, bathrooms, living area, lot size, construction year, and sale date.
- Remove records where the property price is zero or negative.
- Remove records where living area or lot size is zero or negative.
- Convert sale dates into datetime values and remove records with invalid dates.

These operations ensure that the essential attributes used for valuation calculations contain valid positive values.

### **6. Sale Date Processing**

The `date` column is converted into a datetime format using Pandas.

The conversion allows the extraction of temporal information from the original sale date.

A new feature, **sales_year**, is created to represent the year in which each property was sold.

This feature supports calculations involving property age and renovation timelines.

### **7. Property Age Calculation**

A new feature called **property_age** is created using the sale year and construction year.

**Formula:**

`property_age = sales_year - yr_built`

This feature estimates how old the property was when it was sold.

Properties with negative calculated ages are treated as invalid, because their recorded construction year occurs after the sale year.

The resulting feature can be used to study differences in property age and understand property valuation patterns.

### **8. Renovation Feature Engineering**

The dataset includes a renovation year, which is used to derive additional renovation-related features.

#### **Renovation Status**

A new column named **is_renovated** is created.

- **1:** The property has a recorded renovation year greater than zero.
- **0:** No renovation year is recorded.

This converts the renovation information into a binary feature suitable for further analysis.

#### **Years Since Renovation**

A new feature called **years_since_renovation** is calculated using the sale year and renovation year.

**Formula:**

`years_since_renovation = sales_year - yr_renovated`

The calculation is applied only to properties with a recorded renovation year.

Values are treated as invalid when the renovation year is later than the sale year or occurs before the original construction year. Such values are set to missing.

This feature helps represent the time elapsed since a property's recorded renovation.

### **9. Price Per Square Foot for Living Area**

The project calculates a valuation metric based on the interior living area.

**Formula:**

`price_per_sqft_living = price / sqft_living`

This feature measures the sale price relative to the property's living area.

It can be used to compare properties of different sizes and examine how much buyers pay per square foot of interior living space.

### **10. Price Per Square Foot for Lot Size**

A second valuation metric is created using the total lot size.

**Formula:**

`price_per_sqft_lot = price / sqft_lot`

This feature measures the sale price relative to the total land area.

Using both living-area and lot-size metrics provides two different perspectives on property valuation.

- **Living Area Valuation:** Relates the property price to the usable interior area.
- **Lot Size Valuation:** Relates the property price to the total land area.

These metrics are analyzed separately because living area and lot size represent different property characteristics.

### **11. Outlier Detection Using the IQR Method**

The Interquartile Range (IQR) method is used to identify unusually low or high valuation metrics.

The analysis is performed separately for:

- **price_per_sqft_living**
- **price_per_sqft_lot**

The first quartile (**Q1**) represents the 25th percentile, while the third quartile (**Q3**) represents the 75th percentile.

**Formula:**

`IQR = Q3 - Q1`

The lower and upper statistical bounds are calculated as follows:

- **Lower Bound:** `Q1 - 1.5 * IQR`
- **Upper Bound:** `Q3 + 1.5 * IQR`

Values below the lower bound or above the upper bound are marked as potential outliers.

The project creates separate Boolean outlier columns for both valuation metrics and prints the calculated bounds and number of flagged observations.

These flags identify unusual values for further investigation. They do not automatically remove the outliers from the dataset.

### **12. Data Visualization Using Box Plots**

Box plots are created to visualize the distribution of both price-per-square-foot metrics.

Two plots are displayed:

- **Price per Square Foot – Living Area**
- **Price per Square Foot – Lot Size**

Box plots help identify the median, spread, quartiles, and potential extreme observations in each distribution.

By comparing the two plots, it becomes easier to understand how valuation metrics vary and where unusually high or low values occur.

Matplotlib is used to create the visualizations and display them side by side.

### **13. Exporting the Processed Dataset**

The dataset is exported to a CSV file after feature engineering.

The project uses the filename:

`kc_house_data_feature_engineered.csv`

The exported dataset includes the original property information along with engineered features such as:

- **sales_year**
- **property_age**
- **is_renovated**
- **years_since_renovation**
- **price_per_sqft_living**
- **price_per_sqft_lot**
- **Outlier indicator columns**

The file can be reused for additional data analysis, visualization, statistical exploration, or machine learning preparation.

## **Key Features Created**

| Feature | Description |
|---|---|
| **sales_year** | Year in which the property was sold |
| **property_age** | Property age at the time of sale |
| **is_renovated** | Indicates whether a renovation year is recorded |
| **years_since_renovation** | Years elapsed since the recorded renovation |
| **price_per_sqft_living** | Sale price divided by living area |
| **price_per_sqft_lot** | Sale price divided by lot size |
| **price_per_sqft_living_outlier** | Flags potential living-area valuation outliers |
| **price_per_sqft_lot_outlier** | Flags potential lot-size valuation outliers |

## **Expected Outcomes**

After completing the workflow, the project produces:

- A better understanding of the house sales dataset.
- Improved data quality through missing-value and invalid-value handling.
- Properly formatted sale dates and extracted temporal attributes.
- New features representing property age and renovation information.
- Two price-per-square-foot valuation metrics.
- Statistical bounds for identifying potential valuation outliers.
- Box plots for comparing valuation distributions.
- An exported CSV dataset containing the processed data and engineered features.

## **Conclusion**

The **House Sales Data Understanding, Cleaning & Feature Engineering** project demonstrates a structured approach to preparing real estate data for analysis.

It combines dataset exploration, data cleaning, date processing, temporal feature engineering, valuation metric calculations, statistical outlier detection, and box plot visualization.

The resulting dataset is more suitable for further analytical tasks because important attributes are cleaned, useful features are derived, and potential extreme valuation observations are explicitly identified.

This project provides a foundation for more advanced real estate analytics and future house price prediction models using Python.
