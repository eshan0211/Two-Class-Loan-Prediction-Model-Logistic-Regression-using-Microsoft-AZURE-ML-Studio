# Two-Class-Loan-Prediction-Model-Logistic-Regression-using-Microsoft-AZURE-ML-Studio
- We will try to identify if the loan application gets approved or not.

## 1)Visualising the dataset : 
   - Upload the dataset in Azure ML Studio by selecting the `NEW` option.
   - Once you have uploaded the dataset, create a new `Blank Experiment` after selecting the `NEW` option again.
   - Drag the dataset in the working space and visualise it : 
   - <img width="500" alt="Screen Shot 2021-07-14 at 7 27 00 PM" src="https://user-images.githubusercontent.com/55271617/125634653-83f1240e-c223-48cc-b0ce-9beedc015063.png">
   - <img width="500" alt="Screen Shot 2021-07-14 at 7 34 41 PM" src="https://user-images.githubusercontent.com/55271617/125635746-32a08009-a38d-499c-a5d6-88e96342e263.png">
   - Try to vusialise every column, for eg `gender` has got 2 unique values, that is male or female but it has got some missing values as well.
   - Visualise rest of the columns in the same way.
   - You will also see some missing values in the numeric features of loan amount, loan amount term and credit history. If you notice, that credit history here is not just a score but a binary value of either 0 or 1. This is because the company must have decided that they want to consider applicants with a score higher than a particular value as 1 and others below it as 0. This actually makes it a categorical variable and hence, we will treat it as one in our experiment.

