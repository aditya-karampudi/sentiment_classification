## What is Sentiment Analysis?
It is the procedure to recognize and categorize opinions conveyed in text to decide the writer’s intention towards the topic of the post.
To accomplish this, we use algorithmic approach and try to classify all the records according to their respective category. 

## What makes reviews hard to classify?
Human Language is natural language not a formal language, it is difficult to analyze
For example
 ‘Perfume review: if you are reading this because it is your darling fragrance, please wear it at home exclusively, and tape the windows shut’ --very difficult to figure out using just positive or negative words.
‘This film should be brilliant. it sounds like a great plot, actors are first grade. However, it can’t hold up.’  -- final sentence says a lot about the review	.
Automated sentiment analysis cannot understand sentiment in the context of business goals. -create new corpus based on specific words for machine to understand.

## Approach:
Text Preparation: Cleaning the extracted data before analysis. Non-textual contents like hyperlinks, special characters, number that are irrelevant for the analysis are identified and eliminated.
-	First the text data is uploaded to Python using pandas and a graph is plotted to know the number of records present in each class. It is found that nearly 60% of the data is marked as Negative sentiment. This is data with slightly Class Imbalanced.
-	In order to do Sentiment Analysis there is need of just words but looking at the data it has noise like hyperlinks, number, special characters etc. 
-	During preprocessing, text has been converted to lower case, all the characters other than a-z are removed and words which have length greater than two and less than 15 are only preserved. Next the data is divided into train and test with .75 and .25 ratio this should be done before model building because it will give realistic prediction of how model will perform. We use model to learn on train data and predict the test data. With this procedure, one can know the performance of the model on unseen data i.e. how well a model is generalized.
-	For an algorithm to do text analysis, raw data cannot be sent as input as scikit expects numeric input with fixed size. We need to take text and convert into vectors for that I used CountVectorizer which converts text into matrix of word counts. The role of fit is to learn the vocabulary of training data and transform is going to transform training data into document-term matrix with size 750*4313 matrix where 750 are the unique records and 4313 are the vocabulary terms of train data. 
-	In order to make a prediction, the new observation must have the same features as the training observations, both in number and meaning. Hence, we will only transform the test data and the countvectorizer drops the words in the test data that are not seen during model training. countvectorizer is just for extracting features and building document-tern matrix. The real model building uses this matrix to learn and predict.
