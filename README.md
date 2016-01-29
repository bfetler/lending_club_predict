# lending_club

**Regression Algorithm Tests** in Python using loan data from [Lending Club](https://www.lendingclub.com/info/download-data.action), an online lending service.

#### *prob_lending_club.py* 
Boxplot, Histogram, QQplot of *Amount.Funded* and *Amount.Requested* from loan data subset.  Plots are in **univariate/**.
#### *chi_squared.py* 
Chi-squared plot of *Open.Credit.Lines* from loan data subset.  Plots are in **chisq_plots/**.
#### *linear_regression.py* 
A scatter matrix plot of a loan data subset, both continuous and ordinal variables, shows correlation between *FICO.Average* and *Interest.Rate*, and some correlation with *Amount.Requested*.  Ordinary Least Squares (OLS) Regression of these variables was performed.  The fit shows good p-values but the condition number is high, probably due to the large amount of scatter in the data.  Undoubtably, other variables are correlated with each other as well.  

Plots of the scatter matrix and histograms are in **linear_plots/** and script output is in **linear_output.txt**.
#### *logistic_regression.py* 
A simple logistic regression for a loan data subset was used to predict the likelihood of a loan applicant to receive a high (>= 12%) or low (< 12%) *Interest.Rate*, based upon the *Amount.Requested* and *FICO.Average*.  Likelihood for a low rate was judged to be good if the applicant had a 70% chance to get a loan of less than 12%.  For a $10,000 loan, a FICO score of 720 or greater was needed for a lower rate.  A lower FICO score correlated with a higher interest rate, and a higher loan amount also correlated with a higher interest rate.

Plots of logistic functions are in **logistic_plots/** and script output in **logistic_output.txt**.
#### *multivariate.py* 
Multivariate Regression of *int_rate* (interest rate) using *log_income* (log annual income) and *home_ownership*.  Data is from the full lending club loan data set for years 2013 and 2014.  Multivariate plots are in **multivar_plots/**.  Fit output is at the end of the script **multivariate.py**.
#### *time_series.py*
Time series ARIMA analysis (autoregression integrated moving average) was done of monthly loan count for 2013 and 2014, which shows an almost linear increase over time.  *ARIMA(1, 1, 0)* seems to best model the data without overfitting.  Plots are in **time_series_plots/** and script output is written to **time_series_output.txt**.
