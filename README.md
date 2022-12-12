## Project Objective

A course project for IE 7275: Data Mining in Engineering to identify the influential factors that may contribute to one's heart disease using exploratory data analysis, and figure out the best model that can be used for prediction of heart disease among K-Nearest Neighbor (KNN), Trees-based (Decision Tree, Boosted Tree, Random Forest), Logistic Regression, and Neural Network in Sklearn package. 


## Data & Its Preprocessing

The [heart disease dataset](https://www.kaggle.com/sulianova/cardiovascular-disease-dataset) consists of 70000 records of patient data, 11 attributes and one target column. At first, we clean the data by dropping meaningless feature like ID, removing outliers under summary statistics, pair plot, and searchable medical domain-knowledge. Then, we conduct data transformation, such as data sampling for 5000 records, one hot-encoding for the target, data normalization for the predictor, and data split to train/test with a ratio of 7/3 for further models.

## Exploratory Data Analysis
We conduct an overall analysis on quantifying numeric variable distribution or class frequency of categorical features for subjects who have heart disease compared to those who do not.

### Result
Plots A, B, and C below illustrate that - high age, low height, and high weight are characteristics of a heart disease patient. For normal people, the systolic blood pressure versus diastolic blood pressure is 120/80 which meets our standards in medical settings. However, those two pressures increase if the subject has heart disease, like D, E. 

<img width="500" alt="image" src="https://user-images.githubusercontent.com/49282511/206949054-5826362e-f7ab-480a-b1f9-b48f83e7cef6.png"> 

Our data is approximately balanced, as A(below) shows, which enacts a superior learning performance for the further method. It can be noticed that the percentage of patients with high cholesterol and high glucose significantly increases in the case where the person has heart disease (B, C). This also deepens our understanding of heart disease. Due to poor body conditions which result from having heart disease, patients tend to smoke less, have alcohol intake and work out less, like D, E, F.

<img width="500" alt="image" src="https://user-images.githubusercontent.com/49282511/206950845-84ca7e92-4f7b-4082-af10-58588e90722a.png">


## Data Mining Models
To highlight, we implemented the KNN model on our dataset and got an accuracy of 70.2% when k equals 5. The reason why we chose k=5 is to avoid overfitting with an application of elbow method by observing the graph, training/test accuracy vs. k values. A full Decision Tree is fitted on the whole dataset with 68,414 rows after removing the outliers. As the tree is unstable, cross-validation is introduced for the purpose of removing the effect of the occasional split conditions. Grid search on the parameters combinations of the depth of the tree, minimum number of samples to split, and minimum impurity decrease are conducted for the best parameter choice for improving the predictive accuracy. Boosted tree as an alternative is implemented. Ensemble learning methods like Random forest are also tested. The predictive accuracy of Logistic Regression is 70.2% without any penalty. The accuracy improves with the lasso method and it performs slightly better than the ridge method with higher accuracy of 72.97% than 72.95% from the ridge method. We apply the MLPClassifier from sklearn package by assigning two hidden layers with five nodes each and other default hyperparameters to achieve 73.47% overall accuracy., with the previous accuracy achieved being 73.35% from one hidden layer and 5 nodes

Compared to the KNN, Tree-based method and Logistic Regression, the optimal accuracy of 73.47% is obtained when training a Neural Network under the best parameters, where the parameters used were 2 hidden layers with 5 nodes each and activation function being logistic. The second highest was the Decision tree with an accuracy of 73.2% and the least accuracy obtained using 5-fold cross-validation on the full tree for the whole dataset with a size of 68,414 rows is 62.7%. By trying different parameters using grid search methods, there was an accuracy increase of 10.5% for the Tree. Overall, Neural Networks prove to be the best among all.

<img width="452" alt="image" src="https://user-images.githubusercontent.com/49282511/206948574-e21fe882-6831-4d21-8c2f-0e3175bc5f28.png">
