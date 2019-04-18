# DLHumanDetection
This is the final project for VU Deep Learning

The goal of the project is to train a human detector that can detect human in images. 
This project uses INRIA Person Dataset, which contains 2416 positive images, 1218 negative images in the training set, 1132 positive images and 453 negative images in the testing set.

The positive images have already be cropped, containing a human image with height larger than 100 pixels, and negative images are in various size without any human images in them. 

The method to sample positive images is to take central 60*120 pixels. The method to sample negative images is to take a random number and sample a 60*120 window in any valid space in the negative images, in order to increase the sample space of negative images.

## Plan  
17/4/2019: Readin images, select window  
18/4/2019: Setup model  
...