# Yahoo-Stock-NLP
redict daily stock movement (up or down)  based on financial news
We built a machine learning model to predict daily stock movement (up or down) based on financial news text and market data using a dataset from Yahoo Finance.
The text articles were categorized as either "news" or "opinion" pieces.

We extracted sentiment features using:

VADER SentimentIntensityAnalyzer (compound, pos, neg, neu scores)

TextBlob (polarity and subjectivity scores)

We combined these sentiment scores with basic stock price features (Open, High, Low, Close, Volume) to predict whether the stock would go up or down the next day.
the methods that we have used are:
Text preprocessing: Cleaning, tokenization, stopword removal, lemmatization.

Sentiment Analysis: Using VADER and TextBlob on cleaned text.

Feature Engineering: Combined stock prices and sentiment scores.

Machine Learning Models:

Logistic Regression (TF-IDF features)

K-Nearest Neighbors (TF-IDF features)

Linear Discriminant Analysis (sentiment + stock features)

Train/Test Split:

Time-based split (oldest 80% data for training, newest 20% for testing) to avoid data leakage.

Random split was tested initially but later corrected.
the results are:
1. Logistic Regression with TF-IDF features
Train Accuracy: ~78%

Test Accuracy: ~50–58%

F1-Score: 0.50–0.58

Interpretation:

The model overfits slightly (good train, poor test performance).

TF-IDF features are too sparse and high-dimensional, not enough signal for good prediction.

Conclusion: TF-IDF alone without considering sentiment or stock features is weak for this task.

2. K-Nearest Neighbors (KNN) with TF-IDF features
Train Accuracy: ~72%

Test Accuracy: ~50–55%

F1-Score: 0.50–0.55

Interpretation:

KNN performed even worse because high-dimensional sparse data is bad for distance-based methods like KNN.

Conclusion: KNN is not suitable for text-based stock prediction using TF-IDF.
4. Linear Discriminant Analysis (LDA) — Corrected Version (Time-based, no leakage)
Train Accuracy: 93.5%

Test Accuracy: 93.5%

F1-Score: 93–94%

Interpretation:

Very good balance between train and test accuracies.

No sign of overfitting or underfitting.

Sentiment scores and market features combined create strong predictive power.

Conclusion: This is the final, trustworthy result.
we predict stock movements, achieving around 93% accuracy on unseen data. The results are promising.
