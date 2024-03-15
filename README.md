# Mental Health Program Awareness

## Background 
Mental Health Illness of the employee’s data is 2014 survey data conducted by Open Sourcing Mental Illness (https://osmihelp.org/research/) organization across the countries, targeting the Tech companies.

<b>Regression Models: </b> Logit Regression Model is used to predict the probabilities.  
The dataset linked to the variables in the problem statement attributes are Timestamp – 27Aug 2014 to 30 Nov 2015, Country- United States, States- All states in USA and Tech companies.

## Problem 1
### Problem Statement
1. What is the impact on work interference due to the mental health condition of the employees working in the US technology companies?
2. Below are the few survey questions from the dataset to determine the problem statement: 
    - <b>Family History (FH):</b> Do you have a family history of mental illness?
    - <b>Treatment(T):</b> Have you sought treatment for a mental health condition?
    - <b>Work Interference (WI):</b> If you have a mental health condition, do you feel that it interferes with your work? This is dependent variable.
    - <b>Age:</b> Respondent age. 
    - <b>Male/Female:</b> Respondent gender.

### Results and Interpretation
Using General Linear Model and specifying the link function logit in R program to perform regression analysis.

<img src="https://your-image-url.type](https://github.com/NishaPardeshi/Regression_MentalHealthIllness/blob/master/Logistic_Regression/prob1call.png)" width="900" height="400">

Apart from the above variables more independent variables are considered and below are the results:

![image](https://github.com/NishaPardeshi/Regression_MentalHealthIllness/assets/34423049/189c9d85-d5d8-4e6f-977b-ca0b01efd507)

Based on the above regression analysis, Age and gender doesn’t have any significant effect on Work Interference (dependent variable).





