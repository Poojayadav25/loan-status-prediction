# loan-status-prediction
![1_UC0sy0bENl-DLPy3jmXNag](https://user-images.githubusercontent.com/90573789/172597192-c77d4238-d579-49ea-b06b-82b044983a35.jpeg)

# Problem Statement:
Loans are the core business of banks. The main profit comes directly from the loan’s interest. The loan companies grant a loan after an intensive process of verification and validation. However, they still do not have assurance if the applicant is able to repay the loan with no difficulties. The two most critical questions in the lending industry are:

- How risky is the borrower?
- Given the borrower’s risk, should we lend him/her?
In the modern era, the data science teams in the banks build predictive models using machine learning to predict how likely a client is going to default the loan when they only have a handful of information. Loan Prediction is a very common real-life problem that each retail bank faces at least once in its lifetime. If done correctly, it can save a lot of man hours at the end of a retail bank.

# Goal of this Project:
Dream Housing Finance company deals in all home loans. They have presence across all urban, semi urban, and rural areas. Customer first apply for home loan after that company validates the customer eligibility for loan. Company wants to automate the loan eligibility process (real time) based on customer detail provided while filling online application form.

To automate this process, they have given a problem to identify the customers’ segments, those are eligible for loan amount so that they can specifically target these customers. The goal of this project is to predict whether a loan would be approved or not.

# Hypothesis Generation:
Below are the factors which I think can affect the Loan Approval (dependent variable for this loan prediction problem):

• Salary: Applicant with high income should have more chances of loan approval.

• Previous History: Applicant who have repaid their previous debts should have higher chances of loan approval.

• Loan Amount: Loan Approval should also depend on the loan amount. If the loan amount is less, chances of loan approval should be high.

• Loan Term: Loan for less time and less amount should have higher chances of approval.

• EMI: Lesser the amount to be paid monthly to repay the loan, higher the chances of loan approval.

# Major observation from the data:
- Applicants who are male and married tends to have more applicant income whereas applicant who are female and married have least applicant income

- Applicants who are male and are graduated have more applicant income over the applicants who have not graduated.

- Again the applicants who are married and graduated have the more applicant income.

- Applicants who are not self employed have more applicant income than the applicants who are self employed.

- Applicants who have more dependents have least applicant income whereas applicants which have no dependents have maximum applicant income.

- Applicants who have property in urban and have credit history have maximum applicant income

- Applicants who are graduate and have credit history have more applicant income.

- Loan Amount is linearly dependent on Applicant income

- From heatmaps, applicant income and loan amount are highly positively correlated.

- Male applicants are more than female applicants.

- No of applicants who are married are more than no of applicants who are not married.

- Applicants with no dependents are maximum.

- Applicants with graduation are more than applicants whith no graduation.

- Property area is to be find more in semi urban areas and minimum in rural areas.

# Exploratory Data Analysis:
Examining each variable with respect to target variable
![download](https://user-images.githubusercontent.com/90573789/172598670-068c18e0-b57c-4871-ab56-ead9a2afec61.png)


![download (1)](https://user-images.githubusercontent.com/90573789/172598697-66c2d65e-39eb-4ae0-8f04-168fa27c9fe1.png)

![download (2)](https://user-images.githubusercontent.com/90573789/172598739-b8ce037d-c0cb-4ff8-ace4-188fc473fc35.png)

![download (3)](https://user-images.githubusercontent.com/90573789/172598810-343eabb2-be82-4ab4-b773-95c48c805aea.png)

# Data Preprocessing:
The quality of the inputs in the model will decide the quality of your output. The following steps were taken to pre-process the data to feed into the prediction model.

- Missing Value Imputation
After understanding all the variable in the data, we can now impute the missing values and treat the outliers because missing data and outliers can have adverse effect on the model performance.

We consider the following values in all the features one by one.

For categorical variables: impute using mode.

For numerical variable: imputation using mean or median. Here, I have used median to impute the missing values as evident from Exploratory Data Analysis that loan amount has outliers, so the mean will not be the proper approach as it is highly affected by the presence of outliers.

- Outlier Treatment:
As LoanAmount contains outliers, it is rightly skewed. One way to remove this skewness is by doing the log transformation. As a result, we get a distribution like the normal distribution and does no affect the smaller values much but reduces the larger values.

# Building the Baseline Model:

For the baseline model, I have chosen a simple svm model to predict the loan status. The training data is divided into training and validation set. In this way we can validate our predictions as we have the true predictions for the validation part. The baseline logistic regression model has given an accuracy of 79%. From the classification report, the F-1 score obtained is 80%.

# Feature Engineering:
Based on the domain knowledge, we can come up with new features that might affect the target variable. We can come up with following new three features:

- Total Income: As evident from Exploratory Data Analysis, we will combine the Applicant Income and Coapplicant Income. If the total income is high, chances of loan approval might also be high.

- EMI: EMI is the monthly amount to be paid by the applicant to repay the loan. Idea behind making this variable is that people who have high EMI’s might find it difficult to pay back the loan. We can calculate EMI by taking the ratio of loan amount with respect to loan amount term.

- Balance Income: This is the income left after the EMI has been paid. Idea behind creating this variable is that if the value is high, the chances are high that a person will repay the loan and hence increasing the chances of loan approval.

Let us now drop the columns which we used to create these new features. Reason for doing this is, the correlation between those old features and these new features will be very high and logistic regression assumes that the variables are not highly correlated. We also want to remove the noise from the dataset, so removing correlated features will help in reducing the noise too.

