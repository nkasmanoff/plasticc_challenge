Contained in this repo is my attempt at the LSST's plasticc challenge, where a given data set of the photometry of many different objects are meant to be characterized according to their time dependent flux in various filters, position in the sky, and more into one of 15 possible categories. Further information about the challenge is available here: https://www.kaggle.com/c/PLAsTiCC-2018 . 

My aim in doing this challenge is to get a taste for what sorts of tasks astronomers face when scaling up their research to the challenges of the LSST (the testing dataset is far larger than the training one!), and dealing with many complicating factors for characterizing transients in LSST images. I've already had my hand in LSST data before, where I attempted to look at an example survey image, and characterize individual objects based on features, in the hopes of distinguishing stars and galaxies. This task mainly revolved around the implementation of unsupervised learning techniques in order to create separate areas in the data with moderate results, where this challenge is far more involved. 

Current work is housed in the "workspace" section, while the current data being worked on is in the aptly named "data" folder. 


More updates to come!


Brainstormed approach:

The current structure of the datasets has a metadata section, which provides the position, distance, and redshift of the various sources. The other section contains the flux in each of the filters for the same objects, liked by the "object_id" column. 


My first hypothesis to create a baseline of sorts, is to test a simple model based on the location and distances of these objects, and see if this provides any sort of preliminary information about the nature of the object. While definitely not the best approach, one such merit to this is that I recognize quasars and active galaxies, objects who can potentially flare up and create transient events, will be typically located further away. Perhaps this indicator will provide a purpose in a first runthrough of the data. 
