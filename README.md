# Project 3: Web APIs & NLP

## Problem Statement

Both fitness and nutrition are an important part of living a healthy lifestyle. Although the two can overlap in many ways, there are also many distinguishable features about them individually. The relationship between these two variables makes for a great opportunity to dive into both topics and gain a better understanding of fitness and nutrition individually and separately. The primary goal of this project is to identify whether words came from the fitness or nutrition subreddit and to base this off of the two model's f1 scores.   

## Data Dictionary

|**created_utc**| object | fitness.csv & nutrition.csv | Date the reddit post was created 

|**title**| object | fitness.csv & nutrition.csv | Title of the reddit post

|**subreddit**| object | fitness.csv & nutrition.csv | Category of the subreddit (Fitness or nutrition)

|**self_text**| object | fitness.csv & nutrition.csv | Text of the reddit post

|**title_text**| object | fitness.csv & nutrition.csv | Title and text of the reddit post combined


## Executive Summary

### Side Note

The reasoning for basing the success of the model from the f1 score is because the f1 score it takes a balance between the precision score and the recall score. For this project, the f1 score will showcase the true positives and the true negatives of the dataset.

### Scraping

For the scraping process, the reddit API, PRAW, was used to scrape reddit of 1000 posts of two subreddits: fitness and nutrition. The posts for these two subreddits were then put in their own dataframes and respective csv files, fitness.csv and nutrition.csv. These .csv files were sent to the models.py file to perform preprocessing steps and build models from them. 

### Preprocessing

The preprocessing for these .csv files were done in the function named preprocessing. This function takes in the dataframe name and the title_text column, which is the column that holds all the text of the subreddit. This function begins by reading through each line of the title_text column and performing a number of preprocessing techniques on it. This includes tokenizing, lemmatizing, changing everything to lowercase and removing unnecessary characters. When everything has been preprocessing, the function sends the cleaned text to a new dataframe, along with the name of the corresponding subreddit. 

#### CountVectorizer 

After all the data was preprocessed, it was sent to the CountVectorizer module that converts text into a count of how many times a word appears in the document. A train test split was run on the X (title_text) and y (subreddit) variables and the train and test data was transformed on the CountVectorizer. These transformed variables were used in the models to find various metrics to test how well our models predicted which subreddit the words would most likely end up in. 

## Models

### 1) Random Forest Classifier

Random Forest Classifier is used to gather together predicitions from multiple sets of training data and combine them to provide a high accuracy. For this project, after the CountVectorizer was performed on the data, a Random Forest Classifier was implemented on the combined dataframe. The importance of the top 15 features were printed out and compared.

### 2) Logistic Regression

Logistic Regression is used to distingush whether the data belongs to the positive class. In this model, to compare to the Random Forest Classifier, the Logistic Regression model was implemented on the combined dataframe to predict the probability of the data in the positive class.  

### Metrics

Various metrics were performed on both models to compare how well the model performed.

#### Baseline Score

The baseline score is used to find the most basic model possible and how it will perform for the data we have. We can compare the rest of our metrics to this baseline score to get an idea of how well our model performed.

Baseline score for fitness: 0.5044
Baseline score for nutrition: 0.4956

#### Precision

The precision score was found on the test data vs the predicted data for both fitness and nutrition. This score tells you of all the positives that were predicted in the dataset, how many are actually positive.

Precision score for fitness from Random Forest Classifier: 1.0
Precision score for nutrition from Random Forest Classifier: 0.9004

Precision score for fitness from Logistic Regression: 0.9917
Precision score for nutrition from Logistic Regression: 0.9333

#### Recall

The recall score was found on the test data vs the predicted data for both fitness and nutrition. This score tells you of all the positives in the dataset, how many did the model predict correctly?  

Recall score for fitness from Random Forest Classifier: 0.9016
Recall score for nutrition from Random Forest Classifier: 1.0

Recall score for fitness from Logistic Regression: 0.9370
Recall score for nutrition from Logistic Regression: 0.9912

#### f1 Score

The f1 score was found on the test data vs the predicted data for both fitness and nutrition. This score finds an overall score for your model and deals with taking a balance between your precision and recall score.

f1 score for fitness from Random Forest Classifier: 0.9482
f1 score for nutrition from Random Forest Classifier: 0.9476

f1 score for fitness from Logistic Regression: 0.9636
f1 score for nutrition from Logistic Regression: 0.9614

#### Confusion matrix 

A confusion matrix shows the values of the True Positives, False Negatives, False Positives, and True Negatives. Confusion matrices were created for both the Random Forest Classifier and the Logistic Regression models.

## Conclusions and Recommendations

In conclusion, based on the f1 scores, both models performed well on identifying which subreddit various words came from. For the fitness data, the baseline score was 0.5044. If we compare this to our Random Forest Classifier model and our Logistic Regression model, our f1 scores were 0.9482 and 0.9636 respectively. Similarly, for our nutrition data, the baseline score was 0.4956 whie our f1 scores were 0.9476 and 0.9614 for the Random Forest Classifier model and our Logistic Regression model. This shows that both our models performed well as they were able to classify words into the fitness and nutrition subreddits mostly accurately and that they were performing better than the baseline model. In this case, the Logistic Regression model performed better as it had slightly higher f1 scores, which tell us that it did a better job at predicting true positives than the Random Forest Classifier model did. I believe that since fitness and nutrition do have an overlap of terms, there was room for misclassification in both models. 

For next steps of the continuation and betterment of this project, more columns could be pulled from reddit posts (eg. comments) to add more data and complexity to the dataset. Additionally, another model (eg. GridSearch) could be implemented to add more variety and test more scores against each other to see if there is a better model at minimizing false positives.