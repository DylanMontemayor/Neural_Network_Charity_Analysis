# Neural_Network_Charity_Analysis

## Overview of the Module 19 Challenge

Alphabet Soup foundation invests in charitable organizations but not all are successful (the organization uses the money correctly and shows progress or results). With the information on the past year's investments, a neural network model will be developed to predict which applications have a higher probability to be successful. The objective is for Alphabet Soup to invest wisely. The CSV provided has more than 34,000 organizations with 12 variables. 

### Files and Folders

First model files: AlphabetSoupCharity.ipynb, AlphabetSoupCharity.h5

Optimization model files: AlphabetSoupCharity_Optimzation.ipynb, AlphabetSoupCharity_Optimization.h5

Trials models (neural network and random forest): AlphabetSoupCharity_Trials.ipynb

Resources: images

## Results

### Data Preprocessing

- What variable(s) are considered the target(s) for your model?

Since we want to be able to predict if an investment will be successful, we will use that column as our y variable. The column name is "IS_SUCCESSFUL".

!['1'](https://github.com/DylanMontemayor/Neural_Network_Charity_Analysis/blob/main/Resources/1.png)

- What variable(s) are considered to be the features of your model?

For defining the final features, the preprocessing step was key. We reviewed their amount of unique values and distribution to accommodate or bucket the data for the model. Finally, we applied OneHotEcnoder for transforming all the categorical data into numeric. After dropping some of them, the final model ended with the next variables: 

"NAME", "APPLICATION_TYPE", "AFFILIATION", "CLASSIFICATION", "ORGANIZATION", "INCOME_AMT"

!['2'](https://github.com/DylanMontemayor/Neural_Network_Charity_Analysis/blob/main/Resources/2.png)

- What variable(s) are neither targets nor features, and should be removed from the input data?

EIN is a feature that is playing the role of key value. We delete it since key values won't bring anything to our model. 

For the next features, we counted their values and reviewed their density. We noticed that many of them weren't having a real impact on the model (deleting or adding them neither improved nor affected the final results). 

ASK_AMT, SPECIAL_CONSIDERATIONS, STATUS, USE_CAS

!['3'](https://github.com/DylanMontemayor/Neural_Network_Charity_Analysis/blob/main/Resources/3.png)

### Compiling, Training, and Evaluating the Model

- How many neurons, layers, and activation functions did you select for your neural network model, and why?

Neurons - Since our data isn't exactly linear, we used more than one neuron. We decided to keep 80 neurons in the first hidden layer and 30 in the second after seeing that increasing the number of neurons would require model computational resources and it wasn't adding any value to the model.

Layers - We decided to keep two hidden layers because we increased the number of features by converting them into numeric data. Additionally, we tried the model with three layers and the performance was almost the same as with two.  

Activation functions - We kept ReLU for our two models because of the nature of the data and because it is one of the best options for positive nonlinear input data for classification. We didn't have negative values and our data is not linear. 

Epochs - We reduced from 100 to 50, since from that number the accuracy or the loss remains within the same range. 

!['4'](https://github.com/DylanMontemayor/Neural_Network_Charity_Analysis/blob/main/Resources/4.png)

- Were you able to achieve the target model performance?

We were able to achieve a model performance of **over 0.79** (accuracy) within the preprocessing step. 

!['5']()

In addition, we evaluated the data with a random forest (n_estimators=128, random_state = 78) and we got the same result. Random forest predictive accuracy = 0.792

[See the "AlphabetSoupCharity_Trials", line 24]

!['7'](https://github.com/DylanMontemayor/Neural_Network_Charity_Analysis/blob/main/Resources/7.png) 

- What steps did you take to try and increase the model performance?

After several trials of changing the neural network model (the layers, neurons, and activation functions), we noticed that the model wasn't improving almost anything. So, we went one step before analyzing each of our X features. Before deleting anything, we analyzed the unique values in each variable. In that step, we realized that the name was an identification column but not a key value, therefore, it wasn't necessary to delete it. 

!['6'](https://github.com/DylanMontemayor/Neural_Network_Charity_Analysis/blob/main/Resources/6.png)

### Summary

Overall, we achieved an accuracy of over 0.79, which was above our target. The most important step for getting the final result was preprocessing. If we didn't take extra care of the data that was entering our model, it didn't matter how much we tried to improve it with more resources (neurons, layers, and functions). Finally, in the last trials, we used a random forest model to predict the same target and it threw almost the same result (over 0.92 in). In this case, **the recommendation would be to use random forest for the predictions since it took less code (around 12 fewer lines), computational resources, and time.**   
