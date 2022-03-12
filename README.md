# IMDB-reviews-sentiment-analysis
Natural language processing sentiment analysis was performed on labelled IMDB review dataset. Supervised deep learning was performed testing various neural network (NN) models from basic dense layering, to combinations of recurrent (RNN) and convolutional (CNN) neural networks of varying complexity. 

Overfitting was mitigated, and optimimum test accuracy was achieved, with the use of dropout layers alongside custom optimisers as well as word embeddings from GloVe. 

# Summary of results
Basic NNs with dense layers and RNNs with single LTSM and multi-layer LTSMs achieve a suspcioisly high training accuracy with validation loss increasing over epochs. Clear signs of overfitting.

Dropout layers achieve modest improvement but with clear signs of overfitting still. Using a custom optimiser, according to guidance from N. Srivastava, J. Mach. Learn. Res. 15 (2014) 1929-1958, achieves a substantial reduction in overfitting over 5 epochs suggesting early stopping here could work.

Using GloVe embeddings substantially improves results

To do: use BERT tokenzier


