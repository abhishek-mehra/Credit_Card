### Credit Card Customers

### About the dataset

The dataset relates to a bank’s credit card services, which clients are abandoning. I found this to be an intriguing assignment, as I have had a credit card for myself for a while. This would be an opportunity to learn more about credit cards, and it is a good business problem. The dataset contains information about the customer, including their age, gender, income bracket, and credit card characteristics like their total revolving debt, credit limit, months of inactivity, and open to buy etc. The dependent variable is attrition which tells us whether the customer is still associated with the services or has left the credit card service.

Dataset Source:https://www.kaggle.com/datasets/sakshigoyal7/credit-card-customers

### Business Problem

Clients are departing from a bank’s credit card services (I could not find particular details of the bank or the credit card services). The bank manager is interested in learning why consumers are leaving their services and what can be done about it. I would perform descriptive and predictive analysis to find what factors contribute to customers’ churn.

### Information that I will try to extract from the dataset.

Q. What is the profile of the existing bank customers, for example what is the average age, salaries, type of credit card held by the customers.

Q. What is the profile of customers leaving the credit card services.

Q. What factors differentiate between customers who stay and those who leave the services.

Q. Finding which customers will go attrition

Q. What steps can be taken to make the customers stay with credit card services.

### Breakdown:

### EDA :

After importing the dataset, I performed exploratory data analysis using Pandas functions such as head and summary to get an overview of the data frame.

performing statistical analysis I observed the profiles of the customers. This included their ages, gender, education level, marital status, income category, and credit card category. 

![Capture.JPG](http://localhost:8888/lab/tree/Desktop/Workspace/Projects/Credit_Card/Images/Capture.jpg)

Observations:

- The existing customers stand at 83% of all the customers, 16% customers left the credit card services.
- Major customers were the graduate students. They occupied 30.8% of all the customers
- The next attribute I observed was salary range , 35% of the customers earned less than $40k.
- 93% of the customers are blue card holders.

Our dependent variable is under the column Attrition_Flag, which tells whether the customer is still with the service or has left it.

Observations: - Most of the customers leaving the services are under $40k salary range.

- There is equal ratio of married and single people leaving the services. No deductions could be found in the relationship and attrition
- Since a lot of customers  belong to 40$k salary range they were also in the maximum category of leaving the services.

### multivariate analysis observation

Plotting two features with dependent variables showed some interesting findings. Customers who spent more money left the services less frequently.

This is again verified by plotting the total revolving balance and average utilization ratio scatter plot against customer attrition status. Customers who have a lower average utilization and total revolving balance are more likely to discontinue use of the services.

### Feature engineering

The computer understands numbers, and we need to convert our categorical features for it to understand . Numerical features are already in the number forms. I changed the categorical variables into ‘category’ type variable for pandas. https://pandas.pydata.org/docs/user_guide/categorical.html

### Train test split.

Since there was only one dataset provided, it had to be split into a training dataset and a validation dataset. This is necessary so as to evaluate our machine learning model.

### Machine learning models

I chose the Random Forest classifier and the XGBoost classifier as they are the most widely used models these days in Kaggle competitions. While going through other notebooks, they are the best ML models for tabular forms of data.

I chose the default parameters as the hyperparameter for the machine learning models. This gave me an F1 score of 0.9. A F1 score near 1 is considered good. This means that the model is able to predict both the positive and negative cases correctly. https://stephenallwright.com/good-f1-score/

### Feature importance

Attrition revolved around numerical features especially transaction amount-
This can mean things like - those who want to leave do not do transactions, there is something stopping them from doing transaction.

- The greater the feature's importance, the more important the feature is. - As per Random Forest, Total_Trans_Amt, Total_Trans_Ct are prominent features with 0.175 and 0.168, respectively.

- As per XgbClassifier Total_Trans_Ct with 0.230880 and Total_Revolving_Bal with 0.156581 are the most prominent features. Total_Relationship_Count with feature importance 0.135454 is also an importance feature.

### Conclusions


- As seen in the scatter plot of Transaction amount and transaction count Customers with low transactions, there are more churning. The predictive models also in the higher transaction count and transaction amount there is less churning. We can therefore increase the retention of customers by involving the customers in transactions by giving them attractive offers.

- As seen in frequency plot of the Customers with salary less 40k are the highest number of members in the services , more focus can be given on their retention. Giving the customers with less salary more offers to stay.


These are some traits that were observed to increase the amount of atritted accounts:

Generally low average transaction amounts over the last 12 months
Generally low average utilization ratio
Generally low transaction amount and count change from the end of the year (Q4) compared to the start of the year (Q1)
Generally low transaction count over the last 12 months
Generally low transaction amount over the last 12 months
Generally low average open to buy value over the last 12 months
Generally low revolving balance
Generally low credit limit
Normally 3 months longest inactive for the last 12 months
Note: these traits are also found within persons who have existing credit card accounts. However, these can be traits that can classify what makes a person attrite.