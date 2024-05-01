# ToxicTrek
Detecting Social Media toxicity using Word2vec and Ensemble learning.

## Core  
Social media is an integral part of the contemporary world. Individuals use it to share information, to have conversations or to create content. As one can share, say or comment on anything so along with positive material there is a lot of negativity on social media as well. According to numerous studies negative content, comments and conversations can have an adverse effect on individuals. This is imperative for major social media firms to quickly identify this type of content and remove it so that social media is a safe space for everyone. Hence, here we will try to identify whether a certain comment in English Wikipedia talks data-set is toxic (negative contribution to conversation) or not.

Our Methodology include firstly to convert the raw comments data into numerical representations (embeddings) and then use these as inputs to classifiers such as Logistic Regression, KNN, Naïve Bayes and ensemble methods such as RandomForest and AdaBoost to classify that whether a certain comment is toxic or not. 

## Data

The data has been taken from \href{https://meta.wikimedia.org/wiki/Research:Detox}{\textbf{Wikipedia Detox}} project. This project has multiple data sets but we will be using toxicity annotated data-set. we have around 160k labeled comments from English Wikipedia by approximately 10 annotators via Crowdflower on a spectrum of how toxic the comment is (perceived as likely to make people want to leave the discussion) to how healthy to conversation the contribution is. The data can be found \href{https://figshare.com/articles/dataset/Wikipedia_Talk_Labels_Toxicity/4563973}{here}. We have two set of data \textit{toxicity\_annotations.tsv} \textbf{(1)} and \textit{toxicity\_annotated\_comments.tsv} \textbf{(2)} details of which can be found below. Schema for \textbf{\textit{toxicity\_annotations.tsv}}:
            \begin{itemize}
                \item \textbf{rev\_id}: MediaWiki revision id of the edit that added the comment to a talk page (i.e. discussion). 
                \item \textbf{worker\_id}: Anonymized crowd-worker id.
                \item \textbf{toxicity\_score}: Categorical variable ranging from very toxic (-2), to neutral (0), to very healthy (2) 
                \item \textbf{toxicity}: indicator variable for whether the worker thought the comment is toxic. The annotation takes on the value 1 if the worker considered the comment toxic (i.e worker gave a \textbf{toxicity\_score} less than 0) and value 0 if the worker considered the comment neutral or healthy (i.e worker gave a \textbf{toxicity\_score} greater or equal to 0). Takes on values in \{0, 1\}. 
            \end{itemize}
            Schema for \textbf{\textit{toxicity\_annotated\_comments.tsv}}:
            \begin{itemize}
                \item \textbf{rev\_id}: MediaWiki revision id of the edit that added the comment to a talk page (i.e. discussion).
                \item \textbf{comment}: Comment text. Consists of the concatenation of content added during a revision/edit of a talk page. MediaWiki markup and HTML have been stripped out. To simplify tsv parsing, \textbackslash n has been mapped to NEWLINE\_TOKEN, \textbackslash t has been mapped to TAB\_TOKEN and " has been mapped to `.
                \item \textbf{year}: The year the comment was posted in.
                \item \textbf{logged\_in}: Indicator for whether the user who made the comment was logged in. Takes on values in {0, 1}.
                \item \textbf{ns}: Namespace of the discussion page the comment was made in. Takes on values in \{user, article\}.
                \item \textbf{sample}: Indicates whether the comment came via random sampling of all comments, or whether it came from random sampling of the 5 comments around a block event for violating WP:npa or WP:HA. Takes on values in \{random, blocked\}.
                \item \textbf{split}: For model building in our paper we split comments into train, dev and test sets. Takes on values in {train, dev, test}.
            \end{itemize}
