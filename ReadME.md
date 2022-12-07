# Credit Card Customers

## The dataset

The dataset is about a bank's credit card services, which customers are discontinuing. This was an exciting project for me because I have had a credit card for a long and this is a good business challenge and an opportunity to learn more about credit cards.

The dataset contains information about the customer, including their age, gender, income bracket, and credit card characteristics like their total revolving debt, credit limit, months of inactivity, and open to buy etc. The dependent variable is attrition which tells us whether the customer is still associated with the services or has left the credit card service.

Dataset Source:https://www.kaggle.com/datasets/sakshigoyal7/credit-card-customers

## Business Problem

Clients are departing from a bank’s credit card services (I could not find particular details of the bank or the credit card services). The bank manager is interested in learning why consumers are leaving their services and what can be done about it. I would perform descriptive and predictive analysis to find out what factors contribute to customers’ churn.

## Information that I will try to extract from the dataset.

Q. What is the profile of the existing bank customers, for example, what is the average age, salaries, and type of credit card held by the customers.

Q. What is the profile of customers leaving credit card services.

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



### Machine Learning on Credit card Churning dataset

#### I Created Functions to simplyfy my repeated tasks. I created functions for :


 1. Category data type conversion,  
 
 2. Training-validation split,  
 
 3. Stratified Cross validation,  
  
 4. Model training and Metrics, 
 
 5. Removing outliers,  
 
 6. Standard Scaler

  This would help me to call the function iterativey and perform experiments to improve on my machine learning models.


#### Best base model based on train - Train-Validation split.

I trained multiple RandomForestClassifier models on training data i.e 80% of the whole dataset. 
to maintain the original ratio of the samples in the target class stratified the dataset. Since the target class is imbalanced stratify will provide the same percentage in the split dataset. 


In the RandomForest Clasifier the number of trees was varied, to determine the better performing model. The best metric was obtained was precision_score = 0.943, recall_score = 0.868, roc_score = 0.929, f1_score = 0.904 with number of trees set to 500.

In this experiment the data was not trained on the whole dataset. The validation set kept aside which may hold insghts was not used to train the model. Hence to overcome this I shifted to Stratified Cross Validation to evaluate my model.



#### Best base model base on train - Stratified Cross Validation

I trained Random Forest Classifier on multiple trees to get best base model with:
precison_mean = 0.931, recall_mean= 0.799, f1_score_mean=0.86,roc_mean= 0.894 on 500 number of estimators.

Further I will perform modifications to improve my model.


#### Feature Transformation On base model using Cross validation

##### 1. Treating Outliers

Outliers affect the the machine learning . I removed the outliers from the numerial features with 1.5 times the Inter quartile range. There was no effect in the model ouputs. I decided to keep the oultier since they provide key insights to the training.

##### 2. Standard Scalar 

I used a standard scaler on the numerical feature. This is done to ensure that the numerical values are consistent. It removes the scale of the various features being measured and places all values on an equal scale. This will allow the model to gain more insights from the data.


##### 3. Feature Addition

On adding a new feature of average transaction the model performed better in f1 score and roc auc on the baseline model.This added feature is helping the model to make better predictions.

#### 4. Combining best feature transformation

I combined feature engineering and Standard Scalar transformation into a function. This combined transformation will be used further in the experiments since they are adding value to the model

**ADA
precison_mean = 0.915, recall_mean= 0.807, f1_score_mean=0.858,roc_mean= 0.896**

**RandomForest
precison_mean = 0.936, recall_mean= 0.824, f1_score_mean=0.877,roc_mean= 0.907**

**XGBoost
precison_mean = 0.932, recall_mean= 0.892, f1_score_mean=0.911,roc_mean= 0.94**



#### Selecting the best model out of ADABoost, Random forest and XGBoost classifier

XGBoost performed better than the rest of the models. 


I will further vary the parameters of the XGBoostclasifer to improve on my model


#### Best hyperparametere for XGBoost baseline model

##### Learning rate -

This determines how fast or how slow our model learns from the past errors. Slower learning rate is usually preffered since it includes more data points to learn from.

**precison_mean = 0.933, recall_mean= 0.892, f1_score_mean=0.912,roc_mean= 0.94**

##### Controlling overfitting

###### Depth of tree - 

Greater the depth of the tree more is its complexity and hence more are the chances of its overfiting
By reducing the number of trees improves the scores here.

**precison_mean = 0.937, recall_mean= 0.891, f1_score_mean=0.913,roc_mean= 0.94**



###### Scale_pos_weight

Since the data is imbalanced. Providing the scale_pos_weight balances the weight of the positive and the negative classes. There were significant improvements in the scores. This improved the separability between the target class.

**precison_mean = 0.88, recall_mean= 0.944, f1_score_mean=0.911,roc_mean= 0.96**


#### Holding out a test set to check overfitting and under fitting, Finding the spot of bias and variance tradeoff


I took 10% of the data as test data. Trained the data on the training set and predicted on the test set.


