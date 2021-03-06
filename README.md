# predicting-future-sales
Here I have worked with a challenging time-series dataset consisting of daily sales data to predict total sales for every product and store in the next month. 

This data was provided by one of the largest Russian software firms - 1C Company.

# **Data Description**

## **Files**
* sales_train.csv - the training set. Daily historical data from January 2013 to October 2015.
* test.csv - the test set. You need to forecast the sales for these shops and products for November 2015.
* sample_submission.csv - a sample submission file in the correct format.
* items.csv - supplemental information about the items/products.
* item_categories.csv - supplemental information about the items categories.
* shops.csv- supplemental information about the shops.

## **Data fields**
* ID - an Id that represents a (Shop, Item) tuple within the test set
* shop_id - unique identifier of a shop
* item_id - unique identifier of a product
* item_category_id - unique identifier of item category
* item_cnt_day - number of products sold. You are predicting a monthly amount of this measure
* item_price - current price of an item
* date - date in format dd/mm/yyyy
* date_block_num - a consecutive month number, used for convenience. January 2013 is 0, February 2013 is 1,..., October 2015 is 33
* item_name - name of item
* shop_name - name of shop
* item_category_name - name of item category

**Process Overview**
* The libraries used are numpy, pandas and sklearn. 
* The given data is already clean and has no missing values.
* Not all items in train set are in the test set and vice versa.
* Dropped the unnecessary fields like item price and date_block_num from the training dataset given.
* Converted the dates into the convenient format and converted the dates to months since the prediction is required for a month. 
* Then formatted the data to get the sum of items sold for each combination of shop_id and item_id, for each of the months.
* Then merged the test dataset given and the above train dataset on shop_id and item_id.
* In the model development, I dropped the first month's data from the train dataset to ensure that the train and the test datasets have the same number of columns.
* Then split the datasets accordingly for model fitting.
* I have used linear regression and random forest regressor here.
* On comparing the mean squared errors of the train and test data, and the test scores, the random forest regressor was definitely the better choice.
* Hence, I have generated a prediction using the RFR.
* The final submission file can be found in this repository, in which ID stands for a combination of the item_id and the shop_id, and item_cnt_month is the prediction generated which is the number of items sold monthly for that particular ID. 


