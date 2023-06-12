
# **Credit Risk Analysis Report**


## **Overview of the Analysis**

The purpose of this project was to create a credit risk model for peer to peer loans that helped classify loans as performing loans vs. non-performing/high risk loans.  The target/dependent variable here was loan status (0 = healthy loan, 1=high risk loan).  This means we're looking to segment customers into 2 categories:  good risk and bad risk.

The feature/independent variables in the dataset were variables like: loan size, interest rate, borrower income, debt to income ratio, number of accounts, derogatory marks and total debt.  This looks like a simple potential application stage risk model or account management/collections risk model for approved loans.

Given we're looking to classify customers into good and bad loan categories, we'll be using a logistic regression model within the context of the standard machine learning process.  This process means we'll be:

* Cleaning and pre-processing the data to get it ready for modeling
* segmenting the data in modeling building (training) and model testing (test) samples
* Comparng model predictions vs. actual results to evaluate the quality of the credit risk model
* Make next step adjustments to enhance the model through random oversampling high risk data to enhance model effectiveness

The analytical methods used here include:
* Logistic Regression modeling
* Random Oversampling of high risk data given lower sample size of high risk loans vs. healthy loans


## **Risk Analysis Results**

Using bulleted lists, describe the balanced accuracy scores and the precision and recall scores of all machine learning models.

#### **Machine Learning Model 1:**


**Accuracy Score:** 0.9520

**Confusion Matrix:**

           Pred. 0   Pred. 1
    
Actual 0     18663       102

Actual 1        56       563


**Classification Report:**

              precision    recall  f1-score   support

           0       1.00      0.99      1.00     18765
           1       0.85      0.91      0.88       619

    accuracy                           0.99     19384

   macro avg       0.92      0.95      0.94     19384

weighted avg       0.99      0.99      0.99     19384


#### **Machine Learning Model 2:**


**Accuracy Score:** 0.9936

**Confusion Matrix:**

            Pred. 0  Pred. 1

Actual 0     18649       116

Actual 1         4       615

**Classification Report**

              precision    recall  f1-score   support

           0       1.00      0.99      1.00     18765
           1       0.84      0.99      0.91       619

    accuracy                           0.99     19384

   macro avg       0.92      0.99      0.95     19384

weighted avg       0.99      0.99      0.99     19384



## **Credit Risk Analysis Summary**

### **Regular Data Machine Learning Model 1 Summary:**

* Overall model accuracy at 0.99 or 99% is very high and very good. The model does a better job at predicting heathly loans vs. high risk loans given both the precision score and recall score are higher for 0 vs. 1 (1.00 > 0.85 precision score and 0.99 > 0.91 recall score). Having said that, a precision score of 0.85 and recall score of 0.91 for high risk loans is very good and this model does work on predicting high risk loans.

* The higher recall score for high risk loan predictions (predicting 1) vs. precision score (0.91 vs. 0.85) tells us that the model produces more false positives (lower precision score) than false negatives (higher recall score). This means the model predicts high risk loans when they're not actually high risk more often than it predicts a no charge-off loan that actually charged off. This skew in error means the model is erroring in a direction we can live with, its more accurately predicts a charged-off/high risk loan than it predicts a charged-off loan that didn't charge-off.

### **Oversampling Data Machine Learning Model 2 Summary:**

* This oversampled model doesn't have much room to improve predicting heahly loans (0) vs. the previous model given the previous model already had precision and recall scores at 1.00 and 0.99 respectively (no real room to improve). The oversampling model performs just as well as the previous model (no better or worse).

* This oversampling model does improve on the prior model in predicting high risk loans (1). The precision score was flat from 0.85 in the prior model to 0.84 in the oversampling model. The recall score improved from 0.91 in the prior model to 0.99 in the oversampling model.

* This means the oversampling model produces way less false negatives with a 0.99 recall score. This means the oversampling model clearly identifies almost all high risk loans in the sample accurately. The false positives didn't change much here given precision scores went from 0.85 to 0.84. This means the oversampling model was about the same in classifying fewer loans as high risk when they weren't really high risk.

### **Final Model Recommendation:**

* Given the model analysis results, I'd recommend implementing the oversampling model (model 2) for future credit risk forecasting for this loan population.  This risk model can assist in identifying high risk loans that may need more risk management strategies applied to it to reduce future losses on the portfolio.  The rationale is pretty simple, most key analysis reports and metrics (accuracy score, confusion matrix and classification report) look better on the random oversampled model vs. the regular data model.  Oversampling is a fairly standard technique in the loss forecasting space and has been proven more effective in practice.

