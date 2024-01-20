# Module 12 Report Template

## Overview of the Analysis

In this section, describe the analysis you completed for the machine learning models used in this Challenge. This might include:

* Explain the purpose of the analysis.
The purpose of this analysis is to help predict high-risk loans, thereby reducing overall risk and allowing stakeholders to better allocate resources to managing high-risk accounts.

* Explain what financial information the data was on, and what you needed to predict.
The financial information includes data on loan size, interest rate, borrower income, debt to income ratio, total lines of credit, derogatory remarks - which would include delinquencies, collections, payment punctuality etc. - total debt, and loan status - being either 0 for health or 1 for high-risk. 

We needed to predict if an account would have a loan_status of 1, or high-risk, given other variables. 

* Provide basic information about the variables you were trying to predict (e.g., `value_counts`).

Given that we're trying to predict loan_status it's value count is:

loan_status
0    75036
1     2500

We can see there is a high imbalance. Only 2500 of our accounts have the high-risk value we're looking to predict.


* Describe the stages of the machine learning process you went through as part of this analysis.

Initially we perform a logistic regression on the imbalanced dataset. We split the target value of loan_status to our y value and the rest of the data set to x.

This provides resonably good recall with predicting high-risk accounts.

At this point we address the imbalance in the dataset by using RandomOverSample to create randomly distributed duplicates of the y samples to bring their value count in line with the rest of the dataset.


* Briefly touch on any methods you used (e.g., `LogisticRegression`, or any resampling method).

We assigned a random_state of 1 in our Logistic Regression model to ensure that the model always uses the same random seed when re-running our model.

## Results

Using bulleted lists, describe the balanced accuracy scores and the precision and recall scores of all machine learning models.

* Machine Learning Model 1:
  * Description of Model 1 Accuracy, Precision, and Recall scores.
Accuracy - 99%
Precision - 0 = 100%, 1 = 84%
Recall - 0 = 99%, 1 = 94%

The precision of 84% indicates that 84% of the predicted high-risk loan are actaully high-risk.

The recall of 94% indicates that it accurately identifies 94% of all high-risk loans. 

Given the dataset, Recall is the most important value we want to acheive. Making sure all high-risk accounts are accurately flagged is the goal.


* Machine Learning Model 2:
  * Description of Model 2 Accuracy, Precision, and Recall scores.
Accuracy - 99%
Precision - 0 = 100%, 1 = 84%
Recall - 0 = 99%, 1 = 99%

Here we see the biggest change after performing the Random Over Sampling.
Recall has now improved to 99% without losing any precision.

With this model we can now predict 99% of high-risk accounts.

## Summary

Summarize the results of the machine learning models, and include a recommendation on the model to use, if any. For example:
* Which one seems to perform best? How do you know it performs best?
The Random Over Sampled model performs best. We can see this in it's high recall.

* Does performance depend on the problem we are trying to solve? (For example, is it more important to predict the `1`'s, or predict the `0`'s? )

Predicting 1's - or high-risk - is the most important factor. Logistic regression's performance at predicting these cases are dependant on having suffient number of cases in the dataset to train on.


