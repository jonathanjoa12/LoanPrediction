# Loan Prediction

Background and Introduction to the Project:

Loans are essential especially today because many people who want to buy a home or a car typically request a loan from the bank. There are many factors that come into play when banks assess a person's ability to pay back a loan or not. This project assesses a dataset containing applicant information. This data is trained under multiple machine learning models and the goal of this project is to assess which model is the best fit for this data. The results will be very useful for banks in determining whether an applicant will be accepted for a loan or not. Most of these sections are briefly discussed in the read me but further detail can be assessed within the .pynb files.

Files: test.csv and train.csv:
The test file is what we will make our predictions on after model training. 
The train file is what we are primarily working with throughout the project that includes applicant information including:

Gender: Male or Female

Marital status: Married or Not Married

Income: How much the applicant makes per year.

Coapplicant income: How much the coapplicant makes.

Credit: Is there an established credit history?

Property area: The type of environment that the applicant lives whether it is rural, semi-urban, or urban.

Loan amount: How much the applicant is requesting for loans.

Loan amount term: The amount of time until the loan is expected to be paid off.

Self-Employed: Is the applicant self-employed or not

Education: Did the applicant graduate college?

Dependents: How many dependents does the applicant have?


File: Exploratory Data Analysis:

The data is explored feature by feature to determine if there are necessary changes needed to improve the training of the model. This includes determining what should be done with the null values, converting string categories to categorical values, and creating visualizations of the individual features including histograms to determine if data is skewed or not. In addition, multiple questions and hypotheses were generated during this section and answered through visualizations. For example, we explore the data to see whether there is a disparity when it comes to gender. Most applicants are male. After using cross-tabulation analysis. We determine that men and women are equally likely to get approved for a loan.

When determining the action that should be done to null values, we took consideration not only what should be inputted statistically, but also the context behind the null value. For example, when we impute the null value for the number of kids, we must input an int or whole number because when we input the mean which is a floating value, we get .76 which cannot represent the number of kids a loan applicant has. 
We notice that our prediction value of loan_status is a binary categorical value. Therefore, we should consider classification models when we train our machine learning models. 

File: Data Preprocessing:

During our exploratory data analysis, we notice the features including the loan amount, applicant income and monthly payments are skewed. Therefore, we must to take the log of the data to mitigate the problem. We also feature engineer the total income by adding the coapplicant income and the applicant income together.

We must split our data into the training and testing set to assess if we have a representative test set or not. We must also scale our data for the distance-based models including K-Nearest Neighbors and Support Vector Machines.

File: Models:

During this section, we explore the most common classification models including Logistic Regression, Decision Trees, Random Forests, K-Nearest Neighbors, Support Vector Machines, Gradient Boosting, and Naive Bayes. We train the models and conduct gridsearching or hyperparameter tuning to find the best parameters of each model.

All the models have a higher training score than testing score which makes them at risk of overfitting with Random Forest Model being the highest at risk. This is a little surprising considering Decision Trees tend to overfit more often than Random Forest Models.

The model that we select is highly dependent on the initial problem that we are trying to solve. For example, if we want to minimize borrowers defaulting on their loans, we will try to optimize the precision rate. Therefore, we would choose a logistic regression model or gradient boosting model that score the highest in precision. 

If we want to improve our customer acquisition rate, we will want to optimize for recall. Many of these consumers may have never had a history of taking out loans from a bank in which there is a higher chance of more consumers defaulting on their loans if recall is the metric chosen to optimize. If recall were the metric to be optimized, we would choose either a Support Vector Machine model or Gradient Boosting model. Each model has their drawbacks including a lower AUC ROC on the Support Vector Machine and slightly higher tendency of overfitting on the Gradient Boosting Model. 

When determining the features that contribute the most to the target variable prediction, the highest contributing factors taken from the logistic regression model are credit history, maritial status, dependents, and education.

In the end of the project, the model is used to predict the test data along with the probabilities of an applicant getting rejected or accepted for their loan.

Drawbacks:

- In terms of the data, a specific credit score number would help significantly to predict the model. A credit history can mean a person has a history of credit. However, its not specified whether it is good or bad credit.

- The dataset is too small. The number of applicants in the dataset is 614 which can significantly affect the results.

- There were a few features that were highly correlated with each other which may have affected the Random Forest Model. They included the Total Income vs Loan Amount and Applicant Income. Loan status and credit history tend to have a moderate correlation between each other.

