# Feaure Selection Collection
In industry, many times we need to generate features, understanding them and generate more to improve model performance. I'm taking notes of some method that may help do further exploration.

## SHAP
* It's amethod used to deal with the draw back of XGBoost feature selection
* [You know what, SHAP value came from game theory][2]
  * "Shapley values correspond to the contribution of each feature towards pushing the prediction away from the expected value."
* [My practice code 1 - XGBoost Regressor][1]
* Github has blocked the loading of JS, in fact it provides a method to interact with each record and understand how the feature values affect the prediction
![shap JS](https://github.com/hanhanwu/Hanhan_Data_Science_Practice/blob/master/Better4Industry/Feature_Selection_Collection/xgboost_shap.PNG)


[1]:https://github.com/hanhanwu/Hanhan_Data_Science_Practice/blob/master/Better4Industry/Feature_Selection_Collection/try_shap_xgboost.ipynb
[2]:https://www.analyticsvidhya.com/blog/2019/11/shapley-value-machine-learning-interpretability-game-theory/?utm_source=feedburner&utm_medium=email&utm_campaign=Feed%3A+AnalyticsVidhya+%28Analytics+Vidhya%29
