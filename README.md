# Project 3 - Web APIs and Predicting Subreddit
Tenzin Wangdu | 3.19.2021

### Problem Statement
---
A resort wants to find out which subreddit the posts is coming from and how can we use a predictive model to see which subreddit a post came from?

### Table of Contents
---
- [Data Collection](#Data_Collection)
- [Data_Dictionary](#Data_Dictionary)
- [Data_Cleaning](#Data_Cleaning)
- [Exploratory Data Analysis](#Exploratory_Data_Analysis)
- [Preprocessing](#Preprocessing)
- [Data Visulization](#Data_Visualization)
- [Modeling](#Modeling)
- [Conclusions and Recommendations](#Conclusion_and_Recommendations)
- [Sources](#Sources)

### Data_Collection
---
Data is collect from Reddit API. I scrape it from pushshift's API 'https://api.pushshift.io/reddit/search/submission'. Then you use request library to get the data and then turn into a dictionary using json. Extract 1000 posts from r/ski subreddit and 400 posts from r/snowboard subreddit.

### Data_Dictionary
---
|Feature|Type|Dataset|Description|
|---|---|---|---|
|**subreddit**|**int**|df|0: Snowboard subreddit and 1: Ski subreddit|
|**title**|*object*|df|The title of the post.|
|**selftext**|*object*|df|text of the post|
|**final_text**|*object*|df|combination of title and selftext|

### Data_Cleaning
---
Filling all the null values with '' because all the null values are in the selftext column. Use .drop_duplicates to drop any duplicate post that came from the subreddit.

### Exploratory_Data_Analysis
---
Filter the data into columns of subreddit and selftext and title. Then combine both selftext and title for the target variable to predict. Convert ski and snowboard subreddit column into a binary column

### Preprocessing
---
RegExp Tokenizer: (‘[a-z]\w+’):  it return only the lowercase letter without any punctuation or special letter.
Lemmatize: To normalize the text without any derived words.

### Modeling
---
Logistic Regression with CountVectorizer 
* Remove common english by setting a stopword
* Built pipeline and GridSearch
* It was easier to interpret using Coef_
* Training score: 92, Testing score: 88, Baseline score: 71

Random Forest with Tfidif
* Decision Tree
* Stop_words, ngram_range
* Built pipeline and GridSearch
* Training score: 98, Testing score: 88, Baseline score: 71

### Data_Visualization
---
World Cloud of Most Common word in Both Subreddit

<img
     src = "https://github.com/tw1270/Web-APIs-and-Predicting-Subreddit/blob/main/images/wordcloud.jpg" style = '' style="float: left; margin: 20px; height: 55px">

Confusion Matrix of Logistic Regression

<img
     src = "https://github.com/tw1270/Web-APIs-and-Predicting-Subreddit/blob/main/images/confusion_matrix.png" style = '' style="float: left; margin: 20px; height: 55px">

Top Predictor of r/snowboard

<img
     src = "https://github.com/tw1270/Web-APIs-and-Predicting-Subreddit/blob/main/images/r_snowboard_predictor.png" style = '' style="float: left; margin: 20px; height: 55px">
     
Top Predictor of r/ski

<img
     src = "https://github.com/tw1270/Web-APIs-and-Predicting-Subreddit/blob/main/images/r_ski_predictor.png" style = '' style="float: left; margin: 20px; height: 55px">
     
### Conclusion_and_Recommendations
---
* Both model were successful, they both beat the baseline by more than 20% 
* Logistic Regression was the better model and its coefficient makes the data more understandable
* The Next Steps would be gather new data and implement into my model to see the score


### Sources
---
https://api.pushshift.io/reddit/search/submission