## 2)Replacing the Missing Values :
   We should clean this missing data so that our model can work on neat and clean information.
   - Drag and drop the `Clean Missing Data` Module in your workspace.
   - Let's first clean the string features by launching the `column selector` on the right hand side of your workspace.
   - Select the columns with string features. 
   - <img width="500" alt="Screen Shot 2021-07-15 at 12 10 46 AM" src="https://user-images.githubusercontent.com/55271617/125675290-ea31b522-56b3-4094-a99d-f22dd78dff2f.png">
   - <img width="500" alt="Screen Shot 2021-07-15 at 12 10 38 AM" src="https://user-images.githubusercontent.com/55271617/125675304-e9db1642-3db5-4347-8d87-3b4251550ecc.png">
   - We have selected `Credit History` as well cause in the next steps we'll replace the missing values with mode.
   - <img width="500" alt="Screen Shot 2021-07-15 at 12 15 26 AM" src="https://user-images.githubusercontent.com/55271617/125675873-9c192bc1-5c13-41e2-af40-336c1ca510b0.png">
   - We want to replace these values with the most frequent value in the respective column. Hence, we select replace with mode. This was the reason that we have selected `credit history` as well so that we retain the 2 unique values and do not get into the trap of mean.
   - We have kept values of `Minimum missing value ratio` and `Maximum missing value ratio` as 0 and 1 respectively cause we want to replace all the missing values.
   - In similar fashion now we can replace the missing numeric values as follows : (this time we'll replace the values with mean)
   - <img width="500" alt="Screen Shot 2021-07-15 at 12 25 44 AM" src="https://user-images.githubusercontent.com/55271617/125677149-cef51249-2576-4cb8-84ac-bc6d4924d15d.png">
   - Now you can run the experiment and visualise the data. (no missing values)
   - <img width="500" alt="Screen Shot 2021-07-15 at 12 27 14 AM" src="https://user-images.githubusercontent.com/55271617/125677337-893d8299-5dcc-4215-b031-0641771b5bdc.png">
   
   ## 3)Selecting Features (Columns) :
- Drag and drop the `select columns in dataset`module in your workspace.
- Select every column except the `Loan ID` cause its just a random unique number.
- <img width="500" alt="Screen Shot 2021-07-15 at 1 25 15 AM" src="https://user-images.githubusercontent.com/55271617/125684590-648f89db-b32b-4b0d-b6c2-833b08a48602.png">
- <img width="500" alt="Screen Shot 2021-07-15 at 1 23 33 AM" src="https://user-images.githubusercontent.com/55271617/125684410-3fdbda7a-440d-491d-a813-04a6171e807d.png">

## 4)Splitting Data :
We will split the existing data and use part of the data for training our model and the rest for testing the result as well as validating the results for accuracy.
- Drag and drop the `split data` module.
- We will split the data in 70:30 ratio and lets do the [stratified split](https://stats.stackexchange.com/questions/250273/benefits-of-stratified-vs-random-sampling-for-generating-training-data-in-classi) on the column, `loan status` so that we have even distribution of values between train and test dataset.
- <img width="500" alt="Screen Shot 2021-07-15 at 1 34 50 AM" src="https://user-images.githubusercontent.com/55271617/125685701-b4524d1f-ae29-47c6-92b0-ccc60f85b129.png">
- Now Run the `split data` module and visulaise the two output nodes.(one has 70 percent data and one 30 percent)

## 5)Training and scoring our two-class Logistic Regression Model :
We are going to predict an outcome that's either yes or no, which means that we are only predicting two classes, so we will use two-class logistic regression.
- Drag and drop the `Two- Class Logistic Regression` Model, we will use the defualt parameters but you can also change the parameters and visualise the change in results with different values of parameters.
- For training our model, drag and drop the `train model` module (selecting loan status as the column selector) and connect them as shown below.
- <img width="500" alt="Screen Shot 2021-07-15 at 1 43 55 AM" src="https://user-images.githubusercontent.com/55271617/125686744-ce0d65c7-d0c8-4dc0-9d6b-5d7650369b8e.png">
- The model is ready to be trained, we want to score the algorithm on our test dataset and see how it performs. So the module that is required for the same is called as a score model, which is basically a validation module for our trained algorithm. So let's search for it and drag and drop it hereand as you will see, it requires 2 inputs. The first one is the train model which is nothing but the output from the train model module and the test dataset.
- So we provide the connection of our train model as well as the test dataset. The test dataset is coming from the second node of split module. Now, let's right click on it and run selected. It will run all the previous steps that have not been executed so far.
- <img width="500" alt="Screen Shot 2021-07-15 at 1 48 09 AM" src="https://user-images.githubusercontent.com/55271617/125687248-17500f33-227c-4275-b6cb-44ff6294dd22.png">
- Now we can visualise the output.
- <img width="500" alt="Screen Shot 2021-07-15 at 1 49 36 AM" src="https://user-images.githubusercontent.com/55271617/125687427-80e94824-8b73-4690-94e4-c5411c97c0f2.png">
- As you can see, there are two additional columns called scored label and score probabilities, scored label is the predicted value of that particular set of features or rows and score probability is the probability with which this particular value has been predicted.

## 6)Evaluating our model :
Lets visualize these results in a bit more structured manner.
- We will use a module called `evaluate model` for evaluating our results.
- It takes 2 nodes which are for evaluating different models. The second one is optional and let's connect our scored model to the first node and run it.
- <img width="500" alt="Screen Shot 2021-07-15 at 1 55 08 AM" src="https://user-images.githubusercontent.com/55271617/125688132-92794f67-c1a9-427b-97ee-292ccaf55732.png">
- After visulising the output, we can say the accuracy is around `83%` and the AUC i.e area under thecurve is also very high which means that the model is a very good model.
- <img width="500" alt="Screen Shot 2021-07-15 at 1 58 11 AM" src="https://user-images.githubusercontent.com/55271617/125688531-6bf6b3ab-0e53-4335-a042-ca8564ddbe7d.png">
- <img width="500" alt="Screen Shot 2021-07-15 at 1 58 20 AM" src="https://user-images.githubusercontent.com/55271617/125688549-7fb5c912-7c0b-4a12-93ed-cb2b0ae2e2b4.png">

Similarly we can also use multi class logistic regression, if we have to categorise our result in more than 2 values, for eg marks in class can be categorised as high, average and low.

# Thank You, Hope the explanation was clear and to the point !









