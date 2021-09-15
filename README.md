# Reddit_suicide_analysis
## Using PRAW API
1. Create a credential [following this post](https://towardsdatascience.com/how-to-use-the-reddit-api-in-python-5e05ddfd1e5c).
2. Praw_data_collection notebook explains the procedure of downloading data.
    1. Send a request to pull a user list who has post on r/ SuicideWatch between 2019/01/01 and 2020/12/31 using Pushshift API.
    2. Loop through the user list to get all posts, comments of each user and comments to their posts, if available.
## Pre-processing

## Cox Partial Hazards Model
[Here](https://lifelines.readthedocs.io/en/latest/Survival%20Regression.html) is the library that contains the survival model used. 
### Features selected
Two main categories of features are included:
1. Indicator of subreddit: top *k* subreddits are selected.
2. Indicator of keyword: use word2vec to expand a manually selected keyword list to *N* keywords.
