# Credit Card Customers

## The dataset

The dataset is about a bank's credit card services, which customers are discontinuing. This was an exciting project for me because I have had a credit card for a long  and this is a good business challenge and an opportunity to learn more about credit cards.

The dataset contains information about the customer, including their age, gender, income bracket, and credit card characteristics like their total revolving debt, credit limit, months of inactivity, and open to buy etc. The dependent variable is attrition which tells us whether the customer is still associated with the services or has left the credit card service.

Dataset Source:https://www.kaggle.com/datasets/sakshigoyal7/credit-card-customers

## Business Problem

Clients are departing from a bank’s credit card services (I could not find particular details of the bank or the credit card services). The bank manager is interested in learning why consumers are leaving their services and what can be done about it. I would perform descriptive and predictive analysis to find what factors contribute to customers’ churn.

## Information that I will try to extract from the dataset.

Q. What is the profile of the existing bank customers, for example what is the average age, salaries, type of credit card held by the customers.

Q. What is the profile of customers leaving the credit card services.

Q. What factors differentiate between customers who stay and those who leave the services.

Q. Finding which customers are likely to leave the services.

Q. What steps can be taken to make the customers stay with credit card services.

## Breakdown:

## EDA :

After importing the dataset, I performed exploratory data analysis using Pandas functions such as head and summary to get an overview of the data frame.

Performing statistical analysis I observed the profiles of the customers. This included their ages, gender, education level, marital status, income category, and credit card category. 

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

## Multivariate analysis observation

Plotting two features with dependent variables showed some interesting findings. Customers who spent more money left the services less frequently.

![Capture.JPG](http://localhost:8888/lab/tree/Desktop/Workspace/Projects/Credit_Card/Images/scatter_plot_transaction_count_amount.jpg)


This is again verified by plotting the total revolving balance and average utilization ratio scatter plot against customer attrition status. Customers who have a lower average utilization and total revolving balance are more likely to discontinue use of the services.




## Conclusions


- As seen in the scatter plot of Transaction amount and transaction count Customers with low transactions, there are more churning.  We can therefore increase the retention of customers by involving the customers in transactions by giving them attractive offers.

- As seen in frequency plot of the Customers with salary less 40k are the highest number of members in the services , more focus can be given on their retention. Giving the customers with less salary more offers to stay.


Further I will utilise machine learning models to predict the label class. And what features are most dominant in predicting the target class.