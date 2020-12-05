# Project III - Readme doc 
Theoretical project: The goal is to reward loyal StarWars fans. To do this a binary classification using NPL is preformed on two different subreddit to determine which is Starwars and which is StarTek.

- Christoper Villafuerte


#### Files 

- 00-reddit_digger.ipynb
- 01-Data_clean-proj_3.ipynb
- 02-basic_modeling-proj_3.ipynb
- 03-nbayesGS_proj_3.ipynb


---

#### Executive summary / Problem statment

StarWars Corporate (Disney) wants to have an overwhelming turnout of fans for the Comic Con 2021.  
- To achieve this Disney is sending reward their fans on the  subbredit StarWars, offering a secret $15 discount off ComicCon 2021 entry fee.  
- Problem: The promotion is only for participants on the StarWars subreddit, therefore corporate want to make sure that only StarWars fans receive this promotions.

#### Problem Statment:

- Problem is to  create a model that yields a high accuracy and precision score in a binary classification between the subreddits StarWars and StarTrek?
    

---

### Data Collection

Data cleaning was done separtly for both subreditts to insure that equal samples of each subredit was used.

   During the cleaning of the data it was noticed that many of the reddit posts had a large number of NaN values with in its 'selfText tag'.  StarWars reddit had a proportionate number of NaN compared to starwars.

We also found that a number of selftexts where '[deleted]' or '[removed]' leaving their selftext unusable. We deleted all instences of both '[deleted]' or '[removed]' to insure the our data was the most complete. 

  By the time we ran our final models we had collected 23,700, StarWars subReddits and 9,000 Startrek subreddits.  Of this origonal data 5,712 Starwars subReddits and 6,000 startrek subReddits where used to run within our models. 

### Model Evaluation:

In desided on our basic model we ran a base model of Naive Bayes, Logistic Regression, Random Forest and Adaboost classifier models, each paired with TfidfVectorizer and CountVectorizer.  

We are looking to see which model has the best Accuracy and Precision.
Specifically of the subreddits that we idenified as being Starwas, how many of those did we get correct. 

Using this Rubric we found that Naive Bayes with Count Vectorizer yeilds the highest performence. 

Below are all graphs showing each model accuracy and precision score. 


```python

```

For all three of these scores Naive Bayes had the highest performence therefore we disided to us this going foward. 

#### Baseline Score

If we where to randomly pull a sample there is a 51% chance that it will be a Starwars class

---

#### Stop words and Lemmatization 

We compiled the most commonly used words into a DataFrame and examined it to see what words could be added to our standard libary of stop words.
- We looked for commonly used words, words in the top 100) that we felt did not help for the relevence of our two classes. 
- we removed words like 'http' , 'com', 've', 'www', 'reddit'
- oddly when we removed the word 'https' we had a drop in accuracy so we left it in

We also crafted a function (with the help of slow jams) to add lemmatization to our countvectorizer. 
- We also saw that we needed to lemmatize our stop words so that both the lemmaizer function would work with our custom stop words

---

#### Model final - Naive Bayes

The Naive Bayes is a probabilistic algorithm.  Our features within this model are the words and their frequency.  Bayes caluclates the probaility of that word using its word frequency and naive bayes assumes every word is independent of the others.  From this the algorithm calculates all the probability senerios and chooses the largest.

A disadvantage of naive bayes is also its strength, in assuming that all attirbutes(features) are mutually independent it does not parrellel the real world where not many things are completly independet of eachother.  This very true for words in a sentence where one word is linked to another because of the very nature the syntex of our language. 
The streagths of native bayes is that it is easy to implement and has a short trianing time.

#### Our Hyper tuning

---

When creating the final model we ran both Naive Bayes & count vectorizer thourgh a gridsearch to establish its best paramaters. 
- Naive Bayes we tested 1, .1, and .01 for the Alpha parenater 
- a (1, 2) CountVectorizer n_gram range was choosen from our gridsearch 
- a min df of 10 for CountVectorizer was choosen out of [1, 2, 6, 10]
- we  used our Lemmatization function 
- we also used our custom stop_words over the standard stop words


Combining our data
- At first we used the 'title' then the 'subtext' from our reddit post as data for classificaiton. 
- For our final model we created a 3rd data feature called 'max_text' that was a combination of both 'title' and 'subtext' 

Through the above process we continually adjusted our model to tune it for the highest Percision score over accuracy.

The final model had a accuracy score is .9771 and a perpercision score of .9906.

With a high accuracy and precision score in a binary classification between the subredits StarWars and StarTrek this model can infer if a reddit is one or the other. 

With this model Starwars corparte will confidently know which is a Starwars subbreddit and be able to offer them the secret $15 discount off ComicCon 2021 entry fee. 

#### Next Steps

- Next steps would be to first re-examine the stop words and add to our dictonary.
- Also the next step would be to add a whole new model, neural network


```python

```
