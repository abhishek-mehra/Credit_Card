### Credit Card Customers

#### About the dataset

Source:https://www.kaggle.com/datasets/sakshigoyal7/credit-card-customers



#### Business Problem, Questions to be solved
Customers are leaving bank credit card services. The bank manager wants to know the causes behind the customers churning. The dataset provides customer details such as age,gender,income category, and credit card related information such as total revolving balance, credit limit, months inactive,open to but.


#### Questions:
1.What type of cutomers are leaving the credit card services.  
2.What are particular characteric/features of customers who leave the services. 
3.What customers stay in the services.    
4.What causes the cutomers to leave.  
5.What can be done to increase the retention rate.  

#### Breakdwon:

##### EDA : 
Importing the dataset and performing Exploratory data analysis. The data has 10127 rows and 23 features. There were no null values in the dataset. Two columns were removed from the dataframe since they were not relevant to the dataset

Statistial anlysis of numerical variables was carried out. There are 13 numerical feature and 6 categorical features.The statistical analysis reveals the Customer_Age, dependent count ,months on book, total relationship count.

Description of Categorical Variables showed various levels in the varibles. Education had 7 unique levels, maritial stauts had 4. there are 6 income categories on total and 4 card categories


##### Visualizations:
Plotting distribution of numerical features show the normal distribution of cutomers age,monthson book,avg utilization ratio,total amount change. bi modal and multi modal distribution of other numerical features is observed.

Correlation graph revelaved the collinearity between various variables. total revolving balance and avg utilization ratio has pearson correlation cofficient of 0.69 . 

##### Multi variate analysis

Plotting 2 features with dependent variables showed some interesting finding. customers with higer transaction amouts and higher transaction amount were leaving the services less.

This is again varified by plotting total revolving balance and avg utilazation ratio scatter plot made against customer attrition status. Customers with lower avg utilization and total revolving balance are more likely to leave the services.


##### Frequency plots

Categorical variable fequency plot show the number of customers distribution as per attrition,gender maritial status,income categories.



#### Feature engineering
The computer understands numbers. Numerical features are already in the number forms. I changed the Caterorical variables into 'category' type variable of pandas.https://pandas.pydata.org/docs/user_guide/categorical.html

##### train test split.
Since there was only one dataset provided , it had to be split into training and validation dataset. This is neccessary so as to evaluate our machine learning model. This dataset should be unseen by the model as it will help to find if our model has overfit the data

##### machine learning model

Random forest clasifier

Xgboost classifier




##### feature importance
As per Random forest Total_Trans_Amt, Total_Trans_Ct are prominent features with 0.175 and 0.168 respectively.


- As per XgbClassifier Total_Trans_Ct with 0.230880 and  Total_Revolving_Bal with 0.156581 are the most prominent features.  Total_Relationship_Count with feature importance 0.135454 is also an importance feature.



##### Learning

Correlation-

Pearson coeefeicent - a single number representing increasing or decreasing relationship between pair of numbers.  


Precsion- precision fraction of correctly identified postives out of all predicted positives, how many are truly postive out of the predicted postives

Example: Consider 100 eggs. Out of 100 eggs only 20 are boiled. We have to predict the number of boiled eggs. 
Consider we predicted 10 eggs were boiled. Out of these 10 eggs only 6 were boiled and 4 were raw.

Precision - how many eggs were truly boiled out of the predicted - 6 of 10

recall - how many eggs were truly boiled out of all the boiled eggs 6 of 20

Recall fraction of correctly identified positives out of all actual positives, how many correctly identified postives out of all the truly postives

Why accuracy is not always a good measure and why we need precision and recall
example: hypothetical-consider we are predicting covid cases at an airport. out of 100 people 10 are covid postive. 90 are negative. consider our model predicts that all the covid cases are negative our accuray would be 90. since we predicted only 10 cases wrongly. Here accuracy metric wont be sufficent .
there we require somehting more than accuracy. precision and recall comes into play here.




##### questions answered

1. customers with low trasnactions leave.
solution: increase the customers usage levels by initially giving them tempting offers.