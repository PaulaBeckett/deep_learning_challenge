# Neural Network Report

## Overview of the Analysis

Using a dataset of over 34,000 records supplied by non-profit foundation Alphabet Soup create a binary classifier 
to predict the likelihood of success for future applicants if funded by Alphabet Soup.

## Results

### Data Preprocessing

Target variable identified 
   * IS_SUCCESSFUL, Was the money used effectively

Feature variables
   * APPLICATION_TYPE, Alphabet Soup application type
   * CLASSIFICATION, Government organisation classification
   * USE_CASE, Use case for funding
   * ORGANIZATION, Organisation type
   * STATUS, Active Status
   * INCOME_AMT, Income classification
   * SPECIAL_CONSIDERATIONS, Special considerations for application
   * ASK_AMT, Funding amount requested            

Removed the following variables due to them being for identifcation only
   * EIN
   * NAME

### Compiling, Training & Evaluating the Model

First model created with deep neural network features
   * first hidden layer with 80 hidden nodes, input dimensions equal to the number of rows in the training split & activation type 'relu'.
     <br/> 80 hidden nodes were choosen as it is approximately double the number of features
   * second hidden layer with 30 hidden nodes & activation type 'relu'.
     <br/> 30 hidden nodes were choosen to be at least half of the first layer, and less than the number of features
   * output layer with one node and activation type 'sigmoid'
     ![image](https://github.com/PaulaBeckett/deep_learning_challenge/assets/125642856/f5abcd4a-789c-4401-91b3-2656e720196d)

   * Training this first model through 100 epochs gave an accuacy of **0.7234** and a loss of 0.5634.
     <br/>This is below the target accuracy of 75% <br/>
     ![image](https://github.com/PaulaBeckett/deep_learning_challenge/assets/125642856/38cb1c18-3af3-466b-a2fd-45c4949d0c6a)

A few attempts were made to increase the target predictive accuracy above the requested 75%
   * Optimisation Attempt 1
       * A third hidden layer of 30 hidden nodes & activation type 'relu' was added
       * Epochs reduced to 50
         ![image](https://github.com/PaulaBeckett/deep_learning_challenge/assets/125642856/642cf03e-3882-47bb-8c2e-9f02e1a46995)

       * This saw a very small increase in accuracy to **0.7238** (increase of 0.0004)
         ![image](https://github.com/PaulaBeckett/deep_learning_challenge/assets/125642856/f0229abc-618d-4c03-8b10-73390b20490e)

   * Optimisation Attempt 2
       * First, second and third hidden layer outputs changed to 'tanh'
         ![image](https://github.com/PaulaBeckett/deep_learning_challenge/assets/125642856/73cb6724-fbc5-46f9-8b6d-70fb905ef486)

       * Again, this saw a very small increase in accuracy from the first optimisation attempt to **0.7245** <br/>
         (increase of 0.0011 from initial training model)<br/>
         ![image](https://github.com/PaulaBeckett/deep_learning_challenge/assets/125642856/4590207a-da1b-40ff-b170-f7e4a3abe433)
        
   * Optimisation Attempt 3
       * Hidden nodes in first, second and third layers reduced to 10, 5 & 2 to assess for possible overfitting of model
         ![image](https://github.com/PaulaBeckett/deep_learning_challenge/assets/125642856/59a20cbc-ddcc-4910-a816-c543669f5727)

       * This model was slightly less accurate than the first model at **0.7227** (decrease in accuracy of 0.0007)
         ![image](https://github.com/PaulaBeckett/deep_learning_challenge/assets/125642856/91e3f036-4595-4cdc-8617-e1df009c457c)

## Summary

In consultation with Alphabet Soup it would be reviewed if the predictive accuracy of 72.45% achieved in the tanh model (Optimsation Attempt 2) was high enough before proceding with the model.

To achieve greater accuracy from a model it would be recommended to run a hyperparameter tuner (such as Hyperband or Sklearn from Keras Tuner).<br/>
The Keras Tuner could help find the optimal parameters, such as number of layers and hidden nodes.

Another recommendation would be for the Alphabet Soup business team to perform some data clean up on INCOME_AMT if possible.

With a cleaner dataset and running a Keras Tuner I am confident that we could provide the team at Alphabet Soup with a predictive model with 
greater than 75% accuracy to aid them in the future application of successful funding.
