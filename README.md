# CNN-CIFAR-10

A [Convolution Neural Network](https://en.wikipedia.org/wiki/Convolutional_neural_network) on the CIFAR-10 dataset. The CIFAR-10 dataset consists of images in 10 distinct classes. For more information refer to: [CIFAR website](https://www.cs.toronto.edu/~kriz/cifar.html). This project was made using TensorFlow and Python to build a multi-layered neural network, and achieved a maximum accuracy of 92.88% on the test dataset and a classification error of 7.12%. 

A good reference: (https://www.baeldung.com/cs/batch-normalization-cnn)

# Method

First, pre-process the data by taking each image and normalise its RGB values to between 0 and 1. Then categorise the data using one-hot encoding (The CIFAR-10 dataset images are in mutually exclusive categories). Input data is now a collection of normalised RGB values. To increase performance we can take the values of multiple images in one epoch. This is referred to as a "batch". Create a convolution layer with a kernel size of 3 by 3. This layer also pads the images witha  border of 0s, which means that corner and edge pixels are checked just as much as the centre pixels, giving a representive distribution across the feature map. Within every convolution layer the activation fuction ReLU is used. Activation functinos make the values in the matrix non-linear, as ReLU changes all tnegative values to 0. Computationally ReLU is very quick making it a good choice for hidden layers in the model.

Following a convolution layer, the batch is normalised meaning the values are changed to a Gaussian distribution standardising the inputs to a layer for each mini-batch. It helps to "coordinate the update of multiple layers in the model" Standardising the values of the previous layers results in less drastic weight update of subsequent layers, which helps to stabilise and speed up training. 

After 2 sets of convolution layers, the values are max pooled: the largest values inside a 2 by 2 window is chosen, reducing the size of the matrix by a quarter. Then the dropout layers;; where input units have a chance of a given rate to be set to 0, with the other units bing scaled up by 1/(1-rate). This ultimately prevents over-fitting which is a common problem in machine learning. This is exacerbated for CNNs in particular since they use a fully connected network so it is important to avoid it. This process is repeated a total of 3 times, with filter sizes of 64, 128, and 256 respectively.

Before compiling the data, the model needs to be converted to fullly connected network. First, data is flattened, from a multidimentional matrix to a 1D array. 3 further dense layers are then added. Dense layers are deeply connected which means neurons receive the input from other neurons in other layers.

```math
Loss = \displaystyle\sum_{i=1}^{output\ size} y_i \cdot \log \hat{y_i}
```
