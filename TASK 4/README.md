# AAPLE Stock Price Analysis

## Project Overview

This project analyzes **Apple Inc. (AAPL) stock price data** using Python. The project focuses on loading historical stock market data, converting the date column into a proper datetime format, and visualizing the **Open, High, Low, and Close (OHLC)** prices over time.

The visualization helps understand how Apple's stock prices have changed throughout the selected period.

## Objectives

The main objectives of this project are:

- Load the AAPL stock dataset.
- Convert the date column into datetime format.
- Analyze historical stock prices.
- Visualize Open, High, Low, and Close prices.
- Compare different stock price measures over time.

## Technologies Used

- **Python**
- **Pandas**
- **NumPy**
- **Matplotlib**
- **Seaborn**
- **Jupyter Notebook / Google Colab**

## Dataset

The project uses:

**The dataset contains historical stock market information for Apple Inc. (AAPL).**

Important columns include:

Column	Description
Date	Trading date
Open	Opening price
High	Highest price during the trading period
Low	Lowest price during the trading period
Close	Closing price

## 1. Import Libraries

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

**Libraries Used**

  -  Pandas – reading and processing the dataset.
  - NumPy – numerical operations.
  - Matplotlib – creating the stock price visualization.
  - Seaborn – available for additional statistical visualizations.


2. Load the Dataset

file_path = '/AAPL.csv'

`df = pd.read_csv(file_path)`

The AAPL.csv file is loaded into a Pandas DataFrame called df.

3. Convert Date Column

`df["Date"] = pd.to_datetime(df["Date"])`

Converts the Date column into Pandas datetime format.

This is important because it allows the date to be used correctly on the X-axis of the time-series chart.

4. OHLC Price Visualization

The following code plots the four main stock prices:

plt.plot(
    df["Date"],
    df["Open"],
    label="Open"
)

plt.plot(
    df["Date"],
    df["High"],
    label="High"
)

plt.plot(
    df["Date"],
    df["Low"],
    label="Low"
)

plt.plot(
    df["Date"],
    df["Close"],
    label="Close"
)

plt.title("AAPL OHLC Prices Over Time")
plt.xlabel("Date")
plt.ylabel("Price")
plt.legend()
plt.show()

Chart Components

-   X-axis → Date
-  Y-axis → Stock Price
-   Open → Price at the beginning of the trading period
-   High → Highest price during the trading period
-   Low → Lowest price during the trading period
-   Close → Price at the end of the trading period
## OHLC Analysis

OHLC stands for:

O → Open
H → High
L → Low
C → Close

The line chart allows comparison of these four prices over time.

It can help identify:

   - Overall price movements
   - Periods of increasing or decreasing prices
   - Differences between opening and closing prices
   - High and low price ranges
   - General historical trends
Project Workflow

`AAPL Stock Dataset
        ↓
Load CSV File
        ↓
Read Data Using Pandas
        ↓
Convert Date to Datetime
        ↓
Select OHLC Columns
        ↓
Create Line Plot
        ↓
Compare Stock Prices Over Time`

Future Improvements

The project can be extended by adding:

  -  Daily returns calculation
  -  Moving averages such as 20-day and 50-day MA
  -  Trading volume analysis
  -  Return distribution histogram
  -  Correlation analysis
  -  Candlestick charts
  -  Volatility analysis
  -  Stock price forecasting
OUTPUT
<img width="1005" height="584" alt="image" src="https://github.com/user-attachments/assets/16cf5988-829d-4ec4-a275-c1d09ded80be" />


## Conclusion

This project demonstrates how Python can be used to perform basic financial time-series analysis. The AAPL dataset is loaded and processed using Pandas, and Matplotlib is used to visualize the Open, High, Low, and Close prices over time.

The project provides a foundation for more advanced stock market analysis and financial data visualization.
