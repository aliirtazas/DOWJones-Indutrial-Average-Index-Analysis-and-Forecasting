# DOWJones-Indutrial-Average-Index-Analysis-and-Forecasting
Finding relationships between individual stocks and the DOW Jones index and forecasting using time series and LSTM

**Introduction**
This project looks to examine the relationships between individual stocks and the DOW Jones index, aiming to unravel the intricate dynamics that influence overall market fluctuations. Through various analysis methodologies, we seek to identify underlying patterns and correlations, providing valuable insights into the factors shaping market performance. Taking our investigation, a step further, we utilize the LSTM-based time series analysis, our focus extends to forecasting DOW Jones index movements, offering a sophisticated perspective for investors and analysts. This inquiry aspires to contribute to a nuanced understanding of market behavior, fostering informed decision-making in the dynamic realm of financial markets.

**Data Extraction**
To construct the dataset, we initiate the process by extracting the most recent DOW Jones tickers from the source "https://stockmarketmba.com/stocksinthedjia.php" using the 'BeautifulSoup' library. This information is then organized into a comprehensive list. Subsequently, leveraging the 'yfinance' library, we proceed to retrieve stock values dating back to September 1, 2020. This specific start date is chosen for its proximity to the latest index modifications, ensuring we capture relevant changes in the composition of the index. Implementing a loop on the compiled list of tickers and utilizing the pdr.get_data_yahoo() function, we obtain the values of each stock, storing them temporarily in a dataframe. We focus on extracting the adjusted close prices for each stock, creating a structured dataframe named 'df' with columns labeled [‘ticker’ + _close]. This organized dataframe proves versatile for subsequent analysis and can be effortlessly exported to a CSV file. Furthermore, we extend our data gathering efforts to encompass historical data for the DOW Jones Industrial Average (DJI), spanning from January 3, 1984. This historical dataset serves as a crucial foundation for the application of Long Short-Term Memory (LSTM) in time series forecasting, enhancing the depth and context of our analytical endeavors.

**Data Dictionary**

Stocks_in_DJI.csv

| Column Name   | -- | Description                                         |
|---------------|----|-----------------------------------------------------|
| Date          | -- | Date of stock price                                 |
| UNH_close     | -- | Adjusted closing price for UnitedHealth Group Inc.  |
| MSFT_close    | -- | Adjusted closing price for Microsoft Corp.          |
| GS_close      | -- | Adjusted closing price for Goldman Sachs Group Inc. |
| HD_close      | -- | Adjusted closing price for Home Depot Inc.          |
| MCD_close     | -- | Adjusted closing price for McDonald’s Corp.         |
| AMGN_close    | -- | Adjusted closing price for Amgen Inc.               |
| V_close       | -- | Adjusted closing price for Visa Inc.                |
| CAT_close     | -- | Adjusted closing price for Caterpillar Inc.         |
| CRM_close     | -- | Adjusted closing price for Salesforce Inc.          |
| BA_close      | -- | Adjusted closing price for Boeing Co.               |
| HON_close     | -- | Adjusted closing price for Honeywell International Inc. |
| AAPL_close    | -- | Adjusted closing price for Apple Inc.               |
| TRV_close     | -- | Adjusted closing price for Travelers Co. Inc.       |
| AXP_close     | -- | Adjusted closing price for American Express Co.     |
| WMT_close     | -- | Adjusted closing price for Walmart Inc.             |
| IBM_close     | -- | Adjusted closing price for Intl Business Machines Corp. |
| PG_close      | -- | Adjusted closing price for Procter & Gamble Co.     |
| JPM_close     | -- | Adjusted closing price for JPMorgan Chase & Co.     |
| JNJ_close     | -- | Adjusted closing price for Johnson & Johnson        |
| CVX_close     | -- | Adjusted closing price for Chevron Corp.            |
| NKE_close     | -- | Adjusted closing price for Nike Inc.                |
| MRK_close     | -- | Adjusted closing price for Merck & Co. Inc.         |
| MMM_close     | -- | Adjusted closing price for 3M Co.                   |
| DIS_close     | -- | Adjusted closing price for Walt Disney Co.          |
| KO_close      | -- | Adjusted closing price for Coca-Cola Co.            |
| DOW_close     | -- | Adjusted closing price for Dow Inc.                 |
| CSCO_close    | -- | Adjusted closing price for Cisco Systems Inc.       |
| INTC_close    | -- | Adjusted closing price for Intel Corp.              |
| VZ_close      | -- | Adjusted closing price for Verizon Communications Inc. |
| WBA_close     | -- | Adjusted closing price for Walgreens Boots Alliance Inc. |
| ^DJI_close    | -- | Adjusted closing price for Dow Jones Industrial Average Index (Market Value) |
-----------------------------------------------------------------------------------------------------

DJI_Stock_Since_Start.csv:
| Column Name | -- | Description                                      |
|-------------|----|--------------------------------------------------|
| Date        | -- | Date of stock price                              |
| Open        | -- | Opening price for DJI on that day                |
| High        | -- | Highest price for DJI on that day                |
| Low         | -- | Lowest price for DJI on that day                 |
| Close       | -- | Closing price for DJI on that day                |
| Adj_Close   | -- | Adjusted closing price for DJI on that day       |
| Volume      | -- | Volume of index (stock)                          |
