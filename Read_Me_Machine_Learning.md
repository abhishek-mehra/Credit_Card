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

Since the data is imbalanced. Providing the scale_pos_weight balances the weight of the postive and the negative classes. There was a significant improvemnts in the scores. This improved the separatabilty between the target class.

**precison_mean = 0.88, recall_mean= 0.944, f1_score_mean=0.911,roc_mean= 0.96**


#### Holding out a test set to check overfitting and under fitting, Finding the spot of bias and variance tradeoff


I took 10% of the data as test data. Trained the data on the training set and predicted on the test set.


