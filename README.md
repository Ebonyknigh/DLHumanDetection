# DLHumanDetection
This is the final project for VU Deep Learning

The goal of the project is to train a human detector that can detect human in images. 
This project uses INRIA Person Dataset, which contains 2416 positive images, 1218 negative images in the training set, 1132 positive images and 453 negative images in the testing set.

The positive images have already be cropped, containing a human image with height larger than 100 pixels, and negative images are in various size without any human images in them. 

The method to sample positive images is to take central 60x120 pixels. The method to sample negative images is to take a random number and sample a 60x120 window in any valid space in the negative images, in order to increase the sample space of negative images.

### Method  
Negative images will be sampled through moving window accross all regions.  
Positive images will be only sampled once to learn the features of human figures.  
Three different CNN models will be created and the final decision will be based on the vote by three models 
Three models are individually trained 15 iterations over INRIA Person dataset using minibatch SGD, and parameters of each iteration is recorded with validation accuracy rate.  
Parameters need to be selected from the record based on validation accuracy rate as reference, and be tested on DetectionTest, which uses entirely different dataset. Detection test may take more than 10GB of memory to validate through the whole testing dataset.  
Due to time and processing power limitation, the weights used in detector are the weights of last iteration of each model.  
If human is detected in the detector, the detected region will be boxed in original image and output the modified image.  

### Note
Due to the limitation of training dataset, which uses low res low noise images, and no vertical linear features are enphysized in negative examples, models trained on the dataset are effective at detecting people, but when dealing with pictures with strong vertical linear features, detector will tend to classify these features as people. I.e. grass in App/13.jpg, pole in App/18.jpg, and door frame in App/19.jpg