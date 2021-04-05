# NLP classification
<hr>
This project uses NPL to create a binary classification model implemented on subreddits for a targeted marketing campaign. 
<br><br>

**Theoretical project:** 
StarWars Corporate would like to have an overwhelming turnout of fans for Comic-Con 2021. To achieve this, StarWars is sending loyalty rewards to their fans on the Reddit platform, offering a secret $15 discount off ComicCon 2021 entry fee. The promotion is only for participants on the StarWars subreddit; therefore, corporate want to make sure that only StarWars fans receive these promotions.

## Problem Statment 

To create a model that can classify between two similar subreddit, specifically to classify posts belonging to Starwars and StarTek subreddit posts correctly. 

Our primary metric was Accuracy and Precision to identify which subreddit is StarWars (TP).

## Executive Summary 

We used the PushShift API to scrape 9,000 Startrek and 23,700 StarWars subreddit to train this model.  After we did exploratory data analysis, we realized that because many Star Wars subreddits were incomplete from being 'deleted' or 'removed,' we had to scrape more Star Wars posts substantially to have balanced classes.

We ran basic models with Naive Bayes, Logistic Regression, Random Forest, and Adaboost Classifier, each paired with TfidfVectorizer and CountVectorizer.

We created custom stop words, used lemmatization, and used the hyperparameters within CountVectorizer to improve our accuracy and precision score. 

The best-tuned model was Naive Bayes with count vectorizer, with an accuracy score of .9771 and a precision score of .9906.

## Contents

- 00-reddit_digger.ipynb
- 01-Data_clean-proj_3.ipynb
- 02-basic_modeling-proj_3.ipynb
- 03-nbayesGS_proj_3.ipynb



### NoteBook 00 - Webscrapping 

We utilized PushShift API to scrape data from both StarWars and StarTrek subreddits.  Each scrape took 2500 posts of a single subreddit and saved it as a CSV file.  We collected additional data to equal out ~ 6,000 posts per class.   

### NoteBook 01 - Data Cleaning and Exploratory Data Analysis

During the cleaning of the data, we noticed that many of the Reddit posts had many NaN values within their 'selfText tag.' StarWars Reddit had a proportionate number of NaN compared to StarWars.


We also found several 'selftexts' where '[deleted]' or '[removed],' leaving their 'selftext' unusable. We deleted all instances of both '[deleted]' or '[removed]' to ensure our data was the most complete.

By the time we ran our final models, we had collected 23,700, StarWars subReddits and 9,000 Startrek subreddits. Of this original data 5,712 Starwars subReddits and 6,000 Startrek subReddits were used to run our models.

### NoteBook 02 - Basic Modeling 

Using the accuracy and precision metric, we trained/tested a base model of Naive Bayes, Logistic Regression, Random Forest, and Adaboost classifier models, each paired with TfidfVectorizer and CountVectorizer.

Using this Rubric, we found that Naive Bayes with Count Vectorizer yields the highest performance.

##### Baseline Score:

At random, a 51% chance that a sample from our data will be a Starwars class.

### NoteBook 02 - Naive Bayes Modeling 

     Naive Bayes:
    The Naive Bayes is a probabilistic algorithm. The features within this model are the words and their frequency. Bayes calculates each word's probability using its frequency, and Naive Bayes assumes every word is independent of the others. 

    Naive Bayes's strengths are that it is easy to implement, it has a short training time, and it assumes that all attributes(features) are mutually independent.  This idea of mutual independence gives it probabilistic strength and a gentle weakness because it does not parallel the real world where many things are partly or wholly interdependent. This is very true for words in a sentence where one word is linked to another because of our language's syntax's very nature. 

    Combining Data 
    We discovered that when the 'title' & 'subtext' feature from each post was combined, the models improved accuracy. 

    StopWords & Lemmatization
    We compiled the most commonly used words into a DataFrame and examined it to see what words could be added to our standard library of stop words.  In addition, we created a function to add lemmatization to our countvectorizer.

    Hyper tuning:
    We trained/tested the model through a grid-search to uncover the best hyperparameters for both the Naive Bayes algorithm and the Count Vectorizer 

## Conclusion

In conclusion, we discovered the best model for solving our problem statement is Naive Bayes, scoring an accuracy score of .9771 and a precision score of .9906 on our test data. With this model, Star Wars corporate will confidently know which is a Starwars subreddit and offer them the secret $15 discount off ComicCon 2021 entry fee.

## Areas of Future Studies

We plan to tune the hyperparameters within our model further and look into Neural Networks in place of the Naive Bayes.  We also would like to test this model randomly against other subreddit groups that will also have spectators at ComicCon 2021.




```python

```
