# Module-12-Challenge - Model Evaluating Creditworthiness
This application utilizes various Supervised Learning techniques to train and evaluate models with imbalanced classes.

The Starter Code was provided along with the historical lending data.

---

## User Story
Credit risk poses a classification problem that’s inherently imbalanced. This is because healthy loans easily outnumber risky loans. Use various techniques to train and evaluate models with imbalanced classes. Using a dataset of historical lending activity from a peer-to-peer lending services company build a model that can identify the creditworthiness of borrowers.

---

## Acceptance Criteria  
The application must meet the following acceptance criteria:  

* Split the Data into Training and Testing Sets
* Train, Test and Evaluate Logistic Regression Model with the Original Data  
* Train, Test and Evaluate Regression Model with Resampled Training Data 
---

## The Application  

The application follows these stages: 

### Split the Data into Training and Testing Sets

1. Read the `lending_data.csv` data from the `Resources` folder into a Pandas DataFrame.
2. Create the labels set (`y`)  from the “loan_status” column, and then create the features (`X`) DataFrame from the remaining columns.
    > **Note** A value of `0` in the “loan_status” column means that the loan is healthy. A value of `1` means that the loan has a high risk of defaulting.  
3. Check the balance of the labels variable (`y`) by using the `value_counts` function.
4. Split the data into training and testing datasets by using `train_test_split`.

### Create a Logistic Regression Model with the Original Data

1. **Fit** a logistic regression model by using the training data (`X_train` and `y_train`).
2. **Predict** on the testing feature data (`X_test`) and the fitted model.
3. **Evaluate** the model’s performance by printing **Balanced Accuracy Score, confusion matrix,** and **classification report**

### Create a Logistic Regression Model with Resampled Training Data  

1. Use the `RandomOverSampler` module from the imbalanced-learn library to resample the data. Confirm that the labels have an equal number of data points. 
1. **Fit** a logistic regression model by using the oversampled training data (`X_train_oversampled` and `y_train_oversampled`).
2. **Predict** on the testing feature data (`X_test`) and the fitted model.
3. **Evaluate** the model’s performance by printing **balanced accuracy score, confusion matrix,** and **classification report**
---

## Report on the Model Evaluating Creditworthiness

For a summary and analysis of the performance of both machine learning models [click here for the detailed REPORT ](report.md)

## Technologies
The application is developed using:  
* Language: Python 3.7,   
* Packages/Libraries: Pandas,  numpy;  balanced_accuracy_score, confusion_matrix from sklearn.metrics import balanced_accuracy_score, classification_report_imbalanced from imblearn.metrics
* Development Environment: VS Code and Terminal, Anaconda 2.1.1 with conda 4.11.0, Jupyterlab 3.2.9  
* OS: Mac OS 12.1

---
## Installation Guide
Following are the instructions to install the application from its Github respository.  

### Clone the application code from Github as follows:
copy the URL link of the application from its Github repository      
open the Terminal window and clone as follows:  

   1. %cd to_your_preferred_directory_where_you want_to_store_this_application  
    
   2. %git clone URL_link_that_was_copied_in_step_1_above   
    
   3. %ls     
        Module-12-Challenge    
        
   4. %cd Module-12-Challenge     

At this point you will have the the entire application files in the current directory as follows:

    * README.md                       (this file that you are reading)  
    * report.md
    * credit_risk_resampling.ipynb         (the application jupter lab notebook)  
    * Resources                      (Folder with the data required) 
        - lending_data.csv  
       

---

## Usage
The following details the instructions on how to run the application.  

### Setup the environment to run the application
Setup the environment using conda as follows:

    5. %conda create dev -python=3.7 anaconda  
    
    6. %conda activate dev  
    
    7. %jupyter lab  

---

### Run the Application
THIS ASSUMES FAMILIARITY WITH JUPYTER LAB. If not, then [click here for information on Jupyter Lab](https://jupyterlab.readthedocs.io/en/stable/).  

After step 7 above, this will take you to the jupyter lab window, where you can open the application notebook **credit_risk_resampling.ipynb** and run the application.  

**NOTE**:
>Your shell prompt will look something like __(dev) ashokpandey@Ashoks-MBP dir%__ ,  with:  
    - '(dev)' indicating the activated 'dev' environment,   
    - ' ashokpandey@Ashoks-MBP ' will be different for you as per your environment, and   
    - 'dir' directory is where the application is located.  
    - '%' sign is the shell prompt - it may be a dollar sign in your implementation 

---

## Contributors
Ashok Pandey - ashok.pragati@gmail.com   
www.linkedin.com/in/ashok-pandey-a7201237

---

## License
The source code is the property of the developer. The users can copy and use the code freely but the developer is not responsible for any liability arising out of the code and its derivatives.

---