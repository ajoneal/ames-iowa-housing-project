# Predicting the price of a house in Ames, Iowa


## Project Description/Problem

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

The data given by the real estate company had several missing values in the .csv files that needed cleaning.  The first goal was to address all null values to ensure both test and training data were free of them.  Columns missing around 50% of the data in the column were removed.  Several of the columns on quality and condition had "NA" values that were turned to null values, so they were returned to "NA" then the quality and condition columns were converted to ordinal values in order to be able to use them in the models created.  There were a few other tweaks to clean the data and only one null value left behind in the test data set and that column was not used in any model features.  After that, I completed a little bit of EDA and created a few models before realizing a few of my cross-validation scores were extremely negative.  I went back and searched for heavy outliers that may have been skewing the data.  After removal of some of these outliers, the cross-validation scores were more in line with the testing and training scores.

After the cleaning was complete, I created dummy columns for some categorical features and gave values to ordinal columns so that I would be able to use them in my models.  I created a heatmap and pairplots with the training data to check which features were highly correlated with 'saleprice' to decide which columns to use as a baseline model and decided that anything with a .5 correlation or higher would go into that first linear regression model.  I used all the previously created variables for the first 3 models that I created, then created some interaction features with the quality and condition features then using those features for a linear regression model and lasso model on the 4th and 5th models.

---
## Modeling, Analysis, and Recommendations

I created 5 different models to help predict sale price.  My 1st baseline linear regression model consisted of features that were highly correlated with the sale price.  The model scored fairly well, and the distribution of residuals suggested there was some room for improvement.  For the 2nd model I threw all the numeric data available at the same model to give it more information.  The model scored 3% higher in its cross-validation score and saw some improvement in residuals, but I believed I could make it better.  For the 3rd model, I scaled the data however it did not change much on the performance and the U-shaped pattern is residuals vs predictions still existed as well as a larger spread as the price increased.  I then created some feature interactions between the different quality and condition variables in hopes increasing performance of the model.  The 4th model I created with feature interactions scored the best out of all the models I created and addressed the issues with the residuals.  I then created a lasso model with the same data, however it scored slightly lower than the previous model I had created.  It did show me which features I could rid possibly rid my model of to create a simpler model going forward.

Of the 5 models I created, I would recommend the 4th model for the real estate agency to use to help them get a better understanding of the price of a house at sale.  This will allow them to provide better insight into potential buyers and sellers that they work with.  I would also recommend creating another model based on the results of the lasso model, dropping the features with low coefficients and checking to see if it improves the current model.  Finally, I would recommend the agency get more data on higher priced houses to better understand that aspect of the housing market.

---
## Presentation link

https://docs.google.com/presentation/d/137j8hflPYz7kjep576jN_ZRbyOTtAEPr4RO_gtlyowY/edit?usp=sharing





