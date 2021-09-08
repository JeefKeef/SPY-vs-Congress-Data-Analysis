# Data Analysis Project Comparing SPY vs Congress Member's performance.
Author: Jeffreyson Nguyen

## Objective
The S&P500 have been known as the most difficult benchmark to beat among investors. The project will analyze the performance of U.S senate members' stock purchases against the SPY, to see whether they outperform the SPY. To measure this, data will be collected from senate member’s stock purchases, along with the date and closing price. This data will be compared with the SPY price within 2 weeks, 1 month, and 3 month. The unit of measure will be the percentage gain of the stock from purchase price to the price that will be 2 weeks to 3 months out and compared to the SPY. In addition, I will be displaying the top performing and worst performing senate members using the percentage gain as the unit of measure. 

## How to run code?
1. Download ipynb and CSV files
2. Upload to JupyterLab
3. pip install yfinance
4. Click on Kernel
5. Restart Kernel and Run All Cells
6. Click Restart
7. Repeat Step 4 to 6 with Data Collection, Data Exploration, and Machine Learning ipynb files.

## Data Collection and Cleaning
### Dataset
1. House data :https://housestockwatcher.com/api
* This dataset will provide information of U.S Senate members stock purchases, including the stock ticker name, closing price, date of purchase, senate name, and the amount of money spent.
2. Senate data: https://senatestockwatcher.com/api
* This dataset will provide information of U.S House members stock purchases, including the stock ticker name, closing price, date of purchase, senate name, and the amount of money spent.
3. SPY data: https://www.nasdaq.com/market-activity/funds-and-etfs/spy/historical
* This dataset will provide the historical data of SPY. The information includes the data, closing price, volume, opening price, high of day and low of day prices.
4. yfinance
* Used this module to retreive individual stock price historical data and store into CSV file. Webscrapping was difficult due to iframes and dynamic webpages. API request using Rapid API only limits 5 requests per minute. Thus, resorting to yfinance was necessary. However, data gathering took 2 hours to complete, thus saving to CSV file was recommended.

Data of senate members are collected through CSV file. Data frame is constructed by selecting the following columns: stock ticker, transaction date when the purchase was made, the type of purchase option between stock or options, the type of purchase the senator made whether it was a purchase or a sale, and the senator name.

The columns were chosen because it will be relevant for the project.

1. Track transaction date

2. Filter out asset type for only stock purchases

3. Purchase type will be filtered out for purchases only

4. Senator name - to track individual performances

The senate data frame is cleaned, removing any rows containing NaN, N/A, --, to avoid invalid data.

Asset types is filtered out to "Stock" only because this project is detecting Stocks only.

Type column is filtered out to contain only "Purchases" because the scope of this project is to track purchases made from congress members.

Data of house members are collected through CSV file. Data frame is constructed by selecting the following columns: stock ticker, transaction date when the purchase was made, the type of purchase option between stock or options, the type of purchase the senator made whether it was a purchase or a sale, and the senator name.

The columns were chosen because it will be relevant for the project.

1. Track transaction date

2. Filter out asset type for only stock purchases

3. Purchase type will be filtered out for purchases only

4. House name - to track individual performances

The house data frame is cleaned, removing any rows containing NaN, N/A, --, to avoid invalid data.

Asset types is filtered out to "Stock" only because this project is detecting Stocks only.

Type column is filtered out to contain only "Purchases" because the scope of this project is to track purchases made from congress members.

Senate and House Dataframe is appended to each other, creating more data and is renamed to Congress.

The SPY Price is collected using the date of purchase made from the Congress member. The date is searched from the SPY dataframe and collect the closing price of SPY on that specific date. The price is then stored into a list to keep track of each stock purchased from different congress members. The data of purchase is also used to find the price of SPY 1 - 12 weeks out from purchase to create 1 week, 2 week, 1 month, and 3 month columns, containing the prices of SPY from the orginal purchase price of SPY.

Collected congress member ticker prices on date of purchase, and 1 week, 2 week, 1 month, and 3 month prices using yfinance.
- Prices are saved into CSV file since collecting data took 2 hours.
- Data is clean from NaN

Data is cleaned from unknown datas which includes ticker symbol changes or company bankruptcy.

Combined all dataframes into one dataframe.

- Calculated percentage gains from 1 week, 2 week, 1 month, 3 month, from both SPY and congress ticker price

## Data Exploration
#### Goals: Visualize data collected which includes: average percentage gain from 1-12 weeks from purchase data(SPY vs Congress), Best and worst performing congress member basaed on 1-12 month gain, Highest and lowest Congress member made, Top stocks traded fromm top three congress member, and taking a look at the best performing congress member performancce against SPY by date.
#### Results:
The data shows that Congress beats SPY by a huge margin in each time range from the price of purchase.
1. 1 week: SPY had 0.02% in gains and the average congress members had 1.57% in gains.

2. 2 week: SPY had 0.36% in gains and congress had 1.7% in gains.

3. 1 month: SPY had 0.78% in gains and congress had 3.6% in gains.

4. 3 month: SPY had -1.59% in gains and congress had 8.9% in gains.

5. Congress made the largest gains in 3 months while SPY largest gain is 1 month from purchase. 

6. Congress largest gain is 2222% in the 1 week time frame and largest lose is -231% within the 1 week time frame.

7. The scatter graph also shows that the majority of trades happened between 2019 to 2021. Is is also where the largest gains and lost are for congress. My prediction is that COVID 19 affected the stock market causing the stock market to be volatile.

8. SPY seem to have the less gains and loses while congress gets higher gains and loses.

9. SPY also had its largest lost in 2020 of March, due to the COVID-19 pandemic.

## Machine Learning
#### Linear Regression is applied to predict the SPY price of the next 30 days utilizing the last 10 days as testing data. KNN classifier is also used to predict whether the next day SPY would close higher than the previous day.
### KNN Classifier Features
1. Features added was High_Low_Diff, which is the daily high and low difference of SPY.

2. Features also included a classification label called class, which is label as 0 and 1. 0 meaning false, 1 meaning true. It searches if the SPY closed higher than the previous day.

3. Volume was used as a feature because volume indicates whether SPY was traded alot or not. With higher volume means more trading activity is happening, and lower means none. It could help determine the price of SPY.

## Concluding Thoughts
From the data gathered, I justify that congress indeed beats the SPY significantly. A hypothesis I came up with could be due to insider trading, where they have insider knowledge of potential news of the stock company that is about to be announced.








