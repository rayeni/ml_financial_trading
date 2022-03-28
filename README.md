# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Capstone Project: Machine Learning and Financial Trading

### Overview

The idea of machine learning (ML) has been present for well over [60 years](https://en.wikipedia.org/wiki/Machine_learning#:~:text=The%20term%20machine%20learning%20was,computer%20gaming%20and%20artificial%20intelligence.). However, it's only recently _(over the last decade)_ that it has garnered a lot of attention _(from self-driving cars, to fraud detection, to product recommendations on online shopping platforms)_. There is no doubt that ML has made considerable contributions in solving real-world problems.

Yet, in the area of trading and investing, there are mixed opinions about ML's usefulness.  Although institutions leverage [ML to gain an advantage in the markets](https://robusttechhouse.com/list-of-funds-or-trading-firms-using-artificial-intelligence-or-machine-learning/), many [retail traders](https://www.investopedia.com/articles/active-trading/030515/what-difference-between-institutional-traders-and-retail-traders.asp#:~:text=Retail%20traders%20typically%20invest%20in,of%20shares%20at%20a%20time.) _(individuals who trade their own money via discount brokers)_ have not experienced the same benefits, for a couple reasons--

1. Lack of knowledge _(some believe ML is difficult to understand, or that it simply offers no value)_

2. Lack of resources _(institutions have millions of dollars to invest network infrastructure and to hire hundreds of PhDs to help gain an advantage in the markets)_


### Problem Statement

#### Can machine learning enhance a retail trader's performance?


---

### Datasets

#### Data Used in Analysis

The following data set was used in the analysis:

* [`gld_data.csv`](./data/gld_data.csv): Gold ETF price data from 12-2011 to 12-2021 downloaded from [Yahoo Finance](https://finance.yahoo.com/) using the [`yfinance`]

#### Data Dictionary
|Feature|Type|Dataset|Description|Notes|
|---|---|---|---|---|
|**Date**|*datetime*|Gold ETF price data|Date of observation|None| 
|**Open**|*float64*|Gold ETF price data|GLD opening price of the day|Dropped after data cleansing|
|**High**|*float64*|Gold ETF price data|GLD highest price of the day|Dropped after data cleansing|
|**Low**|*float64*|Gold ETF price data|GLD lowest price of the day|Dropped after data cleansing|
|**Close**|*float64*|Gold ETF price data|GLD closing price of the day|None|
|**RSI**|*float64*|Gold ETF price data|[Momentum indicator](https://www.investopedia.com/terms/r/rsi.asp)|Calculated using [TA-Lib](https://mrjbq7.github.io/ta-lib/)|
|**pSAR**|*float64*|Gold ETF price data|[parabolic SAR](https://www.investopedia.com/ask/answers/06/parabolicsar.asp) short-term momentum indicator|Calculated using [TA-Lib](https://mrjbq7.github.io/ta-lib/)|
|**TEMA**|*float64*|Gold ETF price data|[Triple Exponential Moving Average](https://www.investopedia.com/terms/t/triple-exponential-moving-average.asp)|Calculated using [TA-Lib](https://mrjbq7.github.io/ta-lib/)|
|**ADX**|*int*|Gold ETF price data|[ADX](https://www.investopedia.com/articles/trading/07/adx-trend-indicator.asp)is used to quantify trend strength.|Calculated using [TA-Lib](https://mrjbq7.github.io/ta-lib/)|
|**Daily_Return**|*float64*|Gold ETF price data|GLD one day return percentage|None|
|**signal**|*int*|Gold ETF price data|Buy (or Exit) signal generated from mechanical (non-ML) system|Added during EDA phase|
|**Strategy_Returns**|*float64*|Gold ETF price data|The product of `signal` and `Daily_Return/Future_Return`|Added during EDA phase|
|**Future_Return**|*float64*|Gold ETF price data|GLD one day return percentage using Python `shift()` method|Added during modeling phase|
|**cumulative_strategy_returns**|*float64*|Gold ETF price data|Calculated by applying `cumprod()` method to `Strategy_Returns`|Added during EDA phase|
|**total_returns**|*float64*|Gold ETF price data|Sum of `cumulative_strategy_returns`|Added during EDA phase|

---

### Analysis Summary

Three machine learning models were tested:

- Logistic Regression
- Decision Tree Classifier
- Random Forest Classifier

Initial tests show that ML can enhance a retail trader's performance.

The three models displayed accuracy rates between 51% and 55%.

They improved strategy returns from 6% _(the return from the mechanical system)_ to 35%, 39%, and 42% respectively, representing and improvement of 458%, 527%, and 577%, respectively.

Initially, the models’ performance metrics were poor when three years of data was used.  After collecting 10 years of data, the metrics improved considerably.


---

### Recommendations 

In order to improve model metrics, the retail trader should do the following:

- use hyperparameter tuning for the aforementioned models to find the best parameters

- explore additional models such as neural networks and principal component analysis

To improve returns, the retail trader should consider doing the following:

- consider adding more features from the 100s of technical indicators available

- change the observation time frame from daily to lower time frames such as hourly, 30m, 15m, etc to find more buying opportunities

- Test, test, test.  This can’t be emphasized enough.  The retail trader must test extensively before going live (i.e., placing live trades).

---
