# DLHumanDetection
This is the final project for VU Deep Learning

The goal of the project is to train a human detector that can detect human in images. 
This project uses INRIA Person Dataset, which contains 2416 positive images, 1218 negative images in the training set, 1132 positive images and 453 negative images in the testing set.

The positive images have already be cropped, containing a human image with height larger than 100 pixels, and negative images are in various size without any human images in them. 

The method to sample positive images is to take central 60*120 pixels. The method to sample negative images is to take a random number and sample a 60*120 window in any valid space in the negative images, in order to increase the sample space of negative images.

Method:  
Negative images will be randomly sampled 10 times in order to make full use of HD images  
Positive images will be only sampled once to learn the features of human figures  

    Aim 1:
        Achieve high accuracy in testing set

    Aim 2:
        Create zoom in/zoom out algorithm along with crop to analyze images at any resolution.  
        Shrink 1.5x a time until original image just larger than 64*128.  
        Memorize shrink ratio.  
        Analyze image N by shifting window 16 pixel(horizontal）， 32 pixel(vertical) a time.  
        Enlarge image N 1.5 times. Analyzing 1.5x N with same shifting mechanism.  
        Enlarge image N 2.25 times, Analyzing 2.5x N with same shifting mechanism.  
        Return result using AND/OR all subresults  
    
    Aim 3:
        Highlight area where there might be human.  
        Depending on the algirhtm's effectiveness, use one of the following:  
            Directly output highest resolution subimages  
            Output image with highest rating/with rating above threshold.  
            With each resolution layer, memorize and group true images (above rating *)  
            Output hightst resolution subimage group combined (through edge vertices) 
    
    

## Plan  
17/4/2019: Readin images, select window  
18/4/2019: Setup model  
...