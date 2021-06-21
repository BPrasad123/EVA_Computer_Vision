
# Assignment:

1. First Part:
   1. Refer to the GRADCAM code we wrote (Links to an external site.)
   2. Build GradCAM images for the one layer before the one we used, and one layer before this one. Show the results.
   3. Load this [image](https://media.karousell.com/media/photos/products/2018/08/20/16_scale_tony_stark_avenger3_headscrupt_with_glasses_1534759826_e79b0cf4.jpg)
   4. "Find"  "sunglasses" in the image using GradCAM
2. Second Part:
   1. Refer to this paper: https://arxiv.org/pdf/1701.03056.pdf (Links to an external site.)
   2. Go to page 21, table 7
   3. The Receptive field increases from 29 to 45.
   4. Explain this increase
   

Submit both parts in a single file. 
 

Notes for this week:

ImageNet Data Preparation
Each RGB image is processed by resizing the smallest dimension to 256px, cropping the center 256x256 region, subtracting the per-pixel mean (across all images) and then using 10 different sub-crops of size 224x224 (corners + center with(out) horizontal flips). SGD with a batch size of 128 (or more), learning rate 10-2 in conjunction with a momentum term of 0.9
