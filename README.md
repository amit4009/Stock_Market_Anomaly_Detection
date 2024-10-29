# Stock_Market_Anomaly_Detection
### <b>Project Overview</B>
<br>This project, Stock Market Anomaly Detection using Python, aims to identify unusual price and volume patterns in major stock tickers (AAPL, MSFT, NFLX, GOOG, and TSLA) over a recent one-year period. Using Z-score-based anomaly detection, the analysis reveals deviations from typical trading behavior, providing insights into market stability and highlighting potential investment risks.</br>

#### <b>Data Collection and Preparation</b>
<br>
**Source**: Data is collected from Yahoo Finance using the yfinance API.

**Tickers:** AAPL (Apple Inc.), MSFT (Microsoft Corporation), NFLX (Netflix, Inc.), GOOG (Alphabet Inc.), and TSLA (Tesla, Inc.).

**Time Period:** Covers a recent 365-day period.

**Attributes Collected:** Includes daily Open, High, Low, Close, Adjusted Close prices, and Volume for each stock.

### Data Download and Structuring:
**Date Range:** Defined from today back 365 days.

F**lattening MultiIndex:** The downloaded data, initially in MultiIndex format, is flattened into single-level column headers.

**Long Format Conversion:** The dataset is reshaped into a long format using the melt function, organizing data by date, ticker, and attribute.

**Indexing:** Converted the “Date” column to datetime format and set it as the index for efficient time-series processing.

### Data Visualization
*Adjusted Close Price Trends:*

A line graph visualizes adjusted closing prices for each stock, allowing us to observe general trends.

*Observations reveal:*

**GOOG** exhibits an uptrend with some volatility.

**AAPL** shows a steady increase, while TSLA shows a more volatile upward trend.

**MSFT** has a slight downward trend towards the end of the period, and NFLX displays a flatter trend with fluctuations.

*Trading Volume Analysis:*
<br>
A second line graph tracks trading volumes, highlighting notable spikes, particularly in AAPL and TSLA.</br>
<br>GOOG has stable trading volume patterns, while MSFT and NFLX show smaller fluctuations, suggesting less volatility in trading interest.</br>

### Anomaly Detection

*Detection Methodology:*
<br>
Z-scores are calculated for each stock’s adjusted close prices and volumes, with a threshold of |Z| > 2 to identify anomalies.
<br>This threshold flags significant deviations, which often correspond to impactful market events.

*Implementation Steps:*
<br>
For each stock’s adjusted close prices and volumes, the Z-scores are calculated to highlight outliers.
Anomalies are flagged and stored separately for adjusted close prices and trading volumes, making it easy to isolate price-based and volume-based anomalies for further analysis.

*Graphical Representation of Anomalies:*
<br>
Anomalies are visually highlighted on the graphs, with red markers for price anomalies and orange markers for volume anomalies, pinpointing unusual trading days.

### Analysis and Observations
<br>

*Price Anomalies:*

GOOG maintains an upward trend with periodic price anomalies that may relate to quarterly reports or market news.
NFLX displays the highest anomaly frequency and magnitude, suggesting market sensitivity and making it the most volatile stock in this analysis.

*Volume Anomalies:*

AAPL and TSLA have highly variable trading volumes with pronounced spikes, possibly reflecting significant investor interest or corporate announcements.
GOOG and MSFT have lower volatility in volume, indicating steadier trading interest.

### Correlation Analysis

*Objective*: Examine relationships between price and volume anomalies across the different stocks.

*Results:*
<br>
AAPL and GOOG price anomalies exhibit a weak positive correlation, indicating some market factors may affect both stocks similarly.
<br>
A negative correlation between AAPL and NFLX in price anomalies suggests that these stocks may react inversely to certain market events.
<br>
GOOG and MSFT have a positive correlation in volume anomalies, hinting at shared investor interest or responses to similar events.
<br>

### Risk Scoring and Interpretation
<br>
To quantify the overall anomaly risk, a Z-score-based risk rating is calculated. This rating reflects the average absolute Z-scores for both price and volume anomalies, allowing a comparative assessment of stock volatility.


*Methodology:*

Average absolute Z-scores for anomalies are calculated to measure the relative instability of each stock.
These scores are normalized across all stocks to create a comparative risk rating.


*Risk Ratings:*

**NFLX**: Highest risk (1.00), indicating frequent and significant anomalies, marking it as the most volatile stock.

**MSFT:** Moderate risk (0.53), with some anomaly activity suggesting intermittent volatility.

**TSLA:** Low risk (0.08), primarily showing volume anomalies rather than price-based instability.

**GOOG:** Minimal risk (0.00), indicating stable trading patterns with almost no significant anomalies.

**AAPL**: NaN risk rating, reflecting no detected anomalies within the analyzed period.

### Conclusion and Implications

This project demonstrates a systematic approach to identifying and evaluating anomalies in stock market data using statistical methods. By quantifying deviations and assessing risk ratings, this analysis provides actionable insights for understanding stock volatility and informing risk-sensitive trading strategies. Future enhancements could involve integrating additional data sources, such as news events or sentiment analysis, to enrich the interpretation of detected anomalies.