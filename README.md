# COVID-19TEST
Epidemiology is the scientific discipline that studies the determinants of health-related states or events in specified populations. Classical methods of Epidemiology such as modeling assumptions become difficult to achieve with large scale-datasets, however, machine learning has the potential to answer these questions. In this thesis, we illustrate the effectiveness of machine learning to forecast and classify in the fields of Environmental Epidemiology and Health Epidemiology. The same pre-existing conditions that increase mortality rates of COVID-19 are the same diseases that are also affected by long-term exposure to air pollution. Low-income populations suffer the most from air pollution disparity and are often burdened with long-term health effects. It is with the utmost importance that we continue investigating the relationship between air pollution and health to enforce existing air pollution regulations and ensure the protection of human health both during and after the COVID-19 pandemic. To study the relation of COVID-19 and air pollution we propose a refined data collection that uses Particulate Matter data and Mexico’s COVID-19 cases public dataset. We approach the classification of COVID-19 diagnosis by using three traditional generalized linear regression models (logistic, probit, and complementary log-log) and two machine learning techniques (random forest classifier and artificial neural network). We use Python to produce the COVID-19 diagnoses classifiers.
## Data Introduction

## Data Cleaning and Resampling
An unbalanced dataset has one class represented better than the other classes. Since the Mexico COVID-19 dataset had a larger number of negative COVID-19 cases than positive ones, the data were highly unbalanced as demonstrated by the bar chart below.

