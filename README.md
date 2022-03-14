# IMDB-reviews-sentiment-analysis
Natural language processing sentiment analysis was performed on labelled IMDB review dataset. Supervised deep learning was performed testing various neural network (NN) models from basic dense layering, to combinations of recurrent (RNN) and convolutional (CNN) neural networks of varying complexity. 

Overfitting was mitigated, and optimimum test accuracy was achieved, with the use of dropout layers alongside custom optimisers as well as word embeddings from GloVe. 

# Summary of results
Basic NNs with dense layers and RNNs with single LTSM and multi-layer LTSMs achieve a suspcioisly high training accuracy with validation loss increasing over epochs. Clear signs of overfitting.

Dropout layers achieve modest improvement but with clear signs of overfitting still. Using a custom optimiser, according to guidance from N. Srivastava, J. Mach. Learn. Res. 15 (2014) 1929-1958, achieves a substantial reduction in overfitting over 5 epochs suggesting early stopping here could work.

Using GloVe embeddings substantially improves results with overfitting absent and validation loss and accuracy converging at ~83%. 

To do: use BERT transformer for potentially higher accracy model. With overfitting largely mitigated, more neurons and/or layers can potentially be introduced to increase complexity of model for higher accuracy model.

Data can be found here:

https://www.kaggle.com/lakshmi25npathi/imdb-dataset-of-50k-movie-reviews

# Basic NN 
The first model we study is a basic NN with dense layers with relative simplicity to try to avoid overfitting--this is usually a problem for NLP due to out-of-vocabulary words often present in the testing data.

We see that over 10 epochs, not only does the model fit the training data suspiciously well (100% accuracy after only a few epochs), it performs poorly on the testing data with validation accuracy decreasing over epochs and with a corresponding increase in validation loss. These are clear signs of overfitting, with the model performing increasingly poorly on testing data. 

# RNNs with LSTM
Next we try an RNN, by way of a multi-layer bi-directional long-short-term-memory (LSTM) model. Such a model is more appropriate for NLP as it allows the algorithm to learn from the sequency of the words in sentences and not just the words themselves, independent of where they are in a sentence. This is achieve with a LSTM by allowing the 'memory' of past words in sentences to correlate with words over distance.

We see some improvement on the basic NN with training accuracy rising steadily however we still see clear signs of overfitting.

Next we take a standard approach to attempt to avoid overfitting by introducting 'dropout' layers to the model. This works by randomly dropping neurons with each iteration, losing their memory of the correlations between neurons and their contribution to the network and forcing neighboring neurons to reconfigure to adapt to these changes. This helps to avoid neurons settling in to a narrowly learned pattern and remain 'dynamic' with new data. 

Consulting the original paper on dropout layers N. Srivastava, J. Mach. Learn. Res. 15 (2014) 1929-1958, indicates that a custom optimiser for the model is also appropriate, with an increased learning rate and momentum, which we use. 

We see good improvement to the model with overfitting absent up to around 5 epochs. After this however, the validation loss begins rising again. This suggests we could use 'early stopping' and limit the number of epochs here.

# GloVe embedding
A modern approach to NLP often utilises pre-trained word vector embeddings. One such example is GloVe, provided by Stanford University, which implements an unsupervised ML algorithm to get word embeddings from the substructure of the word vectore space. This means it is also learning from the 'makeup' of each word, from the sub-words, greatly improving the models capabilities. 

Here we see a substantial improvement on the model with signs of overfitting absent over all 10 epochs sampled. The validation accuracy beings higher, most likely owing to the pre-trained word embeddings, and climbs for all 10 epochs with validation loss falling as well. The results suggest the model is converging, and indeed it is the case if one increases the number of epochs we see convergence of these metrics. 


