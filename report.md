# Module 12: Report on Model Evaluating Creditworthiness

## Overview
Credit risk poses a classification problem that’s inherently imbalanced. This is because healthy loans easily outnumber risky loans. Use various techniques to train and evaluate models with imbalanced classes. Using a dataset of historical lending activity from a peer-to-peer lending services company build a model that can identify the creditworthiness of borrowers.

## Methodology
In order to evaluate evaluate models with imbalanced classes, Logistic Regression model was used. 

   >**Logistic regression** is a supervised classification algorithm in which based upon a number of inputs it gives out discrete outcomes. For example, in our case, based upon **loan_size, interest_rate, borrower_income, debt_to_income, num_of_accounts, derogatory_marks,** and **total_debt** of a borrower, the Logistic Regression model will predict discrete outcomes whether the borrower is creditworthy or risky, i.e. whether he can be loaned money or not.  Mathematically, in Logistic Regression the probability of a discrete outcome is calculated given a set of independent input variables; if the probability is above a threshold one outcome is predicted and if it is below the threshold the other outcome is predicted. 

Lending data was provided in **Resources/lending_data.csv**. As part of the methodology, the following major steps were used: 

1. Split the Data into Training and Testing Sets

2. Create and evaluate a Logistic Regression Model with the Original Data

3. Create and evaluate a Logistic Regression Model with Resampled Training Data 

4. Compare the results of the two models and make recommendation

## Split the Data into Training and Testing Sets

The Lending data contains the following credit related information of a borrower - **loan_size, interest_rate, borrower_income, debt_to_income, num_of_accounts, derogatory_marks, total_debt,** and **loan_status**. 

   > **Note** A value of `0` in the “loan_status” column means that the loan is healthy. A value of `1` means that the loan has a high risk of defaulting.  

The model is trained using this data, i.e. it will learn to predict the **loan_status** based upon **loan_size, interest_rate, borrower_income, debt_to_income, num_of_accounts, derogatory_marks,** and **total_debt**. The **loan_status** is stored in the variable **y** and the rest of the information in the variable **X**.

The entire dataset is divided into two sets, one for **training** and the other for **testing**, keeping in mind that the **test** data should never be seen by the model during **training** or before **testing**.

To accomplish splitting **Original** data **X and y** into **training (X_train, y_train)** and **testing (X_test, y_test)** datasets, `train_test_split` function is used.

### Checking Imbalance  
After splitting the data check to see the amount of information available for training the model using **value_counts()** function on **y_train**. In our dataset, there are about 75,000 **0's** and 2500 **1's** implying that the model is trained significantly more on good loans (status of **0s**) which can impair its ability to detect high risk loans (status of **1s**) as effectively.

At the outset, it is indicating the need for the model to be trained more on detecting high risk loans. First, we find out how well the model works with the Original data. Then, we resample the data to balance the training dataset so that the model is trained equally on both good and high-risk loans.

## Create a Logistic Regression Model with the Original Data
Create and evaluate a Logistic Regression Model with Original Data as follows:  

1. **Fit** the logistic regression model by using the training data (`X_train` and `y_train`).

2. **Predict** on the testing feature data (`X_test`) and the fitted model.

3. **Evaluate** the model’s performance using the **accuracy score**, **confusion matrix** and **classification report**

### Predict a Logistic Regression Model with Resampled Training Data
Create and evaluate a Logistic Regression Model with Resampled Training Data as follows:   

1. **Resample** the Training Data using the `RandomOverSampler` module from the imbalanced-learn library. Confirm equal number of data points. As mentioned earlier, in Original data there are about **75000 healthy** loans while only **2500 high-risk** ones. The majority class with over 30 times more data points than the minority class with only 2500 data points!!  

    >The `RandomOverSampler` function would oversample the minority class so that both the majority and minority classes have the same number of data points. After resampling the Training data both the majority (good loans) and the minority (high-risk loans) classes have the same **56271** number of data points.

1. **Fit** the logistic regression model by using the resampled training data (`X_train_oversampled` and `y_train_oversampled`).

2. **Predict** on the testing feature data (`X_test`) and the fitted model.

3. **Evaluate** the model’s performance using the **accuracy score**, **confusion matrix** and **classification report**


## Results
For both the models, results of the analysis are discussed using **Balanced Accuracy, Precision**, and **Recall** metrics.
   >**Balanced Accuracy** in binary and multiclass classification problems deals with imbalanced datasets. It is defined as the average of recall obtained on each class.  
    **Precision** - "How much what I say is correct" - number of correct predicitions out of all the predictions thought to be correct in that class, i.e. TP/(TP+FP)  
    **Recall** - "How much actual positives are captured" - number of correct predictions out of all the actual True values of a class, i.e. TP/(TP+FN)  

### Logistic Regression Model with the Original Data:
  * Balanced Accuracy Score: The model captures an average of 95% of all actual positives in each class
  * Precision: 
      * 100% for class 0 - predicts 100% samples correctly for 'healthy' loan cases
      * 85% for class 1 - predicts 85% correctly for 'risky' loan cases
  * Recall scores:
      * 99% for class 0 - predicts 99% samples correctly out of all the actual 'healthy' loan cases
      * 91% for class 1 - predicts 91% samples correctly out of all the actual 'risky' loan cases

### Logistic Regression Model with the Resampled Data
  * Balanced Accuracy Score: The model captures an average of 99% of all actual positives in each class
  * Precision: 
      * 100% for class 0 - predicts 100% samples correctly for 'healthy' loan cases
      * 84% for class 1 - predicts 84% correctly for 'risky' loan cases
  * Recall scores:
      * 99% for class 0 - predicts 99% samples correctly out of all the actual 'healthy' loan cases
      * 99% for class 1 - predicts 99% samples correctly out of all the actual 'risky' loan cases

## Summary
Based upon the results of the analysis, it appears that the Logistic Regression model with resampled data has improved recall statistics. The Balanced Accuracy Score went up from 95 to 99%. Also, if you examine both the classes, Recall went from 91% to 99% for class 1, and it remained at 99% for class 0. Also, the Precision dipped marginally from 85 to 84% for class 1.


For class 1 (risky loans), loooking at Precision, of all the predictions the model with Original data predicted 15% incorrectly, implying 619*15% = 92 cases where the borrowers were considered risky, who were not risky.  This number went upto 99 for the resampled model. Depending upon the model, 92 to 99 people could have been extended credit but due to predicting them as risky the Lender actually would lose out related revenues. 

Recall for class 1 went from 91 to 99% meaning that of all the actual risky cases, the model predicted 99% of them accurately, only 1% were predicted as False Negative, i.e 619*.01 = 6 cases! Not bad!

Both the models predict class 0 (healthy) cases 100% accurately.

The objective was to determine credit-worthiness of potential borrowers, and the second model does a great job with 99% accuracy and recall.  I would recommend the model with resampled data to be used for credit risk evaluation. 
