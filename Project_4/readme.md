
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


## How many layers

## MaxPooling

## Receptive Field

## SoftMax

## Learning Rate

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
