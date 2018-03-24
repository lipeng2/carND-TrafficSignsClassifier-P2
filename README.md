# Project Build Traffic Signs Classifiers
This repo contains codes and datasets needed to complete the Project 2 of Udacity Self-Driving Car Nanodegree. The program is designed to classifier German traffic signs with high degree of accuracy

## Overview
* The provided [German traffic sign dataset](http://benchmark.ini.rub.de/?section=gtsrb&subsection=dataset) contains 34799 training examples and 12530 test samples, including a total of 43 different types of traffic signs.

* The archtecture of the trained model is modified base on LeNet. detailed information about the model is documented in the model implementation [here](https://github.com/lipeng2/CarND-TrafficSignsClassifier-P2/blob/master/CarND-Traffic-Sign-Classifier-Project/Traffic_Sign_Classifier.ipynb)

* The best result achieved by our model is 97.3% accuracy on the test dataset provided. The model is trained using adam optimizer, with learning rate of 0.0001, epochs of 50, batch size of 128, and dropout rate of 0.2.

## Data exploration
By visualizing the distribution of the training data shown below, we can see that the data set is highly skewed. For example class 0, 19, 27, 37 have signficantly less data than other classes. Therefore, it is necessary to deploy date augmentation to address this problem. Additionally, during our initial training, our model often overfits the data just after serveral epochs due to its complexity, and we discovered that using data augmentation can be tremendously useful in address the issue of overfitting as well.

<img src='visual summary/distribution.png' height="500" width="800"/>

Below is a snapshot of visualization of the training data. A more detailed visualization is included in the notebook.

<img src='visual summary/sample visualization.png' height="500" width="600"/>

## Approach for finding our solution

### Pretraining
* Augment dataset by applying random rotation from -20 degrees to 20 degrees, generates more data to address problems such as overfitting and data skewness
* Convert data into grayscale, helps reduce computational expense
* Normalized the data obtained from the previous steps, enable faster computation and enhance generalization of the model

### Model Training
1. The first model we used is the LeNet model from the LeNet lab assignment. Without any modification, we just plug in data and train. Despite our efforts in experimenting different hyperparameters, the model yields similar accuracy, which is around 89%, on validation dataset every time. Therefore, we can conclude that the model is not complex enough to explain the data. 

2. We continue to use LeNet architecture for our model. However, we decide to greatly increase the depth of each convolution layers in the model hoping to obtain a model that is complex enough to capture all the information provided by the dataset. Not surprisingly, we are able to obtain a much better accuracy, which is around 93%, on validation dataset. However, the model raises another problem. Just after couple epochs, our model has 100% accuracy on the training data, which means that the model is overfitting the train and not generalizing well on test data. So we decided to use dropout technique to reduce overfitting.

3. Finally, we add two dropout layers with keep_prob of 0.5 in our previous model, and in just 10 epochs of training without tuning any other hyperparameters, the model can consistently achieve an accuracy of around 95% on validation dataset. And after experimenting of numerous combinations of hyperparameters, we find our best result using learning rate of 0.0001, dropout rate of 0.2, opochs of 50, batch size of 128.

4. Below is the result we obtained, and it includes accuracy comparison and a plot showing the distribution of incorrected labeled classes
<img src='visual summary/test results and analysis.png' height="500" width="800"/>

## Suggestion on improvment
As we can see from the above figure, the gap between training accuracy and validation accuracy is still significant compares to the gap between validation and test. This can indicates that a more complex model architecture should be used instead of LeNet in order to gain a better classifier. Potential and promising architectures will be VGG16 ResNet50. 
