# Sentiment Signals: Analyzing Tweets for Emotional Patterns
By [Jacob Ambert](mailto:jaambert@gmail.com), [Meghana Pakala](mailto:megpakala13@gmail.com), & [Katie Pegg](mailto:kpegg916@gmail.com)
![photo of a Welcome to SXSW banner](https://github.com/meghana-pakala/NLP-project/blob/main/images/SXSW.jpg)
We will take you into the world of digital communication, where every tweet, review, and online comment is a gold mine of insights waiting to be discovered through the latest advancements in data science and natural language processing.

We will showcase how we have harnessed sophisticated technology to sift through thousands of tweets related to Apple and Google products, collected during the South by Southwest Festival, or SXSW, of 2013. Our focus is to predict customer sentiment towards these tech hubs, turning raw data into a coherent narrative of public opinion.

## Business Understanding
Our analysis comes from cutting-edge machine learning techniques and natural language processing, allowing us to not only capture but also quantify the emotions embedded within the digital dialogue.

We will take you through our process of data cleaning, exploration, and model building that will reveal the story that lies beneath the surface of social media chatter where every like, share, and tweet is a piece of the larger puzzle of human emotion. Join us as we unveil the power of sentiment analysis, transforming the way we understand and interact with our customers. Let's begin our exploration into the world of "Sentiment Signals."

## Data Understanding
### Overview
Source: https://data.world/crowdflower/brands-and-product-emotions
- Target: positive, negative, & neutral sentiment
The data was sourced from CrowdFlower via Dataworld and the dataset includes over 9,000 tweets collected from the 2013 South by Southwest Festival in Austin, Texas.

SXSW is an annual conglomeration of conferences and festivals centered around art, music, and new technology.

Attendees are able to see new ideas and products unveiled side by side, and analyzing this subset of tweets gives us insight into their initial reactions broadcast in real time.

Given the tweets, human raters evaluated the perceived sentiment and rated it as positive, negative, neutral, or 'can't tell' and this sentiment will be the prediction target for our model.

After data cleaning, such as removing null and duplicate rows, we were left with about 8,000 tweets for analysis.

This graph shows that most of the tweets were for no brand in particular. Apple had the next most related tweets with Google to follow.
![graph showing tweets by brand: mostly tweets for no brand in particular, then apple, then google](https://github.com/meghana-pakala/NLP-project/blob/main/images/tweets_brand.png)

This graph is showing brand sentiment. We mostly see that neutral tweets were about no brand in particular. If there was a brand related to the tweet, it was typically a positive reponse for Apple & Google.
![graph showing brand sentiment: mostly neutral tweets, mostly positive for google & apple](https://github.com/meghana-pakala/NLP-project/blob/main/images/brand_sentiment.png)
This is potentially something to analyze further.

Here is an example of a tweet that was removed since it wasn't really classifiable because it was mostly special characters.
![example tweet of mostly special characters for removal](https://github.com/meghana-pakala/NLP-project/blob/main/images/example_spec_chars.png)

Here is an example of a negative regarding a specific issue with a specific product: the iPhone battery.
![example of negative regarding specific issue: iPhone battery](https://github.com/meghana-pakala/NLP-project/blob/main/images/example_battery.png)

## Preprocessing
To prepare for moedling, we ran standard preprocessing procedures, such as lowering the case for all the letters & removing special characters & common filler words. Specific to tweets, we removed username mentions, any hyperlinks, & text referring to retweets.

## Models
We went through a few different iterations of our models in our analysis. We looked at logistic regression, multinomial naive bayes, decision tree, & random forest models. The standout performers were a logistic regression for binary classification & a random forest for our multiclass model. Originally, the binary model was only about 34% accurate, but after some tuning, the accuracy increased to around 87% on the testing data. The multiclass model was initally perched around 64% accurate, but the score was increased to about 70% after some hyperparameter adjustments. The GridSearchCVs can be found in [this notebook](https://github.com/meghana-pakala/NLP-project/blob/main/notebooks-2/exploring-data-KP.ipynb).

## Evaluation Metrics
We used the accuracy score for our metrics since we wanted to decrease the amount of both false positives (customer likes the product when they do not) & false negatives (customer does not like product when they do) in our calculations.

## Recommendations
We have a few recommendations here. We can take insights from the negative tweets about certain keywords around features of products, like battery life in Apple's devices. This can be used to improve future devices.

There were also quite a few more tweets about Apple compared to Google devices, which is likely due to their popup store at the 2013 SXSW festival. We would recommend other brands, new & established, to follow that lead in having popup stores at SXSW and at other festivals. This could potentially increase a positive outlook.

We can further analyze why there are more tweets about specific Apple products, but not real specific Google devices mentioned. This could be because of brand confusion between Android & Google, or it is simply that Apple a smaller amount of products.

We can recommend our binary model for predicting sentiments, although we would still like to improve its accuracy. We can definitely improve our multiclass model by further customizing the data & tuning.

> hyperparameter tuning (potentially wider GridSearches or ensemble methods)
> weighting classes (negative & positive)
> larger data set for further training on positive & negative sentiments

## Repo Structure 
```
├── data
├── images
├── notebooks-2
├── .gitignore
├── LICENSE
├── final.ipynb
