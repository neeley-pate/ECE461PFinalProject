# ECE461PFinalProject
This is the repository of our work on the ECE 461 P Final Project. Below is a description of the contents of each folder.

## Classifiers
This folder contains two scripts: one script with all models running on original data, and one script with all models running on the PCA data. The PCA csv is /pca/pca_data/AUS_WITH_WEATHER_2022_Categorical_X_train_pca.csv and the original csv is /pca/split_data/AUS_WITH_WEATHER_2022__categorical_train.csv. The models run were decision trees, logistic regression, MLP, XGBoost, and Catboost. These scripts include the data splits, training, and hyper paraemeters of each model. The scripts also include the ROC AUC curve graphs, PR curve graphs, confusion matrices, accuracy metrics, and notable feature graphs. The folder also contains two CSVs with the output labels of the models trained on the original data and the models trained on the PCA data compared to the true labels.

## Comparing Airlines Initially
This folder contains a python notebook that compares delays by airline. This was conducted along with the other data analysis before creating the models. This python notebook shows that Hawaiian Airlines has significant delays compared to any other airline, which could be caused by the overall distance the flights have to fly, or the fact that Hawaiian Airlines was new to the Austin Airport in 2022.

## Data Cleaning and Reduction
The dataCleaningAndReduction folder contains several Python notebooks. The notebooks in this folder performs various tasks, such as combining multiple CSV files, eliminating unwanted features, filtering flights that originate from AUS airport, and randomly sampling the data to reduce its size to 10K rows. Besides, the addWeatherToDataset.ipynb conbines hourly weather data with flight data to provide a better dataset for departure delay prediction.
Explanatory data analysis can be seen [here](https://colab.research.google.com/github/neeley-pate/ECE461PFinalProject/blob/main/dataCleaningAndReduction/exploratoryDataAnalysisAustin.ipynb) on Google Colab.

## Dataset
This folder contains multiple datasets in csv format, including sampled data of Austin airport, KAUS weather data and the combined flight data with weather.

## PCA
The PCA folder contains all the work that was done for PCA analysis, and some data transformation. The pca.ipynb has all of the code. First, I Loaded in the data (from dataset/sataWithWeather directory, there are 2 dataets in this directory on which I performed PCA analysis, one of which had categorical data which required preprocessing). There were some features (the weather features) that had non-numerical values, such as feature "preciptype" which has values like "ice", "rain", "snow", and "freezingrain", as well as feature "conditions" that has values like "Rain", "Snow", "Overcast", etc. For these features, there were some samples who had multiple values as a list. For example, a sample might have ["snow", "rain"] as a value ofr the "preciptype" feature. Thus, the first thing I did was transforming these categorical columns into numerical column by manual one-hot-encoding and then dropping one of the one-hot column. This preprocessed data is stored in "pca/categorical_data" as "AUS_WITH_WEATHER_2022_categorical.csv".

Then I noticed that there were features that one would not have access to before the delay actually occurs since they are calculated after the flight lands at destination, such as ARR_DELAY (which is the arrival delay at destination), CARRIER_DELAY (delay caused by maintenence, fueling, etc), ELAPSED_TIME, etc. Thus, I removed these features. After this processing, I was left with about 30 features. I saved this dataset to the "pca/dropped_data" folder, file names with "AUS_WITH_WEATHER_2022*.csv".

After this, I split the data into train and test data. I saved these datasets to a file so that they can be used later when training models. This file is in folder "pca/split_data", with file name of "AUS_WITH_WEATHER_2022*.csv"

Then I performed a pca.fit_transform on the training data and a pca.transform on the testing data. I saved the transforme data to files so that they can be use later when training models. This file is in folder "pca/pca_data" with file name of "AUS_WITH_WEATHER_2022*.csv"

I also graphed the explained variance for each of the principal components and we were able to capture about 90% of the variance with about 20-25 components. This graph is stored in "pca/explained_variance" as "AUC_WITH_WEATHER_2022*.png".


## Poster
This folder contains the poster but in a pdf to be printed as multiple pieces of paper.

## Regression
This folder contains two python notebooks that run the regression models: linear regression, lasso and ridge regressions, and MLPs. They are separated by the datasets they are run on: PCA and the original dataset, both containing numerical data. The notebooks separate the data into input and output (delay) variables using the included training and test splits. As part of the analysis, each notebook maps input correlation to the delay, visualizing the importance of each input variable. The notebooks then contain a grid search platform to test each of a large number of features on the datasets to obtain the best ones for each model.  For each model, the MSE and R-squared values are computed and used to judge its performance. To visual this, scatter plots for the predicted vs actual departure delays are displayed, as well as a plot of the residuals. 
