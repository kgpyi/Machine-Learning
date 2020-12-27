# Optimizing an ML Pipeline in Azure

## Overview
This project is part of the Udacity Azure ML Nanodegree.
In this project, we build and optimize an Azure ML pipeline using the Python SDK and a provided Scikit-learn model.
This model is then compared to an Azure AutoML run.

## Summary
The dataset is about bank marketing, which has 32950 rows and 21 columns - age,job,marital,education,default,housing,loan,contact,month,day_of_week,duration,campaign,pdays,previous,poutcome,emp.var.rate,cons.price.idx,cons.conf.idx,euribor3m,nr.employed and y

Our target column name is "y" in which entries are - 'yes' and 'no'. Hence we can use binary Logistic Regression. This is a highly imbalanced dataset, as out of 32950: the number of rows with 'no' is 29258 and the number of rows with 'yes' is 3692.

We received the best accuracy with AutoML which used VotingEnsemble
and obtained an accuracy of 0.9166 

## Scikit-learn Pipeline
SKLearn model followed these steps: 

First, we load the dataset to be used from the URL provided, then we clean the dataset using a python script which did one-hot encoding, and split the dataset into train and test sets. Our script itself had a Logistic Regression model implemented using SKlearn which did calculate the accuracy. 
We used Hyperdrive to tune Hyperparameters and save them for later use. The Bandit Policy for early termination was used which terminated our model when any run that doesn't fall within the slack factor or slack amount (slack factor = 0.1 was taken) of the evaluation metric concerning the best performing run will be terminated.

## AutoML
30 iterations were done in 30 min by AutoML and out of them, VotingEnsemble gave the best accuracy which was 0.9166, and the time it took AutoML to apply this algorithm was 1 minute and 11 seconds, also f1_score_weighted was 0.9134728804140997 and log_loss was 0.21040595562533215 which is quite good work.

## Pipeline comparison
The accuracy given by Scikit-learn Pipeline was 0.9104 and the one which was given by AutoML was 0.9166 which not much of a difference, considering the amount of time AutoML took was 34 min while Scikit-learn Pipeline run took 2 min and 49 seconds. But at the same time, the individual time that was taken VotingEnsemble classifier was less than SKLearn. 

It can also be noted that AutoML was able to tell us about the whole more details, but on the other hand, we did calculate the accuracy of SKLearn model. Early termination by using Bandit policy would have decreased the accuracy, and also data was highly imbalanced so our basic Logistic Regression was biased as well which used max iterations of 150 and Regularization Strength of 0.1 whereas AutoML does the normalization itself and n_cross_validations=8 is helpful to stabilize the process which reduces the bias. 

## Future work
We can use feature engineering and reduce the imbalance of the dataset which was not at all addressed. Instead of accuracy, the base can be a better metric is like F1 score or something like that to make things more clear. 

 Also, we can make changes to the HyperDrive policy so that it runs for more time and surely it can come at par with AutoML. It will be a nice find, classic coding versus no coding (less coding if using SDK) 


## Proof of cluster clean up
![alt text](http://https://github.com/kgpyi/Machine-Learning/blob/master/Udacity/Machine%20Learning%20Engineer%20with%20Microsoft%20Azure%20Nanodegree%20Program/Optimizing%20an%20ML%20Pipeline%20in%20Azure/deleteComputeInstance.png/to/img.png)
