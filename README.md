# Modeling Project Success for the Alphabet Soup Charity 

## Overview of the analysis
The purpose of this analysis is to predict which projects and charities would be successful through a machine-learning model using a neural network.  We need to understand which data has an impact to make better decisions.  The intermediate steps include data cleaning, pre-processing and manual model optimization (without using Keras Tuner).

## Deliverable 1: Setup ( contained with the Model with Setup)

* [The full unoptimized model for the charity analysis with no optimizations in Jupyter file](./AlphabetSoupCharity.ipynb)
* [HD5 file of Model](./AlphabetSoupCharity.h5)

## Deliverable 2:  Model with Setup

* [The full unoptimized model for the charity analysis with no optimizations in Jupyter file](./AlphabetSoupCharity.ipynb)
* [HD5 file of Model](./AlphabetSoupCharity.h5)

## Deliverable 3:  Optimized Model

* [Optimized Model with over 75% Accuracy](AlphabetSoupCharity_Optimized.ipynb)
* [HD5 file of Model](./AlphabetSoupCharity.h5)

## Deliverable 4: Summary and Notes

### Data Preprocessing

#### 1. What variable(s) are considered the target for your model?

The target is the "Is-Successful" column which answers whether or not the project was successful and the spenditure was effective.

#### 2. What variable(s) are considered to be the features for your model?

The features of this model are the 

* NAME
* APPLICATION
* TYPE
* AFFILIATION
* CLASSIFICATION
* USE_CASE
* ORGANIZATION
* INCOME_AMT
* SPECIAL_CONSIDERATIONS
* STATUS
* ASK_AMT

#### 3. What variable(s) are neither and should be removed from the input data? 
 EIN (Employer identification) was dropped because the numbers are more like strings.  This would confuse the system.  Dropping Status cause all the values are 1

### Compiling, Training, and Evaluating the Model

#### 1. How many neurons, layers, and and activation functions did you select for your neural network model, and why?

We removed the names and EIN.  After testing,  I put the name back into the model which boosted the accuracy.

Our model has 3 hidden nodes: with 100, 30, 10 

The first layer uses leaky_relu as activation, with the next two using Signmoid.

This Runs for only 100 Epochs, but realistically we could have set the epochs to 5 and get suffcient results.  By adding more neurons, I was able to get up to 90+ accuracy. 

All layers are dense and the Output layer has 1 output using Signoid.

#### 2. Were you able to achieve the target model performance of 75%?

Yes

#### 3. What steps did you take to try and increase model performance?

* Attempted to change the epoch to 200
* added two hidden layers, with 100, 30
* added synapses..100 for all hidden layers.
* Dropped the status column as its all 1, and would not help
* Changed the activation function from relu to leaky_relu on level one
* Changed the activation function from sigmoid to leaky_relu on level three
* Added 4th layer of neurons
* Added Names back into the model
* Reduce names to only values over 5
* Reduced layers to 100, 30, 10   output 1
* Reduced Epochs to 100

### Summary: 

While the model achieved the desired level of accuracy (75%),  I had to struggle with the process.  Without the Name column, I was able to achieve 73%-74% accuracy each time with several different iterations of the model. I would liked to have left the name off of the categorical data list.  While we limited the NAME category to more than 5 entries, ultimately the column weights the model to include previously successful charities. Unfortunately, this was the most heavily weighted feature meaning the model biased toward previously successful charities. The analysis would be fairer for new charities if we could model this without those components.

I ran a test model for XGBoost.  XGBoost is a boosting model that is generally considered a great model for classification.  The lead into the model was basic with just hot-encoding and less focus on noisy columns.  Even then XGBoost was able to produce above the required accuracy with no real optimization.

[Unoptimized XGBoost for Alphabet Soup Charity](./xgboost.ipynb)

I was able to get Accuracy: 77.71% with far less data manipulation for this data set. 