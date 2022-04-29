# Natural Language Processing and Machine Learning for Planned Parenthood

Americans are divided on whether, and under what circumstances, pregnant people should be allowed to terminate their pregnancy. As with most issues nowadays, this debate plays out significantly on the internet. 

The social networking site Reddit provides forums called subreddits which are dedicated to certain topics. R/prochoice and r/prolife are two such channels; each describes itself as a place for like-minded users to discuss their views on the topic of abortion. Unlike r/prochoice, which has existed for several years, r/prolife was created in September 2021, around the time that a controversial bill was proposed in the Texas legislature, which would severely restrict the right to abortion and allow private citizens to be the enforcers that restriction. This bill is one of several in recent months that have heightened the pitch of the abortion debate across the country, with advocates on both sides working ever harder to make their messages heard.

For an abortion healthcare organization such as Planned Parenthood seeking to expand its membership and donations, machine learning using natural language processing could be a useful tool for classifying internet users as potentially receptive or potentially hostile to outreach. Moreover, NLP and machine learning tools could be potentially useful in refining our understanding of the lexicons and linguistic patterns used on both sides of the aisle. 


## Problem Statement
This project seeks to develop machine learning models using user posts on two abortion-related subreddits in order to answer the following questions:
- What is the best machine learning model to predict whether a Reddit post comes from a user who opposes abortion access or one who supports it?
- What data features work best as predictors?
- Are there observable language differences between posts by users in the two categories?


## Data

This project uses a dataset of approximately 10,000 posts from r/prochoice and r/prolife. The posts were collected in a .csv file titled "posts." Two .csv files with engineered features were used for modeling and are included in the directory: "posts_combined_text" includes a column concatenating title and selftext, and "posts_and_sentiment_scores" contains that feature as well as sentiment scores obtained using scikit-learn's VADER sentiment intensity analyzer.

**Data Dictionary:**

| Feature | Type | Description |
| --- | --- | --- |
| title | string | title of the subreddit post |
| selftext | string | text appearing below the title in the post |
| all_text | string | concatenation of title and selftext (contains extra ' ' if no selftext) |
| author_fullname | string | username of post author |
| created_utc | integer | timestamp of when post was created |
| subreddit | string | name of subreddit (prochoice or prolife) where post was created |
| sentiment_compound | float | scikit-learn SentimentIntensityAnalyzer compound score on all text |
| title_sentiment_compound | scikit-learn SentimentIntensityAnalyzer compound score on title |
| sentiment_pos | scikit-learn SentimentIntensityAnalyzer positive score on all text |
| sentiment_neg | scikit-learn SentimentIntensityAnalyzer negative score on all text |


## Observations and Findings

Some differences and language and sentiment between posts from the two subreddits were observed, including interesting differences in the distribution of compound sentiment scores. More research is warranted here.

After training logistic regression and decision tree classifier models on this data, and experimenting with different features, we did not conclusively determine which models or features are most useful for these predictions. This was largely due to the time-consuming nature of running these complex models -- we did not have enough time to adequately tune the models and compare them. However, it was observed that the logistic regression model, surprisingly, performed with higher variance than the decision tree classifier. It was also observed that sentiment analysis did not significantly improve the accuracy of the models.

