# A and A1 Algorithm search

## Use CNN to Image Classification


## Digital representation of an image

- Grayscale image is a matrix of pixels (picture elements).  

- Dimensions of this matrix are called image resolution (e.g. 300 x 300).  

- Each pixel stores its brightness (or intensity ranging from 0 to 255).  

- Intensity corresponds to black color.  

- Color images store pixel intensities for 3 channels: red, green and blue.  


## Convolutional vs fully connected layer  
- In convolutional layer the same kernel is used for every output neuron, this way we share parameters of the network and train a better model.  

- 300x300 input, 300x300 output, 5x5 kernel – 26 parameters in convolutional layer and 8.1×10B parameters in fully connected layer (each output is a perceptron).  

- Convolutional layer can be viewed as a special case of a fully connected layer when all the weights outside the local receptive field of each neuron.  
   
- Equal 0 and kernel parameters are shared between neurons.  


## One convolutional layer is not enough
- It looks like we need to stack a lot of convolutional layers.

- To be able to identify objects as big as the input image 300x300 we will need 150 convolutional layers.
