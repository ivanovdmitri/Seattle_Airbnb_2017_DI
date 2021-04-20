# Machine learning-inspired recommendations for Airbnb hosts in Seattle, WA

# Important questions:
* What property, policy, and pricing choices maximize the revenue for the Airbnb hosts in Seattle, WA?
* What are the projected revenue and the booking rate for the hosts with some specific property attributes, pricing, and policies?

### Available data: Seattle Airbnb open data (01/04/2016 - 01/02/2017)
* *A sneak peek into the Airbnb activity in Seattle, WA, USA*
* Taken from [https://www.kaggle.com/airbnb/seattle](https://www.kaggle.com/airbnb/seattle)

### [Python (Jupyter notebook) code](https://github.com/ivanovdmitri/Seattle_Airbnb_2017_DI/blob/master/Seattle_Airbnb_2017_DI.ipynb)
### [Summary report slides](https://github.com/ivanovdmitri/Seattle_Airbnb_2017_DI/raw/master/Seattle_Airbnb_2017_DI.pptx)
    
### Machine learning solution outline
1. Data cleaning
    * Examine and clean the property listing and booking data
    * Check and make sure the entries with inf and NaN values are either filtered out or replaced with reasonable default values
2. Feature engineering
    * Determine how features correlate with the revenue and the booking rate
    * Examine the features' cross-correlation matrices, add and/or remove the features to produce a set of features that correlate with the revenue and the booking rate but don't have too strong cross-correlations with each other
3. Build a model
    * Use the popular [xgboost.XGBRegressor](https://xgboost.readthedocs.io/en/latest/python/python_api.html) supervised machine learning model
    * Fit for the revenue and the booking rate using [k-fold cross-validation](#https://scikit-learn.org/stable/modules/cross_validation.html) method with a split level of 5
    * Tune the hyper parameters by iterative hand scanning and by utilizing [sklearn.model_selection.GridSearchCV](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.GridSearchCV.html) tool
    * Assess the accuracy of the models by examining the root mean square error, R2, explained variance fraction, and mean absolute error of the <em>validation data</em> splits. Also plot the residuals of the fits to assess any possible biases of the models
4. Use the model
    * Determine the relative importance of the features in predicting the revenue and the booking rate
    * Deploy a function that implements the models using either [pandas.DataFrame](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.html) or Python dictionary as inputs and returns the model predictions for the expected revenue and the booking rate.
5. Add auxiliary functions that allow querying the listing database to determine typical values for the features under specific conditions. 
