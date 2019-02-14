# Cameron Bronstein - Project 3
# Web APIs and Classification Modeling

For project 3, your goal is two-fold:
1. Using Reddit's API, you'll collect posts from two subreddits of your choosing.
2. You'll then use NLP to train a classifier on which subreddit a given post came from. This is a binary classification problem.

## Executive Summary

### Subreddits of choice!
[**Climate**](https://www.reddit.com/r/climate) | [**ClimateSkeptics Subreddit**](https://www.reddit.com/r/climateskeptics)

### Problem Statement
How do we classify speech or text when we do not know the source. This has importance today when much of the information we use to learn about and understand the world is flying through various platforms on the internet, quoted or paraphrased without sources.

In a highly politicized time, we can leverage machine learning to classify the source of text based information. In this specific context, how to we classify climate related speech into two competing categories - climate change acceptance and and climate change skeptics? Using natural language processing and machine learning models, we can do just that!

### Data Summary

|Feature|Type|Description|
|---|---|---|
|domain| object | The source of the post content |
|comments| integer | Number of comments on the post |
|title| object | The title content of the post (to be used for NLP) |
|score| integer | Up vote - Down votes |
|subreddit| integer | Climate (0) and Climate Skeptics (1) |
|url| object | url of the post content |
|lemmatized| object | Post title with lemmatized version of original words |
|stemmed| object | Post title with stemmed version of origial words |
|avg_word_len| float| Average length of the words used in each post |
|title_length| integer | Length of the post title |
| positive_sentiment | float | Positivity of post content |
|negative_sentiment| float | Negativity of post content |
|neutral_sentiment| float | Neutrality of post content |
|compound_sentiment| float | Overall sentiment of post content |

### Notebook Contents

- Imports
- API/ Data Collection
- Converting to pandas
- Text Preprocessing
  - Tokenizing
  - Lemmatizing
  - Stemming
  - Sentiment Analysis
  - Feature engineering
- Exploratory Data Analysis
- Initial Modeling
  - Text Vectorization
    - Count Vectorizer
    - Term Frequency - Inverse Document Frequency
  - Model Comparison
  - Text Comparison
- Final Model Selection
- Model Evaluation

### Presentation
[View it here](https://docs.google.com/presentation/d/1QGFuyKEImY6HTIwW1F5f3bF038ehyuIkR6byuQaJ5do/edit?usp=sharing)

### Conclusions
Model Ensembles were the most effective modeling techniques. I used a Bagging Classifier Decision Tree with bootstrapped data but inclusive features. The model performed with an average accuracy of 0.82 (standard deviation 0.0067) after 20 runs.

The model classified the two subreddits with similar accuracies (climate 0.85, climate skeptics 0.81). By looking at the misclassified posts, they are pretty quickly categorizable by interpreting their context or looking at the source of the linked media. Incorporating the source of the post content into the model could greatly improve its accuracy. Also, using broader n-gram ranges ((1,2), (1,3)) could add some 'context' to the features of our model.

Considering a model like Logistic Regression to bolster our interpretation of the modeling would be beneficial (the Bagging Classifier does not allow for interpretability despite it's increased performance).
