# Supplemental Files for Medium Post - Predict Stock Price with Time-Series Statistical Learning

This folder consists the supplemental files for my Medium Post of <a href="https://medium.com/predict-stock-price-with-time-series-statistical-learning-fec97560439e"><i>Predict Stock Price with Time-Series Statistical Learning</i></a>. In the post, we have made predictive models for Apple (AAPL) and Lockheed Martin (LMT). This folder consists of the code of predictive models train with the following algorithms:
<ul>
	<li>Adaptive model (Facebook Prophet)</li>
	<li>ARIMA model (pmdarima)</li>
	<li>Holts-winters method (Statsmodel)</li>
</ul>

## Goal
To build a prototype predictive model for 2 stocks in order to build a model to predict 505 stock prices in the S&P 500 index. The prototype shall have a high R-square with the testing data between 2019 and May 2020. 

## Data
The stock price is downloaded from Yahoo Finance and store in the relational database (Postgre) in local machine. You may find more detail on how the data is downloaded in the <a href="">ETL Pipeline folder</a> and the tables in the relational database in the <a href="">Database Table folder</a>.

## Files
There are 7 Python codes in this folder:
<ul>
	<li>Prediction_AAPL_arima.py</li>
	<li>Prediction_AAPL_fph.py</li>
	<li>Prediction_AAPL_hw.py</li>
	<li>Prediction_LMT_arima.py</li>
	<li>Prediction_LMT_fph.py</li>
	<li>Prediction_LMT_hw.py</li>
	<li>Graph.py</li>
</ul>
<br>
All the files started with "Prediction" are the codes for the predictive models trained with different algorithms. <i>Graph.py</i> is the helping code to generate line charts of the prediction of stock price.

## Adaptive Model
There are 2 files trained with this algorithm: [<i>Prediction_AAPL_fph.py</i>](Prediction_AAPL_fph.py) and [<i>Prediction_LMT_fph.py</i>](Prediction_LMT_fph.py), which are the predictive models for Apple and Lockheed Martin, respectively. Facebook Prophet is used for model training. 
<br><br>
Both files obtain 2 different time interval of stock price for model training:
<ul>
	<li>Between 1997 and 2018 (model_max)</li>
	<li>Between 2010 and 2018 (model_8yr)</li>
</ul>
<br><br>
The code first obtain data from the local database by querying with psycopg2. Then, change the column name to <i>ds</i> and <i>y</i> which is required by Facebook Prophet. After the model is trained, make a prediction and evaluate the accuracy with the testing data.
<br>
<br>
The R-square of model_max for Apple stock: Negative R-square<br>
The R-square of model_8yr for Apple stock: 45%
<br><br>
The R-square of model_max for Lockheed Martin: 42%<br>
The R-square of model_8yr for Lockheed Martin: 34%

## Graph.py
<i>Graph.py</i> has 1 function: generate_line_chart() which generate a line chart to visualize the stock price of training data, testing data, and the predictive stock price from either models. The function is designed to visualize training data, testing data and at least 1 predictive stock price data set, the 2nd predictive stock price data set is optional. The layout is fixed, except the chart title. The x-axis is fixed to be between 2016 and 2020. The file relies on the following packages:
<ul>
	<li>pandas</li>
	<li>datetime</li>
	<li>Plotly</li>
</ul>
