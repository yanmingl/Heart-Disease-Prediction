# Feature Analysis and Prediction of Heart Disease Patient
## Project Objective

This project, conducted as part of IE 7275: Data Mining in Engineering, aims to analyze the characteristics of patients with heart disease using exploratory data analysis to identify potential risk factors and to develop the best predictive model for heart disease. The models evaluated include K-Nearest Neighbor (KNN), tree-based models (Decision Tree, Boosted Tree, Random Forest), Logistic Regression, and Neural Network, all implemented using the Sklearn package. The ultimate goal is to inform the development of a health app for heart disease prevention and management.


## Data & Its Preprocessing

The [heart disease dataset](https://www.kaggle.com/sulianova/cardiovascular-disease-dataset) used in this project contains 70,000 records of patient data, with 11 attributes and one target column. Before analysis, we conducted data cleaning by dropping irrelevant features, such as patient IDs, and removing outliers using summary statistics, pair plots, and medical domain knowledge. We also performed data transformation, including sampling the dataset to 5,000 records for exploratory data analysis, one-hot encoding for the target, predictor normalization, and splitting the data into training and test sets with a ratio of 7:3 for model evaluation.

## Exploratory Data Analysis
We conducted an overall analysis of the distribution of numeric variables and the frequency of categorical features for heart disease patients compared to those without heart disease.

### Result
The plots below illustrate that heart disease patients tend to be older, shorter, and have higher body weight (A, B, C). Additionally, patients with heart disease tend to have higher systolic and diastolic blood pressure than the standard level of 120/80 mmHg for non-patients (D, E).

<img width="500" alt="image" src="https://user-images.githubusercontent.com/49282511/206949054-5826362e-f7ab-480a-b1f9-b48f83e7cef6.png"> 

We found that our dataset is approximately balanced, which is beneficial for model learning. Furthermore, we observed a significant increase in the percentage of heart disease patients with high cholesterol and high glucose levels, as shown in (B) and (C). In terms of lifestyle, heart disease patients tend to smoke less, consume less alcohol, and exercise less, as indicated in (D), (E), and (F).

<img width="500" alt="image" src="https://user-images.githubusercontent.com/49282511/206950845-84ca7e92-4f7b-4082-af10-58588e90722a.png">

Our findings suggest that maintaining a healthy body weight, regular blood pressure checks, and a healthy lifestyle may help reduce the risk of heart disease.

## Data Mining Models
We evaluated several models, including K-Nearest Neighbor (KNN), tree-based models (Decision Tree, Boosted Tree, Random Forest), Logistic Regression, and Neural Networks.

### Hyperparameter Tuning
For KNN, we chose k=5 based on the elbow method, which avoids overfitting. The model achieved an accuracy of 70.2%.

A Decision Tree was fitted on the dataset using a training size of 75% on both a sample of 5000 rows and the full dataset of 68,414 rows. Predictive accuracies of 64.1% and 63.5% were achieved, respectively, indicating that thousands of records are sufficient to detect potential patterns in the data. To improve accuracy, the model trained on the full dataset was used, but due to the instability of the tree, cross-validation was introduced to remove the effect of occasional split conditions. The average accuracy using 5-fold cross-validation on the full tree was 62.7%, which was assumed as the baseline metric.

Grid search was conducted on parameter combinations for the depth of the tree, minimum number of samples to split, and minimum impurity decrease to identify the best parameter choice for improving predictive accuracy. Applying the best parameters from the grid search method resulted in an approximately 10% increase in accuracy, from 62.7% to 73.2%. Boosted Tree and Random Forest ensemble learning methods achieved predictive accuracies of 72.4% each. 
| criterion |      random_state | max_depth | min_impurity_decrease |  min_samples_split |
| :---         | :----: | :----: | :----: | ---:|
| gini | 1 | 6 | 0.0004 | 10 |

Logistic Regression achieved an accuracy of 72.14% without any penalty, with the lasso method performing slightly better than the ridge method with an accuracy of 72.97% compared to 72.95% for ridge. Regularization plays an important role in ensuring robust representation of model performance.

The MLPClassifier from the sklearn package was used, with two hidden layers of five nodes each and other default hyperparameters, to achieve an overall accuracy of 73.47%, surpassing the previous accuracy of 73.05% achieved with one hidden layer and five nodes. Increasing the number of layers can lead to better accuracy to a certain extent.

### Model Comparison

Comparing the KNN, Tree-based method, and Logistic Regression, training a Neural Network under the best parameters achieved an optimal accuracy of 73.47%. The Decision Tree method had the second-highest accuracy of 73.2%, while 5-fold cross-validation on the full tree for the whole dataset resulted in the least accuracy of 62.7%. Using grid search to test different parameters resulted in a 10.5% accuracy increase for the Tree method. Overall, Neural Networks were found to be the best approach.

<img width="670" alt="image" src="https://user-images.githubusercontent.com/49282511/206948574-e21fe882-6831-4d21-8c2f-0e3175bc5f28.png">

# Future Work
Future work includes exploring sampling techniques to improve accuracy among models, using Random Forest based on the tuned decision tree, cross-validating logistic regression for stable value comparison, testing other parameters for the Neural Network such as the number of nodes, monitoring and avoiding overfitting, implementing classical machine algorithms from scratch, and deploying the model for real health applications such as monitoring people's conditions using wearable devices.
