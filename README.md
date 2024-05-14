# DL-final-project

DL Final Project Sentiment Analysis for Stock Trend Prediction. The fine-tuned FinBERT model predicts if the stock will go up or down based on the sentiment of the statement. 

All the prepared datasets are avaialble datasets folder but the GME 6 Months Sentiment Dataset will be visible after running the `preprocess_data.ipynb` notebook. The models are not uploaded because the file was too large to upload on GitHub.

## Datasets:
1. GME 6 Months Reddit Sentiment Data: https://www.kaggle.com/datasets/pavellexyr/six-months-of-gme-on-reddit
2. GME stock data(Ground Truth) downloaded directly from Yahoo. The dataset is avaialable in the `datasets` folder.

## The order in which files need to be run to get the predictions:

1. Start with the `preprocess_data.ipynb` notebook. This will download the GME Reddit 6 months dataset from Kaggle and preprocess the data to be used for further preprocessing and merging. This file creates the data reuired to fine_tune the sentiment analysis model. There are a lot of visualizations available to understand the data.
2. Next we work on the GME Stock Data to add more features necessary for the prediction. The file `preprocess_gme_dataset.ipynb` will clean the data and merge with the reddit sentiment dataset after making a left join over date. The percentage_change and the expected prediction is also calculated. This will be the ground truth data which will be used for RandomForestClassifier and the SVM classifier for the final trend prediction.
3. Next we run the `finbert_fine_tuning_for_50k_datapoints.ipynb` model to fine-tune the FinBERT model for GME sentiment data. The FinBERT sentiment analysis model has an accuracy of 0.867 when trained on 50k datapoints.
4. Now we run the `random_forest _with_personal_pred.ipynb` file to predict using the loaded FinBERT model and fit the data on RandomForestClassifier and the SVM classifer models. The model has a test accuracy of 0.5902.
