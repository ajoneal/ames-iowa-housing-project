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

The data given by the real estate company had several missing values in the .csv files that needed cleaning.  The first goal was to address all null values to ensure both test and training data were free of them.  