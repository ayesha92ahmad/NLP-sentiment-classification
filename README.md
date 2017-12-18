# NLP-sentiment-classification
Natural language processing- classification of sentiment on twitter data

## Data
For the purpose of this project, we use Twitter dataset created by SemEval.
SemEval shared task Twitter data, labeled for sentiment. The Semantic Evaluation conference, SemEval, has recently added sentiment detection in Twitter messages and other social media genres to its shared tasks.
For example, in 2014, it ran as Task 9, sub-task B, Message Polarity Classification: http://alt.qcri.org/semeval2014/task9/.
The data was manually labeled and each dataset is available as a Twitter id paired with the manual label. There are 5 labels used for each message: “positive”, “negative”, “objective”, “neutral”, “objective OR neutral”. For this series of experiments, three class, “pos”, “neg” and “neu” are chosen. To actually get the tweets, a script can be run to get Tweets from Twitter. If a Twitter user has retracted their tweet, then Twitter will no longer send it out and it is marked as “Not Available”. The dataset given here was collected in the Spring 2014 from Twitter.
### Processing steps
The tweets dataset need to be preprocessed, to remove noise. For example, stop words, differently cased words, etc. Following is the order of steps used to preprocess the tweets, for one of the experiments:
1.	Convert every word to lower.
2.	Apply filter for alphabets determined by the regular expression: ^[^a-z] +$
3.	Apply filter for stop words- The list of stop words is obtained from ‘stopwords_twitter.txt’

For the other experiments, words are converted to lower case.
## Features
Experiments are performed with three kinds of feature sets. Document, SL, and POS
To create the feature set, all the words are taken into consideration. In this case, it is recommended to not filter any words for these. However, as one of the experiments, it is chosen to create feature set using the filtered document.

### Document/Bag of words feature
In a bag of words feature, all the words in the corpus are collected and some number of most frequent words are selected to be the word features.

### Subjectivity Lexicon
This feature set defines features that include word counts of subjectivity words negative feature will have number of weakly negative words + 2 * number of strongly negative words. positive feature has similar definition, not counting neutral words.

### Part of Speech
The part of speech tagger feature set takes a document list of words and returns a feature dictionary which it gets by running the default POS tagger (the Stanford tagger) on the document and counting four types of POS tags to use as features

## Results
Performance of Document feature on preprocessed (and filtered) tweets
![Document feature on preprocessed (and filtered) tweets](https://github.com/ayesha92ahmad/NLP-sentiment-classification/blob/master/images/doc-feat-preprocessed.png)

Performance of Document feature on all tweets
![Document feature on all tweets](https://github.com/ayesha92ahmad/NLP-sentiment-classification/blob/master/images/doc-feat-all.png)

Performance of subjective lexicon feature set on all tweets
![SL Feature set](https://github.com/ayesha92ahmad/NLP-sentiment-classification/blob/master/images/SL-feat-set.png)

Performance of part of speech feature set on all tweets
![pos feature set](https://github.com/ayesha92ahmad/NLP-sentiment-classification/blob/master/images/pos-feat-set.png)

Performance of subjective lexicon feature set on all tweets with K fold cross validation
![subjective lexicon feature set on all tweets with K fold cross validation](https://github.com/ayesha92ahmad/NLP-sentiment-classification/blob/master/images/kfold-sl-doc-pos.png)


Performance of subjective lexicon feature set on all tweets with K fold cross validation
![Performance of SK-learn's Multinomial Naive Bayes Classifier validation](https://github.com/ayesha92ahmad/NLP-sentiment-classification/blob/master/images/k-fold-multinom-nb.png)

## Conclusion
When the results of all these classification models are compared, it can be seen that there is not a major difference in the performance measures of them all. For future work, some additional features may be picked up. Entity extraction can improve the feature set and performance result leading to a better model. This was out of scope for this project, however, it would be a good extension to take up.
