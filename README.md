![](https://img.shields.io/github/followers/alokthakur93?label=Follow%40alokthakur93&style=social)
![](https://img.shields.io/github/forks/alokthakur93/Stroke-risk-prediction?label=Fork&style=social)
![](https://img.shields.io/github/stars/alokthakur93/Stroke-risk-prediction?style=social)
![](https://img.shields.io/github/watchers/alokthakur93/Stroke-risk-prediction?style=social)
![](https://img.shields.io/github/issues/alokthakur93/Stroke-risk-prediction)
![](https://img.shields.io/github/repo-size/alokthakur93/Stroke-risk-prediction)
![](https://img.shields.io/github/languages/code-size/alokthakur93/Stroke-risk-prediction)

# Stroke Risk Prediction: Project Overview
* Created a simple classification Flask app which predicts the risk of stroke based on input given by a patient.
* Used different visualizations to understand the data and gain important insights.
* Handled Outliers using **IQR** and **Box plot**, Imputed missing values using mean imputation.
* Created different models to check the best suited model for this classification problem.
* Deployed a client facing Web App on **Heroku**

## Deployment Link: https://stroke-risk-prediction.herokuapp.com/

## Code and Resources Used 
**Python Version:** 3.7  
**Packages:** pandas, numpy, sklearn, matplotlib, seaborn, imblearn, flask, pickle, plotly.

**For Web Framework Requirements:**  ```pip install -r requirements.txt```  

## Business Problem / Objective:

According to the World Health Organization (WHO) stroke is the 2nd leading cause of death globally, responsible for approximately 11% of total deaths.
Use this dataset to predict whether a patient is likely to get stroke based on the input parameters like gender, age, various diseases, and smoking status. Each row in the data provides relevant information about the patient.

## Dataset details:
* The dataset was taken from Kaggle. To see the dataset visit this link: https://www.kaggle.com/fedesoriano/stroke-prediction-dataset

## Exploratory Data Analysis (EDA):
* Created different visualizations like count plot, scatter plot, Box plot to extract insights.
* Here are some visualizations:

![boxplot](https://github.com/alokthakur93/Stroke-risk-prediction/blob/main/avg_boxplot.PNG)

![heatmap](https://github.com/alokthakur93/Stroke-risk-prediction/blob/main/heatmap.PNG)

### Data Pre-processing:
* Done Label Encoding of categorical variables
* Imputed missing values in BMI variable
* Handled outliers using IQR and Box plot
* Upsampled the data using SMOTE because dataset was imbalanced
* Normalized all the values

## Model Building:

After doing pre-processing of data, I split the data into train set and test set with test size of 30%.

Tried five different models and evaluated using recall/sensitivity/True positive rate because our model must be able to identify the positive cases more correctly which necessary in Medical Domain.(Probability of correctly identifying positives)

Done Hyperparameter Tuning But this did'nt gave good result, original Xgboost model was good.

## Model Evaluation:
The XG Boost model far outperformed the other approaches on the test set

**Logistic regression:** Sensitivity - 0.78

**Decision Tree:** Sensitivity - 0.10

**Random Forest:** Sensitivity - 0.04

**Neural Network:** Sensitivity - 0.11

**XG Boost:** Sensitivity - 0.64

**_Note_**: Here sensitivity of logistic regression is high but its specificity and overall accuracy is lower than that of Xg boost model, which decreases the effectiveness of Logistic regression. Therefore, Xgboost model was chosen.

## Inferences made in EDA:
1. Individuals having high glucose levels and low BMI had stroke
2. Individuals having higher age had stroke
3. Individuals suffering from extreme obesity are also suffering from Hypoglycemia
4. Average glucose level is high in higher age group
5. 75% of data comes under average glucose level of 114 but maximum glucose level here is 271 we can clearly see that these are outliers but we can't delete these because we will lose large chunk of data, let it be there because these indicates that individuals are suffering from Hyperglycemia(>126) which is quite possible. max value = 169.5
6. Similar case is for BMI.Deleting these outliers will result in loss of heavy chunk of data. individuals having BMI more than 33 is quite possible, but individuals having BMI > 50 is a case of extreme obesity. max value = 47.5







