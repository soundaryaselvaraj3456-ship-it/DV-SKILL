## TASK-3- AAPL Stock Price Analysis

## Project Overview

This project performs a basic analysis of **Apple Inc. (AAPL) stock data** using Python and Pandas.

The analysis focuses on loading the AAPL dataset, inspecting the data, checking for missing values in important price attributes, and calculating the **daily price delta** and **daily percentage return**.

---

## Objectives

- Load AAPL stock data from a CSV file.
- Inspect the structure and statistical summary of the dataset.
- Convert the `Date` column into datetime format.
- Check missing values in important stock attributes.
- Calculate the daily price difference between the opening and closing prices.
- Calculate the daily percentage return.

---

## Technologies Used

- **Python**
- **Pandas** – Data loading and analysis
- **NumPy** – Numerical operations
- **Matplotlib** – Data visualization
- **Seaborn** – Statistical visualization

---

## Dataset

The project uses an `AAPL.csv` file containing Apple stock market data.

### Important Columns

| Column | Description |
|--------|-------------|
| `Date` | Trading date |
| `Open` | Opening stock price |
| `High` | Highest price of the day |
| `Low` | Lowest price of the day |
| `Close` | Closing stock price |
| `Volume` | Number of shares traded |

---

## Data Inspection

The dataset is inspected using:

`python
display(df.head())
print(df.info())
print(df.describe())`

**These commands are used to:**  
-Display the first five records.
-Check column names and data types.
-Check the number of rows and non-null values.
-View statistical information such as mean, minimum, maximum, and standard deviation.
---
## Data Cleaning
Date Conversion

The Date column is converted into datetime format:

`df["Date"] = pd.to_datetime(df["Date"])
Select Important Price Attributes`

The important price attributes are selected:

`price_cols = ["Open", "High", "Low", "Close", "Volume"]
Check Missing Values`

Missing values are checked using:

`print(df[price_cols].isnull().sum())`

## Feature Engineering
**1. Daily Price Delta**

The daily price delta is calculated as:

Price Delta = Close − Open

`df["Price_Delta"] = df["Close"] - df["Open"]`

Interpretation:

  -Positive value → Closing price is higher than opening price.
  - Negative value → Closing price is lower than opening price.
  - Zero → Opening and closing prices are the same.

**2. Daily Percentage Return**

The daily percentage return is calculated using:

Daily Return (%) = ((Close − Open) / Open) × 100

`df["Daily_Return_%"] = (
    (df["Close"] - df["Open"]) / df["Open"]
) * 100`

This shows the percentage change between the opening and closing price during a trading day.

---
## Final Output

The analysis displays the following columns:

`Date
Open
High
Low
Close
Volume
Price_Delta
Daily_Return_%`

Example:

`print(df[[
    "Date",
    "Open",
    "High",
    "Low",
    "Close",
    "Volume",
    "Price_Delta",
    "Daily_Return_%"
]].head())`

## Analysis Performed

The project currently performs:

   - Dataset preview
   -  Dataset information analysis
   - Statistical summary
   - Date conversion
   - Missing-value checking
   - Daily price delta calculation
   - Daily percentage return calculation

## Future Improvements

The project can be extended with:

  - Stock price trend visualization
  -  Trading volume analysis
  -  20-day and 50-day moving averages
  -  Daily return distribution
  -  Correlation heatmap
  -  OHLC price charts
  -  Volatility analysis
  -  Monthly and yearly performance analysis

  ##  Project Structure

AAPL-Stock-Analysis/
│
├── AAPL.csv
├── aapl_analysis.py
└── README.md

## Conclusion

This project provides a basic foundation for analyzing AAPL stock price movements. By calculating the daily price delta and percentage return, the analysis helps identify whether the stock price increased or decreased from the opening price to the closing price on each trading day.
