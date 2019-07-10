## Problem Statement

NLP (Natural language processing) is the practice of training machines and computers to learn our natural everyday language. To teach this practice, lets start by webscraping two reddit websites with at least a total of 1000 posts. For a model to be able to classify which class the prediction belongs to, this is a classification problem that is dealing with discrete variables. Our two subreddits were about NBA and NFL; by the end of training the model, we should see a high accuracy score which is indicative of how well the model can perform.

## Executive Summary

### Data wrangling/gathering/acquisition

We initially scraped both websites and pulled down their posts. We had initially tried pulling 20 per request however, that only summed up to being slightly less than 500. This was an issue because we wanted at least 500 posts from each website. This led to doubling the number of pull requested from 20 requests to 40 requests. When analyzing the most frequent words shown in both models, there were many common words or noise we saw between the two reddit posts (season, game) however, there were also numerous names we didn't want either reddit post to have (http, com). We wanted to remove this set of words by adding them to the set of stop words from the scikit feature extraction library. Once data wrangling and data acquisition are done, we concatenate our dataframes to make one whole dataframe for how model to train with. 
### Natural Language Processing

For both reddit posts, we converted our title features into our X and our subreddit into our target variable. The next step was to binarize the target variable into two discrete variables. Subreddits named "NBA" were now given a value of 1, whereas the subreddits with "NFL" were given a value of 0. Prior to modeling we, we established a baseline value from analyzing the binary variable with the majority count. The count of the majority class was 53% for the NBA class. This is a very low baseline value and therefore, we will have to fit our data into a classification model with robust parameters through gridsearching.

### Classification Modeling

Using count vectorizer to count the frequency of words, the two classification models used with count vectorizer were Logistic Regression and Naive Bayes. The two classification models that incorporated TFI-DF vectorizer however, were the Random Forest and Support Vector Machines. Through pipelining and gridsearching, we were able to find robust parameters for each of the models. The metric that measured the models success was accuracy of the test data. Accruacy tells us how accurately the model can predict the correct class of a given word. It is also crucial to compare each models train/test accuracy score because the difference between the two is indicative of how overfit the model is. Upon finding the best classification model, we then build predictions.


## Conclusion

It was clearly evident from the baseline score (53%) that the baseline model would not predict the source of words accurately. All of our classification models produced better scores than our baseline model by a huge increment, concluding that all of our models are better than our baseline model. From all of the classification models, the Naive Bayes model using countvectorizer produced the best metrics and therefore, we will use this model to generate which website a given word came from. Although the model is slightly overfit, it is much more mitigated compared to the other classification models. The model can now identify which subreddit a given word derived from!

Best score of our model with gridsearched parameters: 0.93.9
Ideal parameters: {'cvec__max_features': 3500, 'cvec__ngram_range': (1, 1), 'nb__alpha': 0.1}
Score of our train model: 0.967
Score of our test model: 0.939



