![image](https://user-images.githubusercontent.com/32992857/144300564-52a95c80-6ad8-417f-a108-e8e99671b644.png)

 We applied a type of data augmentation referred to as Synthetic Minority Oversampling Technique or SMOTE. Having a bias toward positive COVID-19 cases doesn’t allow effective learning of the model’s decision boundary.  To address this issue, SMOTE oversamples the minority class which in this case is the positive COVID-19 result. First, we split the dataset into a training set and a testing set for cross-validation. With the testing size being 20% of the data and the training set being 80% of the data. After that, we fit the SMOTE algorithm to resample the data. 
 
 Raw data had to be preprocessed before being used in statistical analysis or machine learning models. For the Mexico COVID-19 dataset, the column names were translated from Spanish to English. There were no missing values in the dataset, however, when the datasets were merged to account for PM2.5 and PM10 there were missing values in both PM2.5 and PM10. Imputation by the column means was used to replace the missing values in each column. To check if any values were missing after we imputated the column means we summed up the null values for each column and calculated 0 missing values in the dataset.To check for outliers we used the Inter quartile range (IQR) method. We found each quartile and set a lower limit of Q1-1.5*IQR and an upper limit of Q3+1.5*IQR. Any data point beyond this range was defined as an outlier and then removed. We also looked at the correlation map of the data to see the significance of our predictors and observed the comorbid diseases were highly correlated to each other.

## Binary Logistic Regression Model
Suppose the response variable Y assumes only two values which can be coded as 0 or 1. 0 is a negative COVID-19 result and 1 is a positive COVID-19 result. This type of variable is therefore termed binary. A binary logistic regression models the probability that the response, Y , is positive. 

**Logistic Regression Summary table**

![image](https://user-images.githubusercontent.com/32992857/144290139-a4dc3dbd-4d17-40ab-acac-1608e2f14ba1.png)

From the Summary table of the logistic regression model we observed that Intubated,  Lan_Indig, Diabetes, EPOC, Asthma, Hypertension, Chronic_Renal, Tobacco were not significant predictors since their p value was greater than 0.05 and were therefore removed from the model before calculating the confusion matrix.

**Confusion Matrix for Binary Logistic Regression Model**

| **Correctly Classified** | **33866** | **64%** |
| --- | --- | --- |
| **Incorrectly Classified** | 18736 | 36% |

**Logistic Regression Model Metric evaluators**

| Accuracy | Precision | MCC |
| --- | --- | --- |
| 64% | 36% | 25% |


## Binary Probit Regression Model
Probit model is often used as an alternative to a binary logistic regression. In the Probit model, the probability \pi=P(Y=1) is regressed on a set of predictors x_1,\ \ldots,\ x_k through the following relation:

**Probit Regression Summary table**

![image](https://user-images.githubusercontent.com/32992857/144289803-ce883878-6b6f-4769-b312-9a9c43ee727e.png)

From the Summary table of the Probit model we observe Sex, Hos_Clin, Pneumonia, Nationality, Pregnant, Immuno, Obesity, Contact_Covid, ICU, PM10, PM2.5, and difference are statistically significant since their p value was less than 0.05. The insignificant features Intubated,  Lan_Indig, Diabetes, EPOC, Asthma, Hypertension, Chronic_Renal, Tobacco were therefore removed from the model before calculating the confusion matrix. 

**Confusion Matrix for Binary Probit Regression Model**

| **Correctly Classified**   | **33866** | **64%** |
| -------------------------- | --------- | ------- |
| **Incorrectly Classified** | 18736     | 36%     |


**Probit Regression Model Metric evaluators**

| Accuracy | Precision | MCC |
| -------- | --------- | --- |
| 64%      | 36%       | 25% |

## Binary Complementary Log-log Model
The complementary log-log regression models \pi=P(Y=1) as a function of a set of predictors x_1,\ \ldots,\ x_k through the following formula:

**Complementary Log-log Regression Summary table**

![image](https://user-images.githubusercontent.com/32992857/144290691-80d8f46b-29bc-4928-85ee-3995d074a215.png)

From the Summary table of Complementary Log-Log we observe Sex, Hos_Clin, Pneumonia, Nationality, Pregnant, Immuno, Obesity, Contact_Covid, ICU, PM10, PM2.5, and difference are statistically significant since their p value was less than 0.05. The insignificant features Intubated,  Lan_Indig, Diabetes, EPOC, Asthma, Hypertension, Chronic_Renal, Tobacco were therefore removed from the model before calculating the confusion matrix. 

**Confusion Matrix for Binary Complementary Log-log Regression Model**

| **Correctly Classified**   | **33866** | **64%** |
| -------------------------- | --------- | ------- |
| **Incorrectly Classified** | 18736     | 36%     |

**Complementary Log-log Regression Model Metric evaluators**

| Accuracy | Precision | MCC |
| -------- | --------- | --- |
| 64%      | 55%       | 24% |

## Random Forest 
A Random Forest is a combination of a series of decision tree structure classifiers. Based on their COVID-19 results, the Random Forest Algorithm was applied to Mexico’s COVID-19 data. To evaluate which predictors were important we used the Sklearn package and called on feature importance. We plotted the top 10 feature importances from the random forest algorithm as demonstrated in the plot below. 
By default, the number of trees in the forest is 100. The greater the number of tree splits, the more information the random forest captures about the dataset. However, if the maximum depth is too high it can increase overfitting. Therefore, knowing these limitations, by trial and error,  we set the maximum depth of each tree to 6. The top 10 important features were Sex, Intubated, PM2.5, Pneumonia, Tobacco, PM10, Lan_Indig, Cardiovascular, ICU. 

<img src="https://user-images.githubusercontent.com/32992857/144293987-a495b2b9-7a4d-4d8a-b24a-5cf266df3cd6.png" width="600" height="400">

**Confusion Matrix for Random Forest Model**

| **Correctly Classified**   | **34940** | **66%** |
| -------------------------- | --------- | ------- |
| **Incorrectly Classified** | 17662     | 34%     |


**Random Forest Model Metric evaluators**

| Accuracy | Precision | MCC |
| -------- | --------- | --- |
| 66%      | 58%       | 28% |

## Artificial Neural Network

<img src="https://user-images.githubusercontent.com/32992857/144294720-63732156-8ef3-42a9-b7d5-370c53ec6cc8.png" width="400" height="600">

The features from the Mexico COVID-19 dataset are used to predict the class COVID-19 diagnosis. The COVID-19 diagnosis is predicted in the output node. In the neural network, the input layer and the three hidden layers were given the activation function ‘Relu’, to increase efficiency. Adding more hidden layers allows the complexity of the classification functions to be found. The output node had the sigmoid function to ensure that the ANN output classifies the class into 0 or 1.  Since the ANN is classifying a binary output,we used the binary cross-entropy loss function.Keras uses Stochastic Gradient Descent when running the artificial neural network. We added a variance calculation of each updated weight to determine which predictors were the most important in the model and obtained results of the most important predictors being Sex, Hos_Clin, Pneumonia, Pregnant, Lan_Indig, Diabetes, Asthma, Hypertension, Obesity, Tobacco. To evaluate the model accuracy, a confusion matrix was calculated, with the following results:

**Confusion Matrix for Artificial Neural Network**

| **Correctly Classified**   | **34306** | **65%** |
| -------------------------- | --------- | ------- |
| **Incorrectly Classified** | 18291     | 35%     |

**Artificial Neural Network Model Metric evaluators**

| Accuracy | Precision | MCC |
| -------- | --------- | --- |
| 65%      | 62%       | 29% |


## Conclusion

Ultimately, by comparing all the algorithm results, we can see that random forests had the highest accuracy and precision as shown in the barplot below:

![image](https://user-images.githubusercontent.com/32992857/144297762-532eaaa1-e117-4079-ab22-7048bdea9b2a.png)

However, the feature importances of each algorithm differed. The three generalized linear models showed similar importance in predictors. But the two machine learning techniques were more variable. The table below compares the important features of each algorithm. 

![image](https://user-images.githubusercontent.com/32992857/144297895-0b625ed9-6f21-4a76-8ad0-11520dfbb91a.png)

From the table above we can see that the Features Sex, Hos_Clin, Pneumonia, Immuno, Cardiovascular, Obesity, Contact_Covid, ICU, and PM2.5 are important in each algorithm. Therefore demonstrating that particulate matter affects positive COVID-19 test results. 
