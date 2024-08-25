---
author: 23A863N
title: "Applied Data Science Project Documentation"
categories: ITD214
---
## Project Background
As a member of a support group, we aim to set up an online support system to improve emotional support and provide a sense of community and anonymity to those taking part and seeking help.The online community allows individuals to connect with others experiencing similar challenges and share coping strategies.

By understanding user needs, preferences, and behaviours, we can optimize the platform's content to better meet their expectations. Ultimately, the goal is to create a positive and supportive online environment that fosters a strong sense of community and empowers users to effectively address their challenges. As a measurement of our goal, we hope to see an increase in positive sentiment expressed by users' post by 20%.

In particular, I will be exploring the overall sentiments of the community at large, and try to understand what they are struggling with, which in turn can be a motivating factor.

## Work Accomplished
Our primary source of data will be the scrapped data from the subreddit titled r/Foreveralone

### Data Preparation
Firstly, I import the libraries, in particular "praw", which is "Python Reddit API Wrapper", a Python package that allows for simple access to Reddit's API. I also import TextBlob, a library in Python for processing textual data. At the same time, I also calculate the polarity scores from the same subreddit.

While I tried to scrap 500 posts using the keyword "better", I was only able to extract 187 posts. this may be a limitation of using a simple free praw code.
I extract the 187 posts into a csv file titled "foreveralone_sentiment.xlsx"

Before I proceed with the modelling, I go through the data manually, and identify a list of stop words, which are words that appear commonly but hold little meaning to the sentiments expressed by the community. I remove white space, remove non-alphabetic characters, convert all text to lowercase and remove the list of stop words.

### Modelling
The extracted data includes polarity scores ranging from -0.75 to 0.5525. I classify polarity scores above zero to be positive, zero to be neutral, and scores below zero to be negative sentiment. I plot a histogram first to show the distribution of sentiments from the extracted data. From the histogram, we can see that 64% of the community have a positive sentiment, 30% are negative, and 6% are neutral
![Screenshot 2024-08-25 112616](https://github.com/user-attachments/assets/e9696e4e-03f0-4271-a6ac-0b83d1f386ba)

A bar chart helps us see clearly the percentage of overall sentiments expressed by the community. 
![Screenshot 2024-08-25 113406](https://github.com/user-attachments/assets/868012ed-6462-402a-93b2-061341fcf078)

Next, I identify the particular topics which are most commonly brought up by the community by using WordVectorizer and Latent Dirichlet allocation. I import the two libraries and run the codes, identifying the following topics:

-Topic 1: people life things time posts day want probably know person

-Topic 2: people going friends know feel life need social say years

-Topic 3: feel life love really women people time know way want

### Evaluation
I did a breakdown of each individual post by each user, to determine the probability of each comment being either positive or negative. 
Some results that returned were surprising, such as 
"Text: 28M Got my first girlfriend!
Probabilities: tensor([[0.4604, 0.5396]])"

![image](https://github.com/user-attachments/assets/379ee497-fadf-420c-ac6b-ebcb931c2ab9)


The exmaple above tells us that the predictor classifies the sentence "28M Got my first girlfriend!" has a probability of 46.04% to be positive, and a 53.96% of being negative. If we were to personally observe and understand the tone of the sentence including the exclamation mark, it is more than likely a positive comment, but the predictor gives it a higher probability of being negative.

## Recommendation and Analysis
Another sentiment model could be used, 

## AI Ethics
Discuss the potential data science ethics issues (privacy, fairness, accuracy, accountability, transparency) in your project. 

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce bibendum neque eget nunc mattis eu sollicitudin enim tincidunt. Vestibulum lacus tortor, ultricies id dignissim ac, bibendum in velit. Proin convallis mi ac felis pharetra aliquam. Curabitur dignissim accumsan rutrum. In arcu magna, aliquet vel pretium et, molestie et arcu. Mauris lobortis nulla et felis ullamcorper bibendum. Phasellus et hendrerit mauris. Proin eget nibh a massa vestibulum pretium. Suspendisse eu nisl a ante aliquet bibendum quis a nunc. Praesent varius interdum vehicula. Aenean risus libero, placerat at vestibulum eget, ultricies eu enim. Praesent nulla tortor, malesuada adipiscing adipiscing sollicitudin, adipiscing eget est.

## Source Codes and Datasets
Upload your model files and dataset into a GitHub repo and add the link here. 
