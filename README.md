# ToxicTrek
Detecting Social Media toxicity using Word2vec and Ensemble learning.

## Core  
Social media is an integral part of the contemporary world. Individuals use it to share information, to have conversations or to create content. As one can share, say or comment on anything so along with positive material there is a lot of negativity on social media as well. According to numerous studies negative content, comments and conversations can have an adverse effect on individuals. This is imperative for major social media firms to quickly identify this type of content and remove it so that social media is a safe space for everyone. Hence, here we will try to identify whether a certain comment in English Wikipedia talks data-set is toxic (negative contribution to conversation) or not.

Our Methodology include firstly to convert the raw comments data into numerical representations (embeddings) and then use these as inputs to classifiers such as Logistic Regression, KNN, Naïve Bayes and ensemble methods such as RandomForest and AdaBoost to classify that whether a certain comment is toxic or not. 

## Data

The data has been taken from [**Wikipedia Detox**](https://meta.wikimedia.org/wiki/Research:Detox) project. This project has multiple data sets but we will be using toxicity annotated data-set. we have around 160k labeled comments from English Wikipedia by approximately 10 annotators via Crowdflower on a spectrum of how toxic the comment is (perceived as likely to make people want to leave the discussion) to how healthy to conversation the contribution is. The data can be found [**here**](https://figshare.com/articles/dataset/Wikipedia_Talk_Labels_Toxicity/4563973). From here we have two datasets that we will use: *toxicity\_annotations.tsv* and *toxicity\_annotated\_comments.tsv*.
