## SENTIMENT ANALYSIS OF TWEETS
[![forthebadge](https://forthebadge.com/images/badges/made-with-python.svg)](https://forthebadge.com)<br>
### INTRODUCTION
<p align='justify'>In recent times people have started using social networking platforms like twitter..etc. This has
generated huge amounts of structured and unstructured data. Processing these huge amounts of
data can make us understand the intentions of the user which as a result can help in optimizing
user experience which plays a key role. This data requires analysis due to the need to easily
and accurately label sentiment classes on a large scale (huge data). Sentiment analysis is the
automated process of analyzing text data and sorting it into sentiments positive, negative, or
neutral. Using sentiment analysis tools to analyze opinions in Twitter data can help companies
understand how people are talking about their brand. Appropriate natural language processing
techniques are required to accomplish the goals. Methods that can analyze noisy data are
required as the data is on a large scale we may not have it in a structured manner. In the
marketing field, companies use it to develop their strategies, to understand customers' feelings,
how people respond to their campaigns or product launches. In the political field, it is used to
keep track of political views, to detect consistency and inconsistency between statements and
actions at the government level. It can be used to predict election results as well. Sentiment
Analysis also is used to monitor and analyze social phenomena, for the spotting of potentially
dangerous situations and determining the general mood of the blogosphere. Sentiment analysis
is also called opinion mining. Opinion mining involves analyzing opinions, sentiments, or
mentality of the author from the transcription. Online opinions have a great and direct influence
on the business of many e-commerce sites. Before buying any product on any online platform
it is a general tendency for a user to look at the review of the product and then buy it according
to the review given. This way sentiment analysis is very important in the industry.</p>

### APPROACH:
<p align='justify'>Sentiment analysis can be performed with different algorithms. They can be performed using
machine learning and deep learning algorithms. Machine learning algorithms are good to a
certain extent whereas deep learning techniques can dig deep inside the data and understand
the patterns from the data. We read in the data set and analyse the data by preprocessing
techniques. We only consider the “sentiment” and “tweet_text” column and drop the tweet_id
column as it is not necessary. The first thing we do after this is removing the stopwords from
the tweet_text column. Generally these words do not contribute and have no value in computing
the sentiment of a tweet. After removing the stopwords we also remove the mentions in the
text. In order for our deep learning model to understand the text data we convert into numbers.
To use the text as input for our model, we first need to convert the words into integers that refer
to an index in a dictionary. Only the most frequent words are kept. We clean the text by
applying filters and putting the words to lowercase. Words are separated by spaces. Once the
dictionary has been created we can convert the text to a list of integer indexes. This is done
with the text_to_sequences method of the Tokenizer. These integers are now converted into
one hot encoding features which are provided to the model. We also need to convert our target
classes to numbers in order for the model to understand. We perform OneHotEncoding to the
target labels with the to_categorical() method in keras. We use labelEncoder() function in
sklearn to convert the ‘positive’, ‘negative’, ‘neutral’ to their numerical representation. After
converting to numbers we apply the to_categorical() method in keras and convert it into onehot-
encoded form. After our data is ready we use the validation set to evaluate the model
performance when we tune the parameters of the model. We start with a model with 2 densely
connected layers of 64 hidden elements. The input_shape for the first layer is equal to the
number of words we allowed in the dictionary and for which we created one-hot-encoded
features. As we need to predict 3 different sentiment classes, the last layer has 3 hidden
elements. The softmax activation function makes sure the three probabilities sum up to 1. In
the first layer we need to estimate 640064 weights. This is determined by (nb inputs * nb hidden
elements) + nb bias terms, or (10000 x 64) + 64 = 640064 In the second layer we estimate (64
x 64) + 64 = 4160 weights In the last layer we estimate (64 x 3) + 3 = 195 weights. Because
this project is a multi-class, single-label prediction, we use categorical_crossentropy as the loss
function and softmax as the final activation function. We run for a predetermined number of
epochs and will see when the model starts to overfit. Now, we can try to do something about
the overfitting. There are different ways to do that.</p>
<div>
<p align='justify'>1] Reduce the network's size by removing layers or reducing the number of hidden elements in
the layers.
<p align='justify'>2] Add regularization, which comes down to adding a cost to the loss function for large weights.</p>
<p align='justify'>3] Adding dropout layers, which will randomly remove certain features by setting them to zero.</p>
<p align='justify'>1. Reducing the network's size: We reduce the network's size by removing one layer and lowering the number of hidden elements in the remaining layer to 32. We can see that it takes
more epochs before the reduced model starts overfitting (around epoch 10). Moreover, the loss increases much slower after that epoch compared to the baseline model.</p>
<p align='justify'>2. Adding Regularization: To address overfitting, we can also add regularization to our model. For the regularized model we notice that it starts overfitting earlier than the baseline model. However, the loss increases much slower afterwards.
<p align='justify'>3. Adding drop out layers: The model with dropout layers starts overfitting a bit later than the baseline model. The loss also increases slower than the baseline model. From the results obtained by training and testing our model, the model with the dropout layers performs the best on the test data.</p></p></div>

### MODEL ARCHITECTURE
![model architecture](https://user-images.githubusercontent.com/48044041/88028665-970c1980-cb56-11ea-8f79-7643ccabc754.png)
### Kaggle Score
<img src='https://user-images.githubusercontent.com/48044041/208591004-16dda4d6-299f-4d9e-93a8-7eefe24244c2.PNG'>
<img src='https://user-images.githubusercontent.com/48044041/208590762-13982523-7c8d-4d49-8c5a-bc60dfeff5a8.PNG'>

## Future Work
Working on different approches to improving the Accuracy...
