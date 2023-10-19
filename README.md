# Project 3: Web APIs & NLP

## Problem Statement

Both fitness and nutrition are an important part of living a healthy lifestyle. Although the two can overlap in many ways, there are also many distinguishable features about them individually. The primary goal of this project is to identify whether words came from the fitness or nutrition subreddit and to base this off of the two model's highest accuracy.   
## Data Dictionary

|**created_utc**| object | fitness.csv & nutrition.csv | Date the reddit post was created 

|**title**| object | fitness.csv & nutrition.csv | Title of the reddit post

|**subreddit**| object | fitness.csv & nutrition.csv | Category of the subreddit (Fitness or nutrition)

|**self_text**| object | fitness.csv & nutrition.csv | Text of the reddit post

|**title_text**| object | fitness.csv & nutrition.csv | Title and text of the reddit post combined


## Executive Summary

### Scraping

For the scraping process, the reddit API, PRAW, was used to scrape reddit of 1000 posts of two subreddits: fitness and nutrition. The posts for these two subreddits were then put in their own dataframes and respective csv files, fitness.csv and nutrition.csv. These .csv files were sent to the models.py file to perform preprocessing steps and build models from them. 

### Preprocessing

The preprocessing for these .csv files were done in the function named preprocessing. This function takes in the dataframe name and the title_text column, which is the column that holds all the text of the subreddit. This function begins by reading through each line of the title_text column and performing a number of preprocessing techniques on it. This includes tokenizing, lemmatizing, changing everything to lowercase and removing unnecessary characters. When everything has been preprocessing, the function sends the cleaned text to a new dataframe, along with the name of the corresponding subreddit. 

#### CountVectorizer 

After all the data was preprocessed, it was sent to the CountVectorizer module that converts text into a count of how many times a word appears in the document. A train test split was run on the X (title_text) and y (subreddit) variables and the train and test data was transformed on the CountVectorizer. These transformed variables were used in the models to find various metrics to test how well our models predicted which subreddit the words would most likely end up in. 

## Models

### 1) Random Forest Classifier
 

### 2) Logistic Regression

#### Metrics

## Conclusions and Recommendations