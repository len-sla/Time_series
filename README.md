## Project Purpose
Getting familiar with time series data approach and models

### General info
[Time Series](https://en.wikipedia.org/wiki/Time_series) is a collection of data points indexed based on the time they were collected. Most
often, the data is recorded at regular time intervals. What makes Time Series data special?
Forecasting future Time Series values is a quite common problem in practice. Predicting the weather
for the next week, the price of Bitcoins tomorrow, the number of your sales during Chrismas and
future heart failure are common examples.
Time Series data introduces a “hard dependency” on previous time steps, so the assumption that
independence of observations doesn’t hold. What are some of the properties that a Time Series can
have?
Stationarity, seasonality, and autocorrelation are some of the properties of the Time Series.

 ###  [time_series_retail.ipynb ](time_series_retail.ipynb)
As an input 2 years  sells data  from one of the online shops were taken and then resampled to 10 day period.
Other time domains are also tried. piece of data looks like below:
![train df ](train-sample.PNG)

---
At first try data was taken as is without cleaing ouliers and other bad surprises.
to process simple Keras model with LSTM was used
with a structure as below
```
model = keras.Sequential()
model.add(
  keras.layers.Bidirectional(
    keras.layers.LSTM(
      units=128, 
      input_shape=(X_train.shape[1], X_train.shape[2])
    )
  )
)
model.add(keras.layers.Dropout(rate=0.2))
model.add(keras.layers.Dense(units=1))
model.compile(loss='mean_squared_error', optimizer='adam')

```
Results were not particularly impressive:
---

![before cleaning ](time-series.PNG)




 
structure of df before cleanup:
---
![before cleaning ](train-before.PNG)

After cleanup  cleanup:

![aftercleaning ](train-after.PNG)

### and results...
![aftercleaning ](time-series-after-cleaning-df.PNG)

![after cleaning ](time-series-after-cleaning-df1.PNG)



_Created by:_ [@len-sla]

