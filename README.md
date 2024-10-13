# Forecasting Net Prophet: Analyzing MercadoLibre's Google Search Traffic and Stock Price Patterns

## Overview

This project aims to analyze Google search traffic data for MercadoLibre and investigate potential relationships between search trends and the company's stock price patterns. By understanding these patterns, we can gain insights into market behavior, optimize marketing strategies, and explore the predictability of stock movements based on public interest.

## Table of Contents

- [Introduction](#introduction)
- [Data Description](#data-description)
- [Methodology](#methodology)
  - [Step 1: Find Unusual Patterns in Hourly Google Search Traffic](#step-1-find-unusual-patterns-in-hourly-google-search-traffic)
  - [Step 2: Mine the Search Traffic Data for Seasonality](#step-2-mine-the-search-traffic-data-for-seasonality)
  - [Step 3: Relate the Search Traffic to Stock Price Patterns](#step-3-relate-the-search-traffic-to-stock-price-patterns)
  - [Step 4: Create a Time Series Model with Prophet](#step-4-create-a-time-series-model-with-prophet)
- [Results](#results)
- [Conclusions](#conclusions)
- [Dependencies](#dependencies)
- [License](#license)

## Introduction

MercadoLibre is the most popular e-commerce platform in Latin America, boasting over 200 million users. As a growth analyst at MercadoLibre, the goal of this project is to analyze financial and user data to uncover insights that can drive company growth. Specifically, this project explores whether predicting Google search traffic can translate into the ability to successfully trade the company's stock.

## Data Description

The project utilizes two primary datasets:

1. **Google Search Trends Data**: Hourly search traffic data for the term "MercadoLibre" sourced from Google Trends.
2. **Stock Price Data**: Historical stock price data for MercadoLibre, including closing prices, sourced from financial markets.

## Methodology

The analysis is divided into four main steps:

### Step 1: Find Unusual Patterns in Hourly Google Search Traffic

#### Objectives

- Identify any unusual patterns in Google search traffic.
- Connect these patterns to corporate financial events.

#### Actions

1. **Data Importation**: Read the search data into a Pandas DataFrame.
2. **Data Slicing**: Focus on May 2020, the month when MercadoLibre released its quarterly financial results.
3. **Visualization**: Plot the search traffic data for May 2020 to identify any unusual patterns.
4. **Traffic Calculation**: Calculate the total search traffic for May 2020.
5. **Comparison**: Compare May 2020's total search traffic to the monthly median across all months.

#### Findings

- **Increased Traffic**: The total search traffic for May 2020 was higher than the monthly median, indicating increased public interest during the release of financial results.

### Step 2: Mine the Search Traffic Data for Seasonality

#### Objectives

- Identify predictable seasonal patterns in the search traffic data.
- Use these patterns to optimize marketing efforts for better ROI.

#### Actions

1. **Hourly Analysis**: Group the data by the hour of the day and calculate average traffic.
2. **Daily Analysis**: Group the data by the day of the week and calculate average traffic.
3. **Weekly Analysis**: Group the data by the week of the year and calculate average traffic.
4. **Visualization**: Plot the average traffic for each grouping to identify trends.

#### Findings

- **Time of Day**: Search traffic peaks between 10 AM and 8 PM, with the highest popularity around midnight.
- **Day of the Week**: Tuesdays receive the most search traffic, with a decreasing trend towards the weekend.
- **Week of the Year**: Increased search traffic during weeks 40 to 50, suggesting higher interest in the fourth quarter.

### Step 3: Relate the Search Traffic to Stock Price Patterns

#### Objectives

- Explore any relationships between search traffic and stock price movements.
- Determine if search trends can predict stock volatility or returns.

#### Actions

1. **Stock Data Importation**: Read the stock price data into a DataFrame.
2. **Data Concatenation**: Merge the stock price data with the search trends data.
3. **Data Slicing**: Focus on the first half of 2020 (January to June) for analysis.
4. **Visualization**: Plot both search trends and stock prices over the selected period.
5. **Feature Engineering**:
   - **Lagged Search Trends**: Shift search trends data by one hour to see if past searches affect future stock prices.
   - **Stock Volatility**: Calculate a four-hour exponentially weighted moving standard deviation of stock returns.
   - **Hourly Stock Return**: Compute the percentage change in stock price on an hourly basis.
6. **Correlation Analysis**: Examine correlations between lagged search trends, stock volatility, and stock returns.

#### Findings

- **No Strong Predictive Relationship**: Low correlation values suggest that lagged search traffic does not predict stock volatility or hourly stock returns effectively.

### Step 4: Create a Time Series Model with Prophet

#### Objectives

- Forecast future search trends using the Prophet time series model.
- Understand the components contributing to the search trends.

#### Actions

1. **Data Preparation**: Format the data for Prophet by resetting the index and renaming columns to 'ds' (datestamp) and 'y' (value).
2. **Model Fitting**: Fit the Prophet model to the historical search trends data.
3. **Future Prediction**: Create a future DataFrame extending 2000 hours ahead (approximately 80 days) and generate forecasts.
4. **Visualization**:
   - **Forecast Plot**: Visualize the forecasted search trends.
   - **Components Plot**: Break down the forecast into trend, daily, weekly, and yearly components.
5. **Component Analysis**: Analyze the components to answer specific questions about search traffic patterns.

#### Findings

- **Near-Term Forecast**: The search traffic is expected to stabilize in the near term.
- **Greatest Popularity Time**: Midnight exhibits the greatest popularity in search traffic.
- **Most Active Day**: Tuesdays receive the highest search traffic.
- **Lowest Annual Point**: Search traffic reaches its lowest point around October.

## Results

The project successfully identified patterns and trends in MercadoLibre's search traffic and stock price data. While increased search traffic aligns with significant corporate events, such as the release of financial results, there is no strong predictive relationship between search trends and stock volatility or returns. The Prophet model provided insights into seasonal components, which can be valuable for marketing and strategic planning.

## Conclusions

- **Marketing Optimization**: Identifying peak hours and days for search traffic can help focus marketing efforts when user interest is highest.
- **Investment Insights**: Despite increased search traffic during key events, search trends alone are not reliable predictors of stock price movements.
- **Seasonality Awareness**: Understanding seasonal trends allows the company to prepare for periods of higher or lower public interest.

## Dependencies

- **Python Version**: Python 3.x
- **Libraries**:
  - `pandas`
  - `numpy`
  - `matplotlib`
  - `prophet` (formerly `fbprophet`)
  - `datetime`

## Usage

1. **Clone the Repository**: Download or clone the project files to your local machine.

2. **Install Dependencies**:

   - Run the following command to install the required libraries:

     ```
     pip install pandas numpy matplotlib prophet
     ```

3. **Run the Analysis**:

   - Ensure that you have the necessary datasets (`google_hourly_search_trends.csv` and `mercado_stock_price.csv`) in the project directory.
   - Run the Python script or Jupyter Notebook to execute the analysis step by step.

4. **View Results**:

   - The script will generate plots and outputs for each step of the analysis.
   - Review the visualizations and printed findings to understand the patterns and conclusions.

## License

This project is provided for educational purposes and does not carry any specific license.

---

**Note**: Ensure that you have the correct versions of all libraries installed. If you encounter any issues with the `prophet` library, refer to the official [Prophet documentation](https://facebook.github.io/prophet/docs/installation.html) for installation guidance.
