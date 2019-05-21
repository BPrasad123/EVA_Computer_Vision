
# Architectural Basics #

## Image Normalization
If we do not normalize the data, then each feature will be having different pixel value distribution. This will result in over weight correction for some features while under correction for others during the backpropagation. This is not an ideal scenario that we want.  

There are three techniques for normalization:
(x - x.min()) / (x.max() - x.min()) => values from 0 to 1  
2*(x - x.min()) / (x.max() - x.min()) - 1 => values from -1 to 1  
(x - x.mean()) / x.std() => values from anything to anything, but mean at 0  

For image inputs we need all our pixel values to be positive and considering simplicity, we normally go ahead with the first of above mentioned techniques. Normalizing the data helps in faster convergence and better accuracy.

## Number of Epochs and when to increase them
Case 1: If the training accuracy is increasing and validation accuracy is not at least decreasing for a few consecutive epochs, we can increase number of epochs.
Case 2: During optimum Learning Rate strategy such as Cyclic Learning Rate, we need to run the model for higher number of epochs to get the optimal range of learning rate


## we know our network is not going well, comparatively, very early
If the running model is not improving the training accuracy much for first 5-8 epochs then it is very unlikely that the model will perform way better with higher number of epochs. In this case we need to look into the network architecture.

## Batch Size, and effects of batch size
The batch size should be large enough that is likely to include the data from each class randomly. Larger batch size results in smaller epoch time provided the underlying memory supports the same. However, the point to note here is that larger batch size not alway necessarily results in better accuracy. We need to try with a few different sizes in a  trial and error fashion to know which batch works the best for the given dataset. Moreover, considering the computational optimality we normally consider the batch size to be a power of 2.

## 3x3 Convolutions
Instead of directly convoluting the image with intended size of kernel (like 5x5, 7x7, 9x9 or 11x11) we can always repeat 3x3 convolution so as to reach the effective kernel size of our inteded size - like two times 3x3 to reach 5x5, three times to reach 7x7 and so on. There are a few benefits, as mentioned below, of doing so hence it is a popular approach of convolution.  
* With repeat of 3x3 convolutions we end up with lesser number of model parameters
* This results in addition of more layers hence giving more opportunity to the model to learn better
* With smaller size of kernel the extracted feature is pretty local instead of a general overview of the image. This helps in capturing complex features of the image.  

## How many layers
When all other ideal network design related requirements are fulfilled, having more number of layers generally result in better accuracy. However we generally add layers judiciously till we reach the receptive field close to that of the object in the image. If we need our model to learn the background as well because of its significance, then we can add more layers while ensuring that the receptive field size is equal or a little more than that of the image.

## MaxPooling
Pooling helps to reduce the spatial dimension of an image. Among all the pooling techniques, Max Pooling is the most popular one. Generally it is of size 2x2 and operates with stride value of 2. It takes the max value from the portion it operates on and puts that in the feature map. When with max pooling the spatial dimension gets reduced by half, the effective global receptive field is doubled.

## Receptive Field
A receptive field (considering global receptive field) is the effective dimension of input that the convolutional layer looks at. With more number of convolution layers as the spatial dimension reduces the effective receptive field size increases. To can calculate the difference between the input size and remaining spatial dimension to get the receptive field size at a particular layer when convolution has been done with zero padding.

## SoftMax
It is a normalized exponential function that takes the real numbers and provides with probability like score. It must not be considered as probability of the class labels. Rather it is an exponentially caliberated score for each class outcome for better differeciation.

## Learning Rate
It decides how many times the negative grandient step needs to be taken for each update during gradient descent. We can change the LR at different steps of training by using LRScheduler or ReduceLROnPlatau or CyclicLR. Generally learning rate is kept at a low number for better convergence. 

## 1x1 Convolutions

## Kernels and how do we decide the number of kernels?

## Batch Normalization

## Position of MaxPooling

## Concept of Transition Layers

## Position of Transition Layer

## The distance of MaxPooling from Prediction

## The distance of Batch Normalization from Prediction

## DropOut

## When do we introduce DropOut, or when do we know we have some overfitting

## When do we stop convolutions and go ahead with a larger kernel or some other alternative (which we have not yet covered)

## When to add validation checks

## LR schedule and concept behind it

## Adam vs SGD
