# COVID-19TEST
Epidemiology is the scientific discipline that studies the determinants of health-related states or events in specified populations. Classical methods of Epidemiology such as modeling assumptions become difficult to achieve with large scale-datasets, however, machine learning has the potential to answer these questions. In this thesis, we illustrate the effectiveness of machine learning to forecast and classify in the fields of Environmental Epidemiology and Health Epidemiology. The same pre-existing conditions that increase mortality rates of COVID-19 are the same diseases that are also affected by long-term exposure to air pollution. Low-income populations suffer the most from air pollution disparity and are often burdened with long-term health effects. It is with the utmost importance that we continue investigating the relationship between air pollution and health to enforce existing air pollution regulations and ensure the protection of human health both during and after the COVID-19 pandemic. To study the relation of COVID-19 and air pollution we propose a refined data collection that uses Particulate Matter data and Mexico’s COVID-19 cases public dataset. We approach the classification of COVID-19 diagnosis by using three traditional generalized linear regression models (logistic, probit, and complementary log-log) and two machine learning techniques (random forest classifier and artificial neural network). We use Python to produce the COVID-19 diagnoses classifiers.
## Binary Logistic Regression Model
Suppose the response variable Y assumes only two values which can be coded as 0 or 1. 0 is a negative COVID-19 result and 1 is a positive COVID-19 result. This type of variable is therefore termed binary. A binary logistic regression models the probability that the response, Y , is positive. 



**Confusion Matrix for Binary Probit Regression Model**

| **Correctly Classified** | **33866** | **64%** |
| --- | --- | --- |
| **Incorrectly Classified** | 18736 | 36% |

**Probit Regression Model Metric evaluators**

| Accuracy | Precision | MCC |
| --- | --- | --- |
| 64% | 36% | 25% |
## Binary Probit Regression Model
## Binary Complementary Log-log Model
## Random Forest 
## Artificial Neural Network
