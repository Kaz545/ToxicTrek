# ToxicTrek :atom:
Detecting Social Media toxicity using Word2vec and Ensemble learning.

## Core  
Social media is an integral part of the contemporary world. Individuals use it to share information, to have conversations or to create content. As one can share, say or comment on anything so along with positive material there is a lot of negativity on social media as well. According to numerous studies negative content, comments and conversations can have an adverse effect on individuals. This is imperative for major social media firms to quickly identify this type of content and remove it so that social media is a safe space for everyone. Hence, here we will try to identify whether a certain comment in English Wikipedia talks data-set is toxic (negative contribution to conversation) or not.

Our Methodology include firstly to convert the raw comments data into numerical representations (embeddings) and then use these as inputs to classifiers such as Logistic Regression, KNN, Naïve Bayes and ensemble methods such as RandomForest and AdaBoost to classify that whether a certain comment is toxic or not. 

## Data

The data has been taken from [**Wikipedia Detox**](https://meta.wikimedia.org/wiki/Research:Detox) project. This project has multiple data sets but we will be using toxicity annotated data-set. we have around 160k labeled comments from English Wikipedia by approximately 10 annotators via Crowdflower on a spectrum of how toxic the comment is (perceived as likely to make people want to leave the discussion) to how healthy to conversation the contribution is. The data can be found [**here**](https://figshare.com/articles/dataset/Wikipedia_Talk_Labels_Toxicity/4563973). From here we will be using two datasets: *toxicity\_annotations.tsv* and *toxicity\_annotated\_comments.tsv*.

## Discussion 

To understand the data better we plotted the WordCloud for toxic and non-toxic comments and we can clearly see that in toxic comments there are a lot of expletive and indecent words while in non-toxic its the opposite. We can find these plots below. 

### _Toxic Comments_
![Toxic Comments](/Misc/toxic_comments.png)

### _Non Toxic Comments_

![Non Toxic Comments](/Misc/non_toxic_comments.png)

Furthermore, we converted our raw data into embeddings using word2vec. A language model details about which can be found [here](https://jalammar.github.io/illustrated-word2vec/). After converting the data into embeddings we plotted the data after apply PCA and we can see that toxic and non toxic comments are well separated in this space. Hence this output from the word2vec model can be used as an informative features to our classification models. 

### _PCA Plot_

![PCA](/Misc/pca_plot.png)

Note that we used PCA just to visualize the data and passed the whole output of 300 dimensional embeddings from word2vec to our models. Results for the models can be found below and AdaBoost seemed to have the best performance across all the metrics. Since we had imbalanced dataset we also utilized SMOTE to cater for that and then ran our models on balanced dataset. Models performed relatively better on the balanced dataset.

### _Results_
![results](/Misc/tt_results.png)

## How to Run

To run just simply download the required datasets from the link provided the data section. Set the correct path in the notebook and run this notebook on Colab :grinning:.
Specifically here in the notebook you can change the path: 
```
mydata1 = pd.read_table('/content/drive/MyDrive/Colab Notebooks/Project/toxicity_annotated_comments.tsv')
mydata2 = pd.read_table('/content/drive/MyDrive/Colab Notebooks/Project/toxicity_annotations.tsv')
```
##### Note
Paper is also attached for further details and references. This project is associated with my coursework at Georgia Tech. 
