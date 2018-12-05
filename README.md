Contained in this repo is my attempt at the LSST's plasticc challenge, where a given data set of the photometry of many different objects are meant to be characterized according to their time dependent flux in various filters, position in the sky, and more into one of 15 possible categories. Further information about the challenge is available here: https://www.kaggle.com/c/PLAsTiCC-2018 . 


To save some time to someone interested in this, I achieved a competition score of ~1.26, which is in the top 50% (basically the only positive way to spin that score :)).  

My aim in doing this challenge is to get a taste for what sorts of tasks astronomers face when scaling up their research to the challenges of the LSST (the testing dataset is far larger than the training one!), and dealing with many complicating factors for characterizing transients in LSST images. I've already had my hand in LSST data before, where I attempted to look at an example survey image, and characterize individual objects based on features, in the hopes of distinguishing stars and galaxies. This task mainly revolved around the implementation of unsupervised learning techniques in order to create separate areas in the data with moderate results, where this challenge is far more involved. 

Current work is housed in the "workspace" section, while the current data being worked on is in the aptly named "data" folder. 



Approach
--------

While there are dozens if not hundreds of different potential ways to create a classifier and what features to use, I ended up following along from a popular kernel on the site (https://www.kaggle.com/meaninglesslives/simple-neural-net-for-time-series-classification). 

However, I diverged from this model by using different features. Rather than summarize all passband features into one, I consider each passband individually, and calculate the population statistics for these separately. These population characteristics are then used as features, and include things such as mean, variance, skew, diff2, diff/mean, and so on. Further description of all these are located in the notebook used. 



Fair Warning
------------

The test data is far larger than I can handle on my laptop, as it is a 19GB spreadsheet. As a result I did this testing stuff on the server hosted by kaggle. Regardless, the notebook here is the same one as the one used there. 

The plots generated are the ones used on the training of the model on the training data, which only includes 14 possible classes, while the testing data is injected with a 15th source. 

The method by which I determined the probability of the last class (exclusive to testing data) is that it is the probability of that the object being predicted is "not" one of the other ones. The model uses the "predict_proba" action which outputs a probability between 0 and 1, and the probability of it not belonging to the already predicted class will be 1- that #. The 15th class will be the product of all these uncertainties. 


Results
-------


First, is a graph of one such model's training loss and accuracy with validation data parallel to it. 



Results
-------


This plot is the correlation between all of the relevant statistics averaged over n games to the current game, as a function of n. 

<center>

![Project](https://github.com/nkasmanoff/plasticc_challenge/blob/master/modelloss.png)


</center>

<center>

![Project](https://github.com/nkasmanoff/plasticc_challenge/blob/master/modelacc.png)


</center>



Additionally, a confusion matrix of the predicted classes. 


<center>

![Project](https://github.com/nkasmanoff/plasticc_challenge/blob/master/conmat.png)


</center>




