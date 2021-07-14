# Two-Class-Loan-Prediction-Model-Logistic-Regression-using-Microsoft-AZURE-ML-Studio
- We will try to identify if the loan application gets approved or not.

## 1)Visualising the dataset : 
   - Upload the dataset in Azure ML Studio by selecting the `NEW` option.
   - Once you have uploaded the dataset, create a new `Blank Experiment` after selecting the `NEW` option again.
   - Drag the dataset in the working space and visualise it : 
   - <img width="600" alt="Screen Shot 2021-07-14 at 7 27 00 PM" src="https://user-images.githubusercontent.com/55271617/125634653-83f1240e-c223-48cc-b0ce-9beedc015063.png">
   - <img width="600" alt="Screen Shot 2021-07-14 at 7 34 41 PM" src="https://user-images.githubusercontent.com/55271617/125635746-32a08009-a38d-499c-a5d6-88e96342e263.png">
   - Try to vusialise every column, for eg `gender` has got 2 unique values, that is male or female but it has got some missing values as well.
   - Visualise rest of the columns in the same way.
   - You will also see some missing values in the numeric features of loan amount, loan amount term and credit history. If you notice, that credit history here is not just a score but a binary value of either 0 or 1. This is because the company must have decided that they want to consider applicants with a score higher than a particular value as 1 and others below it as 0. This actually makes it a categorical variable and hence, we will treat it as one in our experiment.

## 2)Replacing the Missing Values :
