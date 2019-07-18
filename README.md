# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) What sport are we talking?
## Using NLP & Classification to differentiate between r/nfl and r/nba

### Problem Statement

How can we use NLP & Classification to differientiate between r/nfl and r/nba?

### Executive Summary

Admittedly, I am a **huge** sports fan. I am a diehard Buffalo Bills fan, and I have always loved watching the NBA. But there are plenty of people out there that just aren't that interested in sports, that generally give blank stares when you ask them what they thought of NBA free-agency or who is going to win the SuperBowl. Well if those people want to get more involved, this notebook should help them at least determine if someone is talking about the NBA or the NFL and the relevant lingo for each. This notebook aims to achieve two main goals: scrape reddit's api for posts & comments and use natural language processing to build classification models that predict the subreddit for the text in a given post or comment. Not surprisingly, keywords like player name and team name are big indicators. Then there are position names and verbs that are unique to each sport that can help differentiate.

#### Contents of Repository

* [Code](https://git.generalassemb.ly/cobkenney/DSI-Assignments/blob/master/Project_3/code/What%20sport%20are%20we%20talking%3F.ipynb)
* [Data](https://git.generalassemb.ly/cobkenney/DSI-Assignments/tree/master/Project_3/data)
* [Images](https://git.generalassemb.ly/cobkenney/DSI-Assignments/tree/master/Project_3/images)

#### About the Data

The data is scraped from Reddit's API which can be retrieved fairly easily. You take a reddit url such as [https://www.reddit.com/r/nba/](https://www.reddit.com/r/nba/) and add .json to the end of it. You can then use the ```requests``` library to scrape the pages for posts and comments. After some cleaning and manipulation, the result is a pandas dataframe with at least a column of text and a column with the post/comment's respective subreddit. In order to convert the words into numbers for modeling, you can use a vectorizer such as CountVectorizer of TfidfVectorizer to vectorize your words. The result is interpretted in various models.

### Conclusions & Next Steps

After scraping over 5000 posts and comments from r/nfl and r/nba, logistic regression and MultiNomial Naive Bayes proved to be the best models to predict subreddit. When predicting whether or not a post or comment came from r/nfl or r/nba, posts were easier to classify than posts & comments. Removing words like nba and nfl reduced accuracy in my models, but not hugely. My logistic regression model was 95.61% accurate when I kept nba and nfl as words, but it was still 93.07% accurate when I took those words out. Player names and team names were strong features in predicting the subreddit. For example, Kawhi & Clippers were large negative coefficients in my logistic regression model. Westbrook and Kawhi were my most important features in my random forest model. After player names and team names, positions were another important differentiator. Qb was one of the largest positive coefficients for my logistic regression. Overall, the lingo for each sport is fairly distinguishable. <br>

For the future, I want to expand my dataset since these terms are really relevant for June-July 2019, but may not be relevant in a year or in 10 years. The team names will most likely be the same, but the players will be different. I would also like extend the model into a multi-class model with more sports subreddits to help differentiate between other sports.

