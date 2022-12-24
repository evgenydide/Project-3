### Overview
The goal of this exercise is to investigate how capable are the basic classification functions at distinguishing text data from two subreddits of similar general topic. The subreddits chose are "Relationship" and "Am I the Asshole", they both cover stories of conflic in interpersonal relationships and they are both very text heavy. It just so happen, that most subreddits I can think of are mostly either links or pictures, procuring 1,000 posts somewhere else would be a trouble to me. 

### Data Acquisition 

We were provided with an API that pulled all the necessary data from reddit and with instructions on how to use it optimally. For each subreddit, a loop was made that pulled 100 posts, assigned the first (chronologically) post date to a parameter list, waited 2 seconds and repeated the process until a desired number of posts was accumulated. Both subreddits had significant number of removed posts, so number of loops was adjusted. Data from title and posts was fed to two separate dataframes that were merged after rows with removed posts were dropped. API provided a lot of data, but the only one that was passed down was subreddit name, post title and post text. 

### EDA

Very little was done in terms of EDA. Somehow there were some duplicated and 1 null value, they were dropped. Then a dataframe was created using Count Vectorizer. Stopwords were used fron 'english' list as well as some misspells from said list that occured too often (top 15), the subreddit names and some of their derivatives, tldr and words 'amp' and 'x200b'. Resulting dataframe had 21,000 columns. Modeling this proved to be impossible, so it was further weeded out with parameter max_df=0.5,min_df=0.01, leaving just over 4 thousands columns. 

### Modeling

For modeling I run through most of the classifier models that I knew about with scaling, gridsearch, cross validation and train test split when I though it was appropriate. The result was roughly 84% accuracy score on test data with KNN and Single tree undeperforming significantly and Extra Trees performing slightly better than everyone else with 88.4% accuracy score. 

### Conclusion and recommendations

Models performed adequately well. I was not too surprised to see that most classifier models produced very similar result and I assume they did the best out of the data they were fed. It would be a bit curious to run the grid search for most of the models on the entire dataset, maybe even with n_grams (I somehow saw 420,000 columns), it should work better, but I'll probably have to leave my pc calculating this for a day or two. My recommendation- don't do reddit, its not worth it. Idk, I can't imagine any real problem here, its just sating curiosity at best. 