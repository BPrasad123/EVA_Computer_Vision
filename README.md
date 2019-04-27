# Assignment 1B
## Karnel
In convolution, the filter matrix operating on the image matrix is called Kernel. Depending on what features to be extracted, pixel values in the matrix are decided. In general, size of kernel is less than that of image matrix, hence the kernel strides across the entire image to capture features. A particular kernel extracts similar features from whichever image it is applied on. It is also called as feature extractor, filter and 3x3 matrix in convolution.  
  
![alt](https://i.ibb.co/Tv2skXm/Edge-Detection-1.png)  

## Channel  
Imagine a channel as a bucket that contains only similar features coming from a kernel. For an example, consider an image being convoluted with a veritical edge detector kernel. The set of all the vertical features coming from that kernel is called as a channel.  


## Why we use 3x3 kernel only
There are two primary reasons for which we use only 3x3 kernels. One is reduced number of weight parameters and the other one being higher number of layers in the network. With less number of weights the network becomes computationally efficient while the increased number of layers enables the network to learn more complex feature in the data.  
  
Mathematically, applying a 3x3 kernel twice on an image produces the same output as applying a 5x5 kernel once. However, the here are the key differences that make 3x3 more preferred choice:  
  
Convolution with 3x3 kernel two times results in 18 parameters (3x3 + 3x3) and 2 layers.  
Convolution with 5x5 kernel once reults in 25 parameters (5x5) and 1 layer.

## 199x199 image to 1x1 with convolution
With each convolution with 3x3, the spatial dimension of the image gets reduced by 2, with an assumption that the stride is one. Hence to reduce spatial size of image (m x m) to (1 x 1) we need to apply 3x3 convolution m/2 times. The calculation below demonstrates how the size changes at each layer.  
  
layer 0: 199 x 199  
layer 1: conv 3 x 3 => 197 x 197  
layer 2: conv 3 x 3 => 195 x 195  
layer 3: conv 3 x 3 => 193 x 193  
layer 4: conv 3 x 3 => 191 x 191  
layer 5: conv 3 x 3 => 189 x 189  
layer 6: conv 3 x 3 => 187 x 187  
layer 7: conv 3 x 3 => 185 x 185  
layer 8: conv 3 x 3 => 183 x 183  
layer 9: conv 3 x 3 => 181 x 181  
layer 10: conv 3 x 3 => 179 x 179  
layer 11: conv 3 x 3 => 177 x 177  
layer 12: conv 3 x 3 => 175 x 175  
layer 13: conv 3 x 3 => 173 x 173  
layer 14: conv 3 x 3 => 171 x 171  
layer 15: conv 3 x 3 => 169 x 169  
layer 16: conv 3 x 3 => 167 x 167  
layer 17: conv 3 x 3 => 165 x 165  
layer 18: conv 3 x 3 => 163 x 163  
layer 19: conv 3 x 3 => 161 x 161  
layer 20: conv 3 x 3 => 159 x 159  
layer 21: conv 3 x 3 => 157 x 157  
layer 22: conv 3 x 3 => 155 x 155  
layer 23: conv 3 x 3 => 153 x 153  
layer 24: conv 3 x 3 => 151 x 151  
layer 25: conv 3 x 3 => 149 x 149  
layer 26: conv 3 x 3 => 147 x 147  
layer 27: conv 3 x 3 => 145 x 145  
layer 28: conv 3 x 3 => 143 x 143  
layer 29: conv 3 x 3 => 141 x 141  
layer 30: conv 3 x 3 => 139 x 139  
layer 31: conv 3 x 3 => 137 x 137  
layer 32: conv 3 x 3 => 135 x 135  
layer 33: conv 3 x 3 => 133 x 133  
layer 34: conv 3 x 3 => 131 x 131  
layer 35: conv 3 x 3 => 129 x 129  
layer 36: conv 3 x 3 => 127 x 127  
layer 37: conv 3 x 3 => 125 x 125  
layer 38: conv 3 x 3 => 123 x 123  
layer 39: conv 3 x 3 => 121 x 121  
layer 40: conv 3 x 3 => 119 x 119  
layer 41: conv 3 x 3 => 117 x 117  
layer 42: conv 3 x 3 => 115 x 115  
layer 43: conv 3 x 3 => 113 x 113  
layer 44: conv 3 x 3 => 111 x 111  
layer 45: conv 3 x 3 => 109 x 109  
layer 46: conv 3 x 3 => 107 x 107  
layer 47: conv 3 x 3 => 105 x 105  
layer 48: conv 3 x 3 => 103 x 103  
layer 49: conv 3 x 3 => 101 x 101  
layer 50: conv 3 x 3 => 99 x 99  
layer 51: conv 3 x 3 => 97 x 97  
layer 52: conv 3 x 3 => 95 x 95  
layer 53: conv 3 x 3 => 93 x 93  
layer 54: conv 3 x 3 => 91 x 91  
layer 55: conv 3 x 3 => 89 x 89  
layer 56: conv 3 x 3 => 87 x 87  
layer 57: conv 3 x 3 => 85 x 85  
layer 58: conv 3 x 3 => 83 x 83  
layer 59: conv 3 x 3 => 81 x 81  
layer 60: conv 3 x 3 => 79 x 79  
layer 61: conv 3 x 3 => 77 x 77  
layer 62: conv 3 x 3 => 75 x 75  
layer 63: conv 3 x 3 => 73 x 73  
layer 64: conv 3 x 3 => 71 x 71  
layer 65: conv 3 x 3 => 69 x 69  
layer 66: conv 3 x 3 => 67 x 67  
layer 67: conv 3 x 3 => 65 x 65  
layer 68: conv 3 x 3 => 63 x 63  
layer 69: conv 3 x 3 => 61 x 61  
layer 70: conv 3 x 3 => 59 x 59  
layer 71: conv 3 x 3 => 57 x 57  
layer 72: conv 3 x 3 => 55 x 55  
layer 73: conv 3 x 3 => 53 x 53  
layer 74: conv 3 x 3 => 51 x 51  
layer 75: conv 3 x 3 => 49 x 49  
layer 76: conv 3 x 3 => 47 x 47  
layer 77: conv 3 x 3 => 45 x 45  
layer 78: conv 3 x 3 => 43 x 43  
layer 79: conv 3 x 3 => 41 x 41  
layer 80: conv 3 x 3 => 39 x 39  
layer 81: conv 3 x 3 => 37 x 37  
layer 82: conv 3 x 3 => 35 x 35  
layer 83: conv 3 x 3 => 33 x 33  
layer 84: conv 3 x 3 => 31 x 31  
layer 85: conv 3 x 3 => 29 x 29  
layer 86: conv 3 x 3 => 27 x 27  
layer 87: conv 3 x 3 => 25 x 25  
layer 88: conv 3 x 3 => 23 x 23  
layer 89: conv 3 x 3 => 21 x 21  
layer 90: conv 3 x 3 => 19 x 19  
layer 91: conv 3 x 3 => 17 x 17  
layer 92: conv 3 x 3 => 15 x 15  
layer 93: conv 3 x 3 => 13 x 13  
layer 94: conv 3 x 3 => 11 x 11  
layer 95: conv 3 x 3 => 9 x 9  
layer 96: conv 3 x 3 => 7 x 7  
layer 97: conv 3 x 3 => 5 x 5  
layer 98: conv 3 x 3 => 3 x 3  
layer 99: conv 3 x 3 => 1 x 1
