# What Type of Customers Are More Likely to Churn?

## Credit Card Company Customer Churn Classification 
Author: Mikhaela Martin

### Project Objectives and Results:
1. Build a model that predicts the probability a user churns with given dataset. 

I tested four different classifier models: Logistic Regression, Gradient Boost, ADABoost, and Random Forest. I tested these models using all features in the original dataset and created separate models for feature selected data. The best model which maximized recall (79%) was the Random Forest model with eight features. 

The metric I wanted to optimize for was recall (TP / (TP + FN)) because false negatives led to worse consequences than false positives. A false negative occurs when the model predicts a customer to not churn when in fact they did. If the credit card company wanted to target users who were more likely to churn for a marketing campaign, they would probably rather target more people on the verge of leaving than less people. 

2. Identify key patterns and factors that determine attrition rate.

The three features which contributed most to the Random Forest model were: Total_Trans_Amt, Total_Trans_Ct, and Total_Revolving_Bal.

Total_Trans_Amt: The more transactions a customer makes, the less likely they will churn.

Total_Trans_Amt: The more credit a customer spends, the less likely they will churn.

Total_Revolving_Bal: The less credit a customer has left, the more likely they will churn.

### Model Evaluation and Interpretation

Refer to images file for relevant information pertaining to feature importance and precision_recall curves for all models trained.

**Feature Importance Table**
![](feature_importance.png "Title")
**Precision_Recall Curves All Features**
![](no_fs_models.png "Title")
**Precision_Recall Curves Feature Selected**
![](fs_models.png "Title")

 
### Dataset
We will be using a [credit card service company](https://www.kaggle.com/sakshigoyal7/credit-card-customers) dataset from Kaggle.  

### Bank Churners Table

- `Attrition_Flag`: Internal event (customer activity) variable - if the account is closed then 1 else 0
- `Customer_Age`: Demographic variable - Customer's Age in Years
- `Gender`: Demographic variable - M=Male, F=Female
- `Dependent_count`: Demographic variable - Number of dependents
- `Education_Level`: Demographic variable - Educational Qualification of the account holder (example: high school, college graduate, etc.)
- `Marital_Status`: Demographic variable - Married, Single, Divorced, Unknown
- `Income_Category`: Demographic variable - Annual Income Category of the account holder (< $40K, $40K - 60K, $60K - $80K, $80K-$120K, > $120K, Unknown)
- `Card_Category`: Product Variable - Type of Card (Blue, Silver, Gold, Platinum)
- `Months_on_book`: Period of relationship with bank
- `Total_Relationship_Count`: Total no. of products held by the customer
- `Months_Inactive_12_mon`: No. of months inactive in the last 12 months
- `Contacts_Count_12_mon`: No. of Contacts in the last 12 months
- `Credit_Limit`: Credit Limit on the Credit Card
- `Total_Revolving_Bal`: Total Revolving Balance on the Credit Card
- `Avg_Open_To_Buy`: Open to Buy* Credit Line (Average of last 12 months)
- `Total_Amt_Chng_Q4_Q1`: Change in Transaction Amount (Q4 over Q1)
- `Total_Trans_Amt`: Total Transaction Amount (Last 12 months)
- `Total_Trans_Ct`: Total Transaction Count (Last 12 months)
- `Total_Ct_Chng_Q4_Q1`: Change in Transaction Count (Q4 over Q1) 
- `Avg_Utilization_Ratio`: Average Card Utilization Ratio***


*Open-to-buy: The difference between the credit limit assigned to a cardholder account and the present balance on the account.

***Average Card Utilization Ratio: Amount client owes divided by credit limit. (Total_Revolving_Bal / Credit_Limit)


### Methods
- Data Cleaning: Numpy, Pandas, Random Imputation
- Exploratory Data Analysis: Matplotlib, Seaborn, Hypothesis Testing
- Feature Selection: Recursive Feature Elimination
- Model Building: Logistic Regression, Gradient Boost, ADABoost, Random Forest
- Model Evaluation: Precision, Recall, Classification Report, Feature Importance

### Why does churn matter?
Companies want to maximize ther profits which takes both revenue and costs into account. There are three ways to increase revenue and we will go over why increasing retention rate is the most crucial. 

1. Enhance or improve current products. While it is important to drive innovation forward, creating new features or products can actually take a lot of time, creativity, resources, and people to produce good results.
2. Acquire new customers. Expanding your customer base seems like common sense, but this method can be hard for well-established companies to utilize. Also, identifying and advertising to targeted demographies can be costly when you have limited information.
3. Lowering churn. Identifying people in your company who are more prone to churning can be a lot easier because you have the data 

Acquiring new customers costs much more than retaining them. As stated, we will focus on how a company can identify whether a customer can churn. Once a model that can identify the types of customers who are likely to churn or provide a probability of people who are likely to churn at any given time, business solutions such as issuing a retention campaign or promotion can be put into place to target those most prone to churning.


### Why Is There a Spike At Months_on_book = 36?
After investigating this, I am unsure. But, features such as gender, dependent count, and months_inactive_12_mon are correlated. Females, people with more dependents, and people less active in the last twelve months are more likely to have a months_on_book value of 36.

## Further Analysis:
If I had more data about the specific time users attrited, I could have used a time-series model to predict the proability of churn of each user at different phases of their relationship with the credit card company. I could have also created a function which predicted every user's expected time to churn.

