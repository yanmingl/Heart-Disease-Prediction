## Project Objective

A course project for IE 7275: Data Mining in Engineering to analyze the characteristic of subjects who have heart disease using exploratory data analysis to avoid being such a part of patients, and figure out the best model that can be used for prediction of heart disease among K-Nearest Neighbor (KNN), Trees-based (Decision Tree, Boosted Tree, Random Forest), Logistic Regression, and Neural Network in Sklearn package for further health app development. 


## Data & Its Preprocessing

The [heart disease dataset](https://www.kaggle.com/sulianova/cardiovascular-disease-dataset) consists of 70000 records of patient data, 11 attributes, and one target column. At first, we clean the data by dropping meaningless features like ID and removing outliers under summary statistics, pair plots, and searchable medical domain knowledge. Then, we conduct data transformation, such as data sampling for 5000 records for EDA, one hot-encoding for the target, data normalization for the predictor, and data split to train/test with a ratio of 7/3 for further models.

## Exploratory Data Analysis
We conduct an overall analysis on quantifying numeric variable distribution or class frequency of categorical features for subjects who have heart disease compared to those who do not.

### Result
Plots A, B, and C below illustrate that - high age, low height, and high weight are characteristics of a heart disease patient. For normal people, the systolic blood pressure versus diastolic blood pressure is 120/80 which meets our standards in medical settings. However, those two pressures increase if the subject has heart disease, like D, and E. 

<img width="500" alt="image" src="https://user-images.githubusercontent.com/49282511/206949054-5826362e-f7ab-480a-b1f9-b48f83e7cef6.png"> 

Our data is approximately balanced, as A(below) shows, which enacts a superior learning performance for the further method. It can be noticed that the percentage of patients with high cholesterol and high glucose significantly increases in the case where the person has heart disease (B, C). This also deepens our understanding of heart disease. Due to poor body conditions which result from having heart disease, patients tend to smoke less, have alcohol intake, and work out less, like D, E, and F.

<img width="500" alt="image" src="https://user-images.githubusercontent.com/49282511/206950845-84ca7e92-4f7b-4082-af10-58588e90722a.png">

How can you lower the risk or even avoid being a patient with heart disease can be concluded as the past two paragraphs told us. We may be unable to control our age or height, but we can do fitness to manage our weight and regularly test our blood pressure to stay at a relative side. 

## Data Mining Models
They are K-Nearest Neighbor (KNN), Trees-based (Decision Tree, Boosted Tree, Random Forest), Logistic Regression, and Neural Networks.

### Hyperparameter Tuning
To highlight, we implemented the KNN model on our sampled dataset and got an accuracy of 70.2% when k equals 5. The reason why we chose k=5 is to avoid overfitting with an application of the elbow method by observing the graph, and training/test accuracy vs. k values. 

A full Decision Tree is fitted on the dataset with a training size of 75% on both sample (5000 rows) and the full data set (68,414 rows). The predictive accuracies are 64.1% and 63.5% respectively. The relatively small performance illustrates that thousands of records are good enough to detect potential patterns in the data. We improve the accuracy based on the model trained on the full data set, and full data will be used in the following models. As the tree is unstable, cross-validation is introduced for the purpose of removing the effect of the occasional split conditions. The average accuracy using 5-fold cross-validation on the full tree is 62.7%, and we assume this metric as a baseline.

Grid search on the parameters combinations of the depth of the tree, minimum number of samples to split, and minimum impurity decrease are conducted for the best parameter choice for improving the predictive accuracy. We observed a ~10% increase in accuracy, from 62.7% to 73.2%, after we applied the best parameter using the grid search method. Below are the parameters. The predictive accuracy that we got from the Boosted Tree method with 200 estimators is 72.4%. For Ensemble learning methods like Random forest, it is 72.4% as well. 

| criterion |      random_state | max_depth | min_impurity_decrease |  min_samples_split |
| :---         | :----: | :----: | :----: | ---:|
| gini | 1 | 6 | 0.0004 | 10 |

The predictive accuracy of Logistic Regression is 72.14% without any penalty. The accuracy improves with the lasso method and it performs slightly better than the ridge method with higher accuracy of 72.97% than 72.95% from the ridge method. Regularization matters in a robust representation of the model performance.

We apply the MLPClassifier from the sklearn package by assigning two hidden layers with five nodes each and other default hyperparameters to achieve 73.47% overall accuracy, with the previous accuracy achieved being 73.05% from one hidden layer and 5 nodes. It is worthwhile to increase the model layers for better accuracy to some extent.

### Model Comparison

Compared to the KNN, Tree-based method, and Logistic Regression, the optimal accuracy of 73.47% is obtained when training a Neural Network under the best parameters, where the parameters used were 2 hidden layers with 5 nodes each and the activation function is logistic. The second highest was the Decision tree with an accuracy of 73.2% and the least accuracy was obtained using 5-fold cross-validation on the full tree for the whole dataset with a size of 68,414 rows is 62.7%. By trying different parameters using grid search methods, there was an accuracy increase of 10.5% for the Tree. Overall, Neural Networks prove to be the best of all.

<img width="670" alt="image" src="https://user-images.githubusercontent.com/49282511/206948574-e21fe882-6831-4d21-8c2f-0e3175bc5f28.png">

# Future Work
- In this project, we did not explore the sampling techniques on the final accuracy among models, just stopped after a shallow trail in trees and using the full cleaned dataset. Go ahead and do it!
- Random Forest and the Boosted Tree are expected to achieve a better performance than the Decision Tree. Is it possible to use the Random Forest based on the tuned decision tree?
- The accuracy differs slightly between the vanilla Logistic Regression and its variants with regularization. Why not use cross-validation here for a stable value comparison?
- We just tuned the number of layers in our Neural Network, and try other parameters like the number of nodes as well.
- Are our models overfitting or not? Think about the tradeoff issue, monitor them, and avoid them.
- Not being a toolkit driver, try to implement those classical machine algorithms from the scratch.
- Deploy the model for real health application like apple watch, for monitering people's conditions and gave them a signal for probability of being a patient with heart disease. 
