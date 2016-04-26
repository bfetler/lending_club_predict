## Ad Targeting Using Interest Rate Predictors

We may target different types of questions to loan applicants using variables that predict a high or low interest rate, as a potential predictor of high- or low-risk behavior.  We could also use the same predictors to target advertising to different customer segments.  A model dataset is available from [Lending Club](https://www.lendingclub.com/info/download-data.action), an online lending service.

#### Exploration

Data exploration is given in __lending_club_explore.py.__  The dataset contains 14 variables for 2500 loan applicants from 2013, including the interest rate approved *Interest.Rate*, which may be used as a target variable for supervised learning.  A binary class target *IR_TF* (interest rate true false) was created, using 0 if the rate was below 12% and 1 if it was above 12%.  After data cleaning, 2498 columns remained.  

A scatter matrix revealed some correlations between variables.  Histograms showed that some financial variables were not normally distributed, and were replaced by log variables.  

The data was randomly split into 75% training and 25% testing data using Pandas dataframe sample function.

#### Modeling and Prediction

Fitting the training data was done comparing several methods:
+ Support Vector Machines
+ Naive Bayes
+ Logistic Regression

The following was done for each method:
+ Initial fit and cross validation of training data.
+ If applicable, optimization of meta-parameters by grid score with cross validation.
+ An initial prediction on the test data.
+ Variable optimization on training data as follows: starting with two variable columns, randomly add columns, keeping those with improved score.  
+ Finally, prediction on test data using the optimized columns and parameters.

#### *svm_predict.py*
Prediction of low (< 12%) or high (> 12%) interest rate from eleven independent variables was performed using *Support Vector Machine Classification*  and ten-fold cross validation from *Scikit-learn*, scored using the accuracy of correct predictions.   SVM parameter scoring with a linear kernel showed insensitivity to C, and an optimum value of C=1 was chosen.  Initial variable sets gave an initial score estimate of 89% +- 3%.  Optimization using randomly chosen independent variables was insensitive to parameter choice, indicating the support vector results are largely independent of the data chosen.  Text output is given in **svm_predict_output.txt** and plots in **svm_predict_plots/**.  

#### *naive_bayes.py*
Prediction of low (< 12%) or high (> 12%) interest rate from as many as eleven independent variables was performed using *Gaussian Naive Bayes* modeling from *Scikit-learn*, with separate train and test data sets, and was scored using the number of incorrect predictions.  Trying different independent variables gave an optimum score with 11% of predicted points incorrect using seven variables.  Text output is given in **naive_bayes_output.txt** and plots in **naive_bayes_plots/**.  

#### *naive_bayes_kfold.py*
Prediction of low (< 12%) or high (> 12%) interest rate from eleven independent variables was performed using *Gaussian Naive Bayes* modeling and *k-fold* (4-fold) cross validation from *Scikit-learn*, scored using the number of incorrect predictions.  Initial variable sets gave a baseline estimate of score.  Optimization using randomly chosen independent variables gave the best score, with 11% of predicted points incorrect using only five variables.  Adding more variables increased the incorrect prediction rate.  Text output is given in **naive_bayes_kfold.txt** and plots in **naive_bayes_kfold_plots/**.  

#### *logistic_regression.py* 
A simple logistic regression of a loan data subset was used to predict the likelihood of a loan applicant to receive a high (> 12%) or low (< 12%) *Interest.Rate*, using a number of variables such as the *Amount.Requested* and *FICO.Average*.  The output may then be used to categorize loan applications.  Likelihood for a low rate was assessed to be good if the applicant had a 70% chance to get a loan of less than 12%.  For a $10,000 loan, a FICO score of 720 or greater was needed for a lower rate.  A lower FICO score correlated with a higher interest rate, and a higher loan amount also correlated with a higher interest rate.

Plots of logistic functions are in **logistic_plots/** and script output in **logistic_output.txt**.

