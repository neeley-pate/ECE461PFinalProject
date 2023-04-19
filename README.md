# ECE461PFinalProject
This is the repository of our work on the ECE 461 P Final Project. Below is a description of the contents of each folder.

## Classifiers
This folder contains two scripts: one script with all models running on original data, and one script with all models running on the PCA data. The models run were decision trees, logistic regression, MLP, XGBoost, and Catboost. These scripts include the data splits, training, and hyper paraemeters of each model. The scripts also include the ROC AUC curve graphs, PR curve graphs, confusion matrices, accuracy metrics, and notable feature graphs. The folder also contains two CSVs with the output labels of the models trained on the original data and the models trained on the PCA data compared to the true labels.

## Comparing Airlines Initially

## Data Cleaning and Reduction
The Data Cleaning and Reduction folder contains several Python notebooks that are used to perform data cleaning and reduction tasks on datasets of flight records. The notebooks in this folder performs various tasks, such as combining multiple CSV files, eliminating unwanted features, filtering flights that originate from AUS airport, and randomly sampling the data to reduce its size. Besides, the addWeatherToDataset.ipynb conbines hourly weather data with flight data to provide a better dataset for departure delay prediction.

## Dataset
This folder contains multiple datasets in csv format, including sampled data of Austin airport, KAUS weather data and the combined flight data with weather.

## PCA

The PCA folder contains all the work that was done for PCA analysis, and some data transformation. The pca.ipynb has all of the code. First, I Loaded in the data. Then there were some features (the weather features) thad has non-numerical values, such as feature "preciptype" which has values like "ice", "rain", "snow", and "freezingrain", as well as feature "conditions" that has values like "Rain", "Snow", "Overcast", etc. For these features, there were some samples who had multiple values as a list. For example, a sample might have ["snow", "rain"] as a value ofr the "preciptype" feature. Thus, the first thing I did was transforming these categorical columns into numerical column by manual one-hot-encoding and then dropping one of the one-hot column.

Then I noticed that there were features that one would not have access to before the delay actually occurs since they are calculated after the flight lands at destination, such as ARR_DELAY (which is the arrival delay at destination), CARRIER_DELAY (delay caused by maintenence, fueling, etc), ELAPSED_TIME, etc. Thus, I removed these features. After this processing, I was left with about 30 features. I saved this dataset to the "dropped_data" folder, file names with "AUS_WITH_WEATHER_2022*.csv".

After this, I split the data into train and test data. I saved these datasets to a file so that they can be used later when training models. This file is in folder "split_data", with file name of "AUS_WITH_WEATHER_2022*.csv"

Then I performed a pca.fit_transform on the training data and a pca.transform on the testing data. I saved the transforme data to files so that they can be use later when training models. This file is in folder "pca_data" with file name of "AUS_WITH_WEATHER_2022*.csv"

I also did graphed the explained variance for each of the principal components and we were able to capture about 90% of the variance with about 20-25 components.



## Poster
This folder contains the poster but in a pdf to be printed as multiple pieces of paper.

## Regression
This folder contains the regression models. They are separated by the datasets they are run on: PCA and the original dataset.
