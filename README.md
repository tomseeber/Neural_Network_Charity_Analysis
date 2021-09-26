# Modeling Project Success for the Alphabet Soup Charity 

## Overview of the analysis
The purpose of this analysis is to predict which projects and charities would be successful through a machine learning model using a neural network.  We need to understand which data has an inpact to make better decisions.  The intermediate steps include data cleaning, pre-processing and model optimization.

## Deliverable 1: Setup ( contained with the Model with Setup)

[Set up for the model is in the original file for the model is in the un-optimized version of the model.](./AlphabetSoupCharity.ipynb)

## Deliverable 2:  Model with Setup

[The full unoptimized model for the charity analysis with no optimizations.](./AlphabetSoupCharity.ipynb)

## Deliverable 3:  Optimized Model

[Optimized Model with over 75% Accuracy](AlphabetSoupCharity_Optimized.ipynb)

## Deliverable 4: Summary and Notes

### Data Preprocessing

#### 1. What variable(s) are considered the target for your model?

The target is the "Is-Successful" column which answers whether or not the project was successful and the money use was effective.

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
 EIN (Employer identificaiton) was dropped because the numbers really are more like strings.  This would confuse the system.  Dropping Status cause all the values are 1

### Compiling, Training, and Evaluating the Model*

#### 1. How many neurons, layers, and and activation functions did you select for your neural network model, and why?

As per the instructions, we removed the names and EIN.  After many testing,  I put the name back into the model which boosted the accuracy, despite the instructions of the starting file.

Our model has 3 hidden nodes: with 100, 30, 10 

The first layer uses leaky_relu as activation, with the next two using Signmoid.

This Runs for only 100 Epochs, but realistically we could have set the epochs to 5 and get suffcient results.  By adding more neurons, I was able to get up to 90+ accuracy. 

All layers are dense and the Output layer has 1 output using Signoid.

#### 2. Were you able to achieve the target model performance?

Yes

#### 3. What steps did you take to try and increase model performance?

* Attempted to change the epoch to 200
* added two hidden layers, with 100, 30
* added synapses..100 for all hidden layers.
* Dropped the status column as its all 1, and would not help
* Changed the activation function from relu to leaky_relu on level one
* Changed the activation fuction fron signmond to leaky_relu on level three
* Added 4th layer of neurons
* Added Names back into the model
* Reduce names to only values over 5
* Reduced layers to 100, 30, 10   output 1
* Reduced Epochs to 100

### Summary: 

While the model achieved desired level of accuracy,  I had to struggle with the process.  Without the Name column, I was able to achieve 73%-74% accuracy each time with several different interations of the model.   I would liked to have left the name off of the categorical data list.  While we limited the NAME category to more then 5 entries, ultimately the column weights the model to include previously successful charities.  While we removed the success or not column from the training data, it would be fairer for new charities if we could model this without those components.

I ran a test model for XGBoost.  XGBoost is a boosting model that is generally considered a great model for classification.  The lead in to the model was basic with just hot-encoding and less focus on noisy columns.  Even then XGBoost was able to produce above the required accuracy with no real optimization.

[Unoptimized XGBoost] (xgboost.ipynb)

I was able to get Accuracy: 77.71% with far less data manupulation  for this data set. 