# Implementing Logistic Regression in C++

This repository is for educational purpose to make it simple to grasp and understand the basic concepts of machine learning and deep learning.

Although python is an accepted industry standard and well suited for production purpose, but to get a good grasp and overview of how things work behind the hood, one needs to know and understand the basic operation of how things work.

This repository aims at providing such sort of knowledge about neural networks with the help of logistic regression.

To maintain the simplicity, we'll be using a simple neural network with 4 input neurons and one output neuron. Moreover for ease and to keep things comprehensible, the output classes of the Iris dataset have been reduced to 2 from 3.

## Points to remember

* This is the most basic model, with no hidden layers. In real life scenario, you can have multiple hidden layers
* This model does not use a test set for simplicity purposes. You can however split the training set into training and test set too
* The dataset used is available on kaggle and has 3 classes but we'll be using only 2 of those, *again for simplicity purposes*

## Pre-requisites

* A basic knowledge and overview of logistic regression **[Overview of Logistic Regression](https://towardsdatascience.com/logistic-regression-the-basics-b1716661c71b "Basics of Logistic Regression")**
* You must be familiar with neural networks a bit **[Overview of Neural network](https://towardsdatascience.com/a-gentle-introduction-to-neural-networks-series-part-1-2b90b87795bc "Basics of Neural networks")**

## Overview of the code

First things first, the code has a few global variables,

| Global Variable       | Purpose                                                                                                                                |
|:---------------------:|:--------------------------------------------------------------------------------------------------------------------------------------:|
| weight vector         | This vector is used to store the weights. It is initialized with random values that would later be adjusted in training phase          |
| Learning rate         | Or better known as alpha. It is used to decide how big or small each adjustment would be in accordance with the gradient descent       |
| Epoch                 | It is the number of times the algorithm must go through the entire dataset while training. In our case 9th epoch yeilded 100% accuracy |
| e                     | It is the logarithmic *e* whose value will be used later in activation function                                                        |
| InputValues vector    | This vector will store all the different input values read from the dataset and to be used in training phase                           |
| ExpectedOutput vector | This vector will store all the actual outputs that our model will aim to achieve during the training phase                             |

(https://github.com/anirudhdggl/logistic-regression-cpp/blob/master/docs/images/Global%20variables.png)

The functions, *other than main function*, that we'll be using in this code are

| Function name      | Description                                                                                           |
|:------------------:|:-----------------------------------------------------------------------------------------------------:|
|activation()        | This the activation function. It basically is the sigmoid function, 1 / (1 + e ^ (-z))                |
|updateWeight()      | This function is responsible for updating the weights during the training phase                       |
|calculateAccuracy() | This function is used to calculate the accuracy of our model on the training data itself              |
|test()              | At the end if you wish to predict some output using this model, this test function can be used for it |

(https://github.com/anirudhdggl/logistic-regression-cpp/blob/master/docs/images/functionsInvolved.png)

## Working of the model

The **main()** function will begin it's execution by reading the dataset into the respective vectors. Once done, it will go on to run training step epoch number of times.

(https://github.com/anirudhdggl/logistic-regression-cpp/blob/master/docs/images/epoch.png)

For each step, or epoch, it will calculate the value of *z*, or the aggregate input for the next layer and passes it to the **activation()** function.

(https://github.com/anirudhdggl/logistic-regression-cpp/blob/master/docs/images/activationFunction.png)

*z* is calculated as the sum of products of all the inputs with their respective weights, i.e., product of *input[i]* and *weight[i]* and then adding all of those products together.

Activation function then predicts the value using the sigmoid function.

After the prediction, all the weights are updated accordingly.

(https://github.com/anirudhdggl/logistic-regression-cpp/blob/master/docs/images/updateWeight.png)

In each epoch we predict the *present* accuracy of the model, to analyze later how well the model is performing. It basically gives us 100% accuracy in the 9th epoch.

Once all of the epochs are done, we then can test the model using our test function.

**Note:** *All the predicted values are rounded up to give us either class 0 or class 1*

(https://github.com/anirudhdggl/logistic-regression-cpp/blob/master/docs/images/roundOff.png)

## How to run the code

**For windows**

If you are using windows, simply clone or download the repo into your system using the green button.

(https://github.com/anirudhdggl/logistic-regression-cpp/blob/master/docs/images/cloneButton.png)

Once done you can then use **[VSCode's developer console](https://docs.microsoft.com/en-us/cpp/build/walkthrough-compiling-a-native-cpp-program-on-the-command-line?view=vs-2019 "Run C++ Code in windows")**

Once there, you need to run

`cl /EHsc logistic.cpp`

This will create an *.obj* and a *.exe* file for you. Next to run the compiled exe file, simply type

`logistic`

and hit enter. And **kaboom!!** It works

**For UNIX based systems**

If you are using any linux system, then it is as simply as opening the console and running a few commands.

First you must clone the code using

`git clone https://github.com/anirudhdggl/logistic-regression-cpp`

You may install git if required. Then navigate to the folder that is created for storing the repo and run 

`g++ logistic.cpp -o logistic.o
./logistic.o`

This should work fine but still if run into some issues just make sure that you have g++ installed and executable permissions set to *.o* files. Although I don't think any such issue would ever arise.

> If you find any improvement you can make, you are welcome to do so and for any issues and queries you can straight away mail me.