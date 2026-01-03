# CNN-CIFAR-10

A [Convolution Neural Network](https://en.wikipedia.org/wiki/Convolutional_neural_network) on the CIFAR-10 dataset. The CIFAR-10 dataset consists of images in 10 distinct classes. For more information refer to: [CIFAR website](https://www.cs.toronto.edu/~kriz/cifar.html). This project was made using TensorFlow and Python to build a multi-layered neural network, and achieved a maximum accuracy of 92.88% on the test dataset and a classification error of 7.12%. 

# Method

First, pre-process the data by taking each image and normalise its RGB values to between 0 and 1. Then categorise the data using one-hot encoding (The CIFAR-10 dataset images are in mutually exclusive categories). Input data is now a collection of normalised RGB values. To increase performance we can take the values of multiple images in one epoch. This is referred to as a "batch". Create a convolution layer with a kernel size of 3 by 3. This layer also pads the images witha  border of 0s, which means that corner and edge pixels are checked just as much as the centre pixels, giving a representive distribution across the feature map. Within every convolution layer the activation fuction ReLU is used. Activation functinos make the values in the matrix non-linear, as ReLU changes all tnegative values to 0. Computationally ReLU is very quick making it a good choice for hidden layers in the model.

Following a convolution layer, the batch is normalised meaning the values are changed to a Gaussian distribution standardising the inputs to a layer for each mini-batch. It helps to "coordinate the update of multiple layers in the model"
