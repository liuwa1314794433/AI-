# Tutorial RNN with Keras

## Tutorial: Recurrent Neural Network by Keras

## The Problem: Movie review sentiment analysis
   - In this tutorial, we will perform sentiment analysis on a corpus of movie reviews from Rotten Tomatoes.

   - The dataset is from Kaggle. In this tutorial, we use 39015 phrases as training data and 7803 phrases as testing data. Each phrase is labeled on a scale of zero to four. The sentiment corresponding to each of the labels are:

     - 0: negative
     - 1: somewhat negative
     - 2: neutral
     - 3: somewhat positive
     - 4: positive


## 1. Preparing the Data

## 2.Clean text
   - ASCII characters are ultimately interpreted by the computer as hexadecimal. In consequence, to a computer, ‘A’ is not the same as ‘a’. Therefore, we’ll want to change all characters to lowercase. Since we’re going to be splitting the sentences up into individual words based on white spaces, a word with a period right after it is not equivalent to one without a period following it (happy. != happy). In addition, contractions are going to be interpreted differently than the original which will have repercussions for the model (I’m != I am). Thus, we replace all occurrences using the proceeding function.

   - Word embedding
       Computers don’t understand words, let alone sentences, therefore, we use the tokenizer to parse the phrases. In specifying num_words, only the most common words will be kept. The tokens are then vectorized. By vectorized we mean that they are mapped to integers.

  - Pad sequences
       In order to feed this data into our RNN, all input documents must have the same length. We will limit the maximum review length to max_words by truncating longer reviews and padding shorter reviews with a null value (0). We can accomplish this using the pad_sequences() function in Keras.

## 3. Building the Model
  - Our model is a simple RNN model with 1 embedding, 1 LSTM and 1 dense layers.


## 4. Compiling the Model
  - Before we can begin training, we need to configure the training process. We decide 3 key factors during the compilation step:

  - The optimizer. We’ll stick with a pretty good default: the Adam gradient-based optimizer (Adam - A Method for Stochastic Optimization). Keras has many other optimizers you can look into as well.

  - The loss function. Since we’re using a Softmax output layer, we’ll use the Cross-Entropy loss. Keras distinguishes between binary_crossentropy (2 classes) and categorical_crossentropy (>2 classes), so we’ll use the latter. See all Keras losses.

  - A list of metrics. Since this is a classification problem, we’ll just have Keras report on the accuracy metric.

## 5. Training the Model

## 6. Using the Model
   - Now that we have a working, trained model, let’s put it to use. The first thing we’ll do is save it to disk so we can load it back up anytime.

## 7.Prediction result on test data
   - Using the trained model to make predictions is easy: we pass an array of inputs to predict() and it returns an array of outputs. Keep in mind that the output of our network are probabilities (because of softmax), so we’ll use np.argmax() to turn those into actual classes.

