# Reddit_suicide_analysis
## Using PRAW API
1. Create a credential [following this post](https://towardsdatascience.com/how-to-use-the-reddit-api-in-python-5e05ddfd1e5c).
2. Praw_data_collection notebook explains the procedure of downloading data.
    1. Send a request to pull a user list who has post on r/ SuicideWatch between 2019/01/01 and 2020/12/31 using Pushshift API.
    2. Loop through the user list to get all posts, comments of each user and comments to their posts, if available.
## Pre-processing
1. Text cleaning 
    1. remove special tokens, ...; 
    2. keep following attributes: user name, post time, text, title, subreddit.
3. Compute time to r/ SuicideWatch - time between first post/comment on r/ SuicideWatch to other posts and comments (in days).
4. Keep data only with a positive time, i.e., only focus on activities before on r/ SuicideWatch.
5. Assign a suicidal ideation score to each post/ comment using a [pretrained suicidal though detection model](https://www.kaggle.com/abhijitsingh001/suicidal-thought-detection/data?select=glove.840B.300d.pkl).
## Cox Partial Hazards Model
[Here](https://lifelines.readthedocs.io/en/latest/Survival%20Regression.html) is the library that contains the survival model used. 
### Features selected
Two main categories of features are included:
1. Indicator of subreddit: top *k* subreddits are selected.
2. Indicator of keyword: use word2vec to expand a manually selected keyword list to *N* keywords.
