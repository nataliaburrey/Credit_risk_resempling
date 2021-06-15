# Module 12 Report 

## Overview of the Analysis

In this section, describe the analysis you completed for the machine learning models used in this Challenge. This might include:

* Explain the purpose of the analysis.
 The purpose of the analysis-use various techniques to train and evaluate models with imbalanced classes. In this scenario we hare a credit risk data, where risky loans are usually less common, so the samples of that class are significantly less. This is why model might put more weight on bigger class and although show pretty good prediction overall-will fail to do the most important thing-catch the loans with a high risk
 There is a different ways to balance the data and in this scenario we are using oversampling to balance asset classes to improve the predictive effectiveness of the machine learning model. 

* Explain what financial information the data was on, and what you needed to predict.

We have a CSV file which contains following information about each customer: loan size,	interest rate,	borrower income,	debt to income ratio,	number of accounts, derogatory marks,	total debt.
Based on that information we have to predict which of the following customers will default on the loan (risky loans) and which one will pay it off (healthy loans) 

* Provide basic information about the variables you were trying to predict (e.g., `value_counts`).

- The value_counts() function is used to get a Series containing counts of unique values. The resulting object will be in descending order so that the first element is the most frequently-occurring element. Excludes NA values by default.

 (category 0) : 75036 is the number of healthy loans, (category 1) : 2500 is the number of risky loans, which is obviously unbalanced number. 
 
-The balanced accuracy in binary and multi-class classification problems to deal with imbalanced datasets.  It is defined as the average of recall obtained on each class. The best value is 1 and the worst value is 0 when adjusted=False .

balanced_accuracy score of our model is 0.9520479254722232 -really good 


* Describe the stages of the machine learning process you went through as part of this analysis.

The process consists of the following subsections:

  1. Split the Data into Training and Testing Sets
  2. Create and predict a Logistic Regression Model with the Original Data
  3. Resampled the training data and predicted a Logistic Regression Model with Resampled Training Data

* Briefly touch on any methods you used (e.g., `LogisticRegression`, or any resampling method).

```
Logistic Regression:
  is designed to predict discrete outcomes. We can thus use logistic regression to make decisions. An example is whether to approve or deny a credit card application based on personal information. In this case, logistic regression assesses multiple variables, such as an applicant's age and income, to arrive at one of two answers: approve or deny the application. To further explain, a logistic regression model analyzes the available data. When presented with a new sample of data, the model mathematically determines the probability of the sample belonging to a class. If the probability is greater than a certain cutoff point, the model assigns the sample to that class. If the probability is less than or equal to the cutoff point, the model assigns the sample to the other class.

```

## Results

Using bulleted lists, describe the balanced accuracy scores and the precision and recall scores of all machine learning models.

* Machine Learning Model 1:
  * Description of Model 1 Accuracy, Precision, and Recall scores.

 - Balanced accuracy score (95.2%)
 - Precision score (85%)
 - Recall score (91%)

 Precision with healthy loans (0 category) is 1.00, which is stating that model predicted healthy loans with a 100% accuracy which don’t get any better. The prediction for high-risk loans (1 category) is only 85 % which means that the model sometimes classifying some healthy loans as unhealthy. We can see the proof of that statement in specificity for healthy loans-it is 91%-compare with 99% for unhealthy. It means that our model is really good for catching bad loans-sometimes too good. We need to make sure that mistake does not happened too often as we will miss on some interest revenue and possibly loose some valuable customers-however its better than give a bad loans to a customers who will default on them. Balanced accuracy is calculated as the average of the proportion corrects of each class individually and in our model is 90% for both categories-geometric mean, geometric mean is 95%. We would want those numbers be as high as possible to make sure our model does what we need it to do accurately catching possible bad loans, so we need to improve our sampling data, to balance some of this numbers.


* Machine Learning Model 2:
  * Description of Model 2 Accuracy, Precision, and Recall scores.
  
 - Balanced accuracy score (99.4%)
 - Precision score (84%)
 - Recall score (99%)
 
Precision with healthy loans (`0` category) is 1.00, which is stating that model predicted healthy loans with a 100% accuracy which don’t get any better.  The prediction for high-risk loans (`1` category)  is only 84 %. on one hand the number is not too great. But giving our goal- do not give money to a high risk customers to reduce risk of default of the loan, we can say that our model just gives us more cautious prediction, sometimes classifying some healthy loans as unhealthy. 
Giving the recall and specificity number and for both categories being almost perfect (99%) we can assume that our model did a very good job of correctly correctly classifying healthy and, what most important, high risk loans, we can ignore number for precision being slightly lower.
Harmonic mean for high risk loans are 91% compare with 100% for a healthy loans, which is not too bad, but again confirms our predicament that our model is better in finding originally bigger asset class. 
Overall logistic regression model, fit with oversampled data, gives us EXTREMELY GOOD predictions for both categories, giving a 99-100% for healthy loans, and sometimes being a little too cautious with and classifying some good loans as high-risk loans, which is overall good strategy, giving that other performance metric is close to 100% so the model does its job very well.


## Summary

Summarize the results of the machine learning models, and include a recommendation on the model to use, if any. For example:
* Which one seems to perform best? How do you know it performs best?
Both models perform pretty good, BUT accuracy score and f1 score improved with oversampled data, so i would recommend using oversampled model, as catching even a couple of bad loans can be crucial. Also flagging good loans as bad can also cost us some loyal customers and potential long relationship, we want any improvement.  

* Does performance depend on the problem we are trying to solve? (For example, is it more important to predict the `1`'s, or predict the `0`'s? )

Class 1 - Risky loans - is more rare, but in this case correctly flagging the rare class has the most importance.  Loosing money due to person defaulting on the loan is more costly than  miscatergorize a healthy customer as risky, denying and missing out on interest.

