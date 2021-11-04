# Housing Market in Ames, Iowa


## Project Description

I was recently hired by a real estate agency in Ames, Iowa and asked to help them get a better understanding of the housing market. In order to do so, they asked me to come up with a model that will help them best predict the price of a house at sale based on the current housing data provided to me by the real estate company.

---
## Data

* [`train.csv`](./datasets/train.csv): Housing Data to train the model on
* [`test.csv`](./datasets/test.csv): Housing Data to create predictions and test the model
* [`clean_train.csv`](./datasets/clean_train.csv): Training Housing Data after removing null values and adjusting outliers
* [`clean_test.csv`](./datasets/clean_test.csv): Testing Housing Data after removing null values and adjusting outliers
* [`clean_train_with_features.csv`](./datasets/clean_train_with_features.csv): Cleaned Training Housing Data after creating feature interactions
* [`clean_test_with_features.csv`](./datasets/clean_test_with_features.csv): Cleaned Testing Housing Data after creating feature interactions


Review the [data description](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt) for more information on the features of the datasets.  The column names after cleaning have been adjusted to snake-casing.

---
## Cleaning, Pre-processing, and EDA

The data given by the real estate company had several missing values in the .csv files that needed cleaning.  The first goal was to address all null values to ensure both test and training data were free of them.  Columns missing around 50% of the data in the column were removed.  Several of the columns on quality and condition had "NA" values that were turned to null values so they were returned to "NA" then the quality and condition columns were converted to ordinal values in order to be able to use them in the models created.  There were a few other tweaks to clean the data and only one null value left behind in the test data set and that column was not used in any model features.  After that, I completed a little bit of EDA and created a few models before realizing a few of my cross-val scores were extremely negative.  I went back and searched for heavy outliers that may have been skewing the data.  After removal of some of these outliers, the cross-val scores were more in line with the testing and training scores.

After the cleaning was complete, I created dummy columns for some categorical features and gave values to ordinal columns so that I would be able to use them in my models.  I created a heatmap and some pairplots with the training data to check which features were highly correlated with saleprice to decide which columns to use as a baseline model and decided that anything with a .5 correlation or higher would go into that first linear regression model.  I used all of the previously created variables for the first 3 models that I created, then created some interaction features with the quality and condition features then using those features for a linear regression model and lass model on the 4th and 5th models.

---
## Modeling and Analysis