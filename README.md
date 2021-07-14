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
   We should clean this missing data so that our model can work on neat and clean information.
   - Drag and drop the `Clean Missing Data` Module in your workspace.
   - Let's first clean the string features by launching the `column selector` on the right hand side of your workspace.
   - Select the columns with string features. 
   - <img width="700" alt="Screen Shot 2021-07-15 at 12 10 46 AM" src="https://user-images.githubusercontent.com/55271617/125675290-ea31b522-56b3-4094-a99d-f22dd78dff2f.png">
   - <img width="700" alt="Screen Shot 2021-07-15 at 12 10 38 AM" src="https://user-images.githubusercontent.com/55271617/125675304-e9db1642-3db5-4347-8d87-3b4251550ecc.png">
   - We have selected `Credit History` as well cause in the next steps we'll replace the missing values with mode.
   - <img width="950" alt="Screen Shot 2021-07-15 at 12 15 26 AM" src="https://user-images.githubusercontent.com/55271617/125675873-9c192bc1-5c13-41e2-af40-336c1ca510b0.png">
   - We want to replace these values with the most frequent value in the respective column. Hence, we select replace with mode. This was the reason that we have selected `credit history` as well so that we retain the 2 unique values and do not get into the trap of mean.
   - We have kept values of `Minimum missing value ratio` and `Maximum missing value ratio` as 0 and 1 respectively cause we want to replace all the missing values.
   - In similar fashion now we can replace the missing numeric values as follows : (this time we'll replace the values with mean)
   - <img width="897" alt="Screen Shot 2021-07-15 at 12 25 44 AM" src="https://user-images.githubusercontent.com/55271617/125677149-cef51249-2576-4cb8-84ac-bc6d4924d15d.png">
   - Now you can run the experiment and visualise the data. (no missing values)
   - <img width="1238" alt="Screen Shot 2021-07-15 at 12 27 14 AM" src="https://user-images.githubusercontent.com/55271617/125677337-893d8299-5dcc-4215-b031-0641771b5bdc.png">
   
   ## 3)Replacing the Missing Values :


