
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
Famously called as "Antman", it is pretty effective when there is a need to increase or decrease number of channels without doing convolution and hence computationally effective. In most of the cases it used to reduce number of channels unless there is a specific need to increase. While reducing the number of channels 1x1 enables to model to combine the channels to come up with most dominant ones.

## Kernels and how do we decide the number of kernels?
Kernels are feature extractors, like vertical and horizental edge detectors. Depending the upon the values and their corresponding positions in the kernel matrix, relevant features are extracted from the input image. During backpropagation the model determines the values of kernels so as to extract dominant features. Although there is no specific rule to provide exact number of kernels required for a particular dataset, however the rule of thumb is to add more number kernels if the images are complex to classify.

## Batch Normalization
Within a network, output from a layer becomes the input for the next layer. A change in the distribution of such input, coming from activations from previous layer, results in inappropriate updates in the weights. A batch normalization makes the input a stable distribution that in turn results in accelarated learning of the network.

## Position of MaxPooling
Max Pooling reduces the spatial dimension by half. Hence it is a good approach to apply max pooling at least after 4-6 initial convolution layers so that the model learns better patterns. 

## Concept of Transition Layers
Transition layer is also called as bottleneck layers. The idea is to gradually increase the number of channels within each block and reduce it before the start of the next block. This enables the network to combine and retain only dominant channels at each block resulting in better accuracy.

## Position of Transition Layer
The transition layer is put just before the max pooling at each block. This ensures at lease dominant channels are selected before lossing some spatial information through max pooling.

## The distance of MaxPooling from Prediction
Max pooling should not be applied towards the end of the network. It should be followed by at least a few convolution layers before prediction.

## The distance of Batch Normalization from Prediction
Batch normalization should not be present after the last convolution layer. The idea is to retain the activation outputs as those are so that they can be very well separated/differenciated by softmax layer.

## DropOut
Adding dropout layer initializes some of the weights with zero randomly. This in turn makes the network more generalized resulting in reduced training accuracy. However during the prediction all of the neurons are active hence that results in better test accuracy.

## When do we introduce DropOut, or when do we know we have some overfitting
When training accuracy is pretty high and validation accuracy is low and no more improving with further epochs, we can introduce dropout.

## When do we stop convolutions and go ahead with a larger kernel or some other alternative (which we have not yet covered)
This is purely a guess. I think when we not so focused on the local spatial features rather a general view of the objects in the images for detection purpose.

## When to add validation checks
It is a good practice to add during the training itself to see how the model is converging.

## LR schedule and concept behind it
Reducing learning rate during the training process leads to better performance and reduced training time. The idea is to take smaller gradient steps as the model approaches the local minima. It is called as learning rate annealing as well and LR schedule is one of the approches. We can either keep updating the learning rate with number of epochs or we can change it after a certain number of epochs periodically. 

## Adam vs SGD
Adam use a combination of squared grandient of RMSProp and weighted average of gradients. It leverages adaprive learning rate to find individual learning rate for each parameter.  

SGD is a variant of gradient descent that updates the weights after each batch.  

There are two metrics to decide the efficacy of an optimizer: Speed of convergence and regularization for better accuracy. Adam is faster than SGD for convergence however SGD is better than Adam for when it comes to regularization.
