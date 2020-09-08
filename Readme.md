# AnalyticsVidhya.com Janatahack Demand Forecasting Hackathon
by Wayne Chan and Kavan Pandya

## Introduction

AnalyticsVidhya.com hosted a hackathon for forecasting the product sales for different stores.

Problem Statement: One of the largest retail chains in the world wants to use their vast data source to build an efficient forecasting model to predict the sales for each SKU in its portfolio at its 76 different stores using historical sales data for the past 3 years on a week-on-week basis. Sales and promotional information is also available for each week - product and store wise.

However, no other information regarding stores and products are available. Can you still forecast accurately the sales values for every such product/SKU-store combination for the next 12 weeks accurately? If yes, then dive right in!

We approached this problem using common Scikit-Learn classifiers and then comparing the best performing ones with a neural network.

Ultimately, our best performing solution was a Random Forest model which had an R2 score of 0.72 and RMLSE score of 42.

### Methodology

Our approach was to clean the data by first removing nulls and outliers.  We then converted the time data (such as date, time, month, and year) into a python time readable datetime format. The product sku_id and store_id were then combined to create a combined feature for our modelling.

We established a baseline result using selected regressors from the Scikit-Learn library and performed a base parameter grid search to determine which regressor method worked best. After choosing the top performers from this group, we further tuned them to get improved results. We then created a basic neural network and compared it against the best performing classifier from the grid search and made predictions to submit.

We further created engineered featured such as price_diff by taking the difference of total price and base price and also created polynomial features. 

---

### Data Dictionary

|Feature|Type|Description|
|---|---|---|
|record_id|int64|Unique identifier for each week store sku combination|
|week|object|Starting date of the week|
|store_id|int64|Unique ID for each store|
|sku_id|int64|Unique id for each product|
|total_price|float64|Sales price for the product|
|base_price|float64|Base price of the product|
|is_featured_sku|int64|Was part of the featured item for the week|
|is_display_sku|int64|Product was on display at a prominent place at the store|
|units_sold|int64|(Target)Total units sold for the week-store-sku combination|

#### Provided Data

Provided datasets from Kaggle:

- [Training dataset](./train.csv)
- [Test dataset](./test.csv)

---

### Conclusion

The Random Forest model was the best solution based on our results and achieved a R2 score of 0.72 and RMLSE of 42 on the test dataset. While we did attempt a neural network solution as well it was overfit and the predictions failed to outperform the Random Forest model. 

### Future Improvements

Areas of improvement in the future include better feature engineering to create new relations between the features and additional hyperparameter tuning on the Scikit-Learn classifiers and also additional tuning for the neural network.
