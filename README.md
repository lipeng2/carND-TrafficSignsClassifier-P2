# Project Build Traffic Signs Classifiers
This repo contains codes and datasets needed to complete the Project 2 of Udacity Self-Driving Car Nanodegree. The program is designed to classifier German traffic signs with high degree of accuracy

## Overview
* The provided [German traffic sign dataset](http://benchmark.ini.rub.de/?section=gtsrb&subsection=dataset) contains 34799 training examples and 12530 test samples, including a total of 43 different types of traffic signs.

* The archtecture of the trained model is modified base on LeNet. detailed information about the model is documented in the model implementation [here](https://github.com/lipeng2/CarND-TrafficSignsClassifier-P2/blob/master/CarND-Traffic-Sign-Classifier-Project/Traffic_Sign_Classifier.ipynb)

* The best result achieved by our model is 97.3% accuracy on the test dataset provided. The model is trained using adam optimizer, with learning rate of 0.0001, epochs of 50, batch size of 128, and dropout rate of 0.2.

