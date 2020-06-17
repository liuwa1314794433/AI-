# simple NN


## The sigmoid and the tanh functions are avoided in many applications nowadays since they can lead to the vanishing gradient problem.
    
- The ReLU function is a general activation function and is used in most cases these days.
  - note that ReLU function should only be used in the hidden layers.

- The Softmax function is used for output layer.

- Generally, when building a model, you can begin with using the ReLU. 
  - function and then you can switch to other activation functions if the ReLU.
  - function does not yield a good performance.


## The Problem: MNIST digit classification

- In this tutorial, we'll tackle a classic machine learning problem: MNIST handwritten digit classification: given an image, classify it as a digit.

- MNIST contains 70,000 images of handwritten digits: 60,000 for training and 10,000 for testing. 

- The images are grayscale, 28x28 pixels, and centered to reduce preprocessing and get started quicker.

- We’ll flatten each 28x28 into a 784 dimensional vector, which we’ll use as input to our neural network. Our output will be one of 10 possible classes: one for each digit.

## 1. Preparing the Data

- As mentioned earlier, we need to flatten each image before we can pass it into our neural network. We’ll also normalize the pixel values from [0, 255] to [-0.5, 0.5] to make our network easier to train (using smaller, centered values is often better).

## 2. Building the Model

- Every Keras model is either built using the Sequential class, which represents a linear stack of layers, or the functional Model class, which is more customizeable. We’ll be using the simpler Sequential model, since our network is indeed a linear stack of layers.
     
- The Sequential constructor takes an array of Keras Layers. Since we’re just building a standard feedforward network, we only need the Dense layer, which is your regular fully-connected (dense) network layer. Let’s throw in 3 Dense layers.

## 3. Compiling the Model

- Before we can begin training, we need to configure the training process. We decide 3 key factors during the compilation step:
      
- The optimizer. We’ll stick with a pretty good default: the Adam gradient-based optimizer (Adam - A Method for Stochastic Optimization). Keras has many other optimizers you can look into as well.

- The loss function. Since we’re using a Softmax output layer, we’ll use the Cross-Entropy loss. Keras distinguishes between binary_crossentropy (2 classes) and categorical_crossentropy (>2 classes), so we’ll use the latter. See all Keras losses.

- A list of metrics. Since this is a classification problem, we’ll just have Keras report on the accuracy metric.

## 4.Training the Model Training a model in Keras literally consists only of calling fit() and specifying some parameters. There are a lot of possible parameters, but we’ll only manually supply a few:

## 5.The training data (images and labels), commonly known as X and Y, respectively.

## 6.The number of epochs (iterations over the entire dataset) to train for.

## 7.The batch size (number of samples per gradient update) to use when training.

## 8. Testing the Model

## 9. Use the model

## 10. Prediction

  Using the trained model to make predictions is easy: we pass an array of inputs to predict() and it returns an array of outputs. Keep in mind that the output of our network is 10 probabilities (because of softmax), so we’ll use np.argmax() to turn those into actual digits.
 
## 11. Extensions
      
  What we’ve covered so far was but a brief introduction - there’s much more we can do to experiment with and improve this network. I’ve included a few examples below:
