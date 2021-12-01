# COVID-19TEST
Epidemiology is the scientific discipline that studies the determinants of health-related states or events in specified populations. Classical methods of Epidemiology such as modeling assumptions become difficult to achieve with large scale-datasets, however, machine learning has the potential to answer these questions. In this thesis, we illustrate the effectiveness of machine learning to forecast and classify in the fields of Environmental Epidemiology and Health Epidemiology. The same pre-existing conditions that increase mortality rates of COVID-19 are the same diseases that are also affected by long-term exposure to air pollution. Low-income populations suffer the most from air pollution disparity and are often burdened with long-term health effects. It is with the utmost importance that we continue investigating the relationship between air pollution and health to enforce existing air pollution regulations and ensure the protection of human health both during and after the COVID-19 pandemic. To study the relation of COVID-19 and air pollution we propose a refined data collection that uses Particulate Matter data and Mexico’s COVID-19 cases public dataset. We approach the classification of COVID-19 diagnosis by using three traditional generalized linear regression models (logistic, probit, and complementary log-log) and two machine learning techniques (random forest classifier and artificial neural network). We use Python to produce the COVID-19 diagnoses classifiers.
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

## Artificial Neural Network
