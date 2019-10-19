# Web API and Classification project

![picture1](/pic/wow_c.png)

### Description

The goal of this project is to use API grab data from 2 different subreddits and use NLP method to preprocessing the data and eventually make a classification model. Also use the model to predict if any new post to test the accuracy of the model to predict which category a new post should belong.

The 2 subreddit I selected from reddit is [/r wow](https://www.reddit.com/r/wow/) and [/r classicwow](https://www.reddit.com/r/classicwow/).  

WOW (World of Warcraft) is a MMORPG made by Blizzard Entertainment. It was released at 2004 and it was known as the best RPG game at the time. By 2017, the game had grossed over $9.23 billion in revenue, making it one of the highest-grossing video game franchises of all time. 

However, the heat of the game will decrease overtime even for the most popular game. WOW has been having hard time for the past couple years. In August 26, 2019 blizzard release the Classic WOW - the original version of this game. And it was a big success. Thousands of players went back and even need to wait in queue for hours to get in the game. The peak time of Chinese server alone there are 1 million players online in the same time. 

![picture2](/pic/waiting.png)

Through this project we are briefly looking into how the players behavior on reddit towards these extremely related topics.


### Getting Data

Using PushshiftAPI as tools to get data from reddit. I grabbed 5000 data for each subreddit, and the last reddit post is at 2019/10/15 21:16:53. I used 75% of these data to build data, 25% of the data to test the accuracy of the model. 

### Data Preprocessing

Tried the following combination of NLP method and picked the one with the best accuracy score:

|Vectorizer|Max_feature|Stem|
|---|---|---|
|CountVectorizer  |1000| Yes|
| CountVectorizer |2000| Yes|
|CountVectorizer  |3000| Yes|
|CountVectorizer  |1000| No |
| CountVectorizer |2000| No |
|CountVectorizer  |3000| No |
|TfidfVectorizer  |1000| Yes|
| TfidfVectorizer |2000| Yes|
| TfidfVectorizer |3000| Yes|
| TfidfVectorizer |1000| No |
| TfidfVectorizer |2000| No |
| TfidfVectorizer |3000| No |

The best combination is TfidfVectorizer with 3000 features and stem

### Model Selection

After GridSearch here are the accuracy score for testing and training set of each model.

|index|Model|Vectorize method|Train Score|Test Score|Time to run|
|---|---|---|---|---|---|
|0|Logistic|Cvect|0.8832|0.7352|6.11298|
|1|Logistic|Tvect|0.8432|0.756|16.205156|
|2|Multinomial|Cvect|0.787733|0.7544|1.134696|
|3|Multinomial|Tvect|0.823467|0.756|0.653692|
|4|Random Forest|Cvect|0.6452|0.632|25.084262|
|5|Random Forest|Tvect|0.65|0.6452|25.10024|

Also tried SVC, Decision and Knn model, but due to the limit of computation power of my computer has to give up and using Logistic, Multinomial and Random Forest.

Here is a graph of the prediction vs actually category. We can see that the 2 subreddits are very closely related and there is a big area of overlapping. 

<img src = '/pic/prediction.png' width = '500'>

### Getting New Data and check for accuracy
From 2019/10/15 21:16:53(latest posting we grab) to 2019/10/18 10:20:00 there is another 1977 new posting, the model predicted 79.80% accuracy of these new postings.


Here is a link to [presentation](https://docs.google.com/presentation/d/1Ny9XV__mlxm9311w9kLPTA818Wd0qMe8BReAcnBKEF8/edit?usp=sharing)
# Reddit-Classification-Project
