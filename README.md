#Forecasting by FB Prophet in Colab

There are many forecasting tools available in the market, even Excel worksheet also provides a simple forecasting function, which I have shown how to use it (Yiu, 2019). Other more sophisticated software can provide ARIMA and HP Filter methods for forecasting, but they can be costly.

I learned that FB Prophet provides an open source code and free forecasting tool in R or Python. It allows more detailed parameter settings for making forecasts including three additive components: trend, seasonality and holidays. For more details, one may refer Lyla (2019).

## Requirement
**Python**: 
          NumPy, 
          Pandas, 
          Seaborn, 
          Matplotlib
          FB Prophet

install FB Prophet  in colab-
!pip install fbprophet

install FB Prophet  in Vs code -
%pip install fbprophet

###The Prophet Forecasting Model

We use a decomposable time series model with three main model components: trend, seasonality, and holidays. They are combined in the following equation:

                                         y(t) = g(t)+s(t)+h(t)+εt

g(t): piecewise linear or logistic growth curve for modelling non-periodic changes in time series
s(t): periodic changes (e.g. weekly/yearly seasonality)
h(t): effects of holidays (user provided) with irregular schedules
εt: error term accounts for any unusual changes not accommodated by the model

Using time as a regressor, Prophet is trying to fit several linear and non linear functions of time as components. Modeling seasonality as an additive component is the same approach taken by exponential smoothing in Holt-Winters technique . We are, in effect, framing the forecasting problem as a curve-fitting exercise rather than looking explicitly at the time based dependence of each observation within a time series.

Prophet requires the variable names in the time series to be:

                     y – Target
                    ds – Datetime
 
 #Steps-
 
 -1.Importing datasets
  
  -2.Read train and test
  
  -3.Convert to datetime format
  
  -4.convert to time series from dataframe
  
  -5.Fitting the prophet model
  
      m = Prophet
      m.fit
      
  -6.prediction
  future = m.make_future_dataframe(periods=213)
  forecast = m.predict(future)

  
    
EVvaluation metric 

RMSE:-Root mean squared error is an absolute error measure that squares the deviations to keep the positive and negative deviations from canceling one another out. This measure also tends to exaggerate large errors, which can help when comparing methods. is the fitted forecast value for the time period t.

rmse = sqrt(mean_squared_error)
mean_squared_error = mean(forecast_error^2)
forecast_error = expected_value - predicted_value



conclusion

Prophet certainly is a good choice for producing quick accurate forecasts. It has intuitive parameters that can be tweaked by someone who has good domain knowledge but lacks technical skills in forecasting models. Readers can also try and fit Prophet directly over the hourly data and discuss in the comments if they are able to get a better resul


