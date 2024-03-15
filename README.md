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

<img src="https://github.com/NishaPardeshi/Regression_MentalHealthIllness/blob/master/Logistic_Regression/prob1call.png" width="900" height="500">

Apart from the above variables more independent variables are considered and below are the results:

<img src="https://github.com/NishaPardeshi/Regression_MentalHealthIllness/blob/master/Logistic_Regression/prob1coef.png" >

Based on the above regression analysis, Age and gender doesn’t have any significant effect on Work Interference (dependent variable). 

<b>Probabilities:</b> Finding the impact probability of independent variables on dependent variable.   
1. <b> Work_Interference = -1.2456+(0.9987*FH)+(3.9010*T)  </b>  
   <b> Considering Treatment constant and the interpretation of FH.  </b>   
    For  FH =0 : ln(p/1-p) = -1.234  
         FH = 1: ln (p/1-p) = -1.234+0.9887 = -0.246  
    b1 is change in log odds comparing having no FH and FH.  
    
    Transform odds into probability -> P = $(e^y/1+e^y)$   
    For FH =0 : Probability = $(e^{-1.234} / 1+ e^{-1.234})$ = 0.23
    FH = 1 : Probability = $(e^{-0.246} / 1+ e^{-0.246})$ = 0.44  
    Difference in probability = 0.44-0.23 = 0.21 
   
    <b>Interpretation: </b> The company will have 21 percent points more Work Interference when employee has Family History compare to employees with no Family history.

2. <b> Work_Interference = -1.2456+(0.9987*FH)+(3.9010*T)  </b>   
   <b> Considering Family History constant and the interpretation of Treatment. </b>    
    For T =0 : ln(p/1-p) = -1.234  
    T = 1: ln (p/1-p) = -1.234+3.89 = 2.656   
    b2 is change in log odds comparing having no T and T.  
   
    Transform odds into probability -> P = $(e^y/1+e^y)$   
    For T =0 :- Probability = $(e^{-1.234} / 1+ e^{-1.234})$ = 0.23  
    T =1 :- Probability = $(e^{2.656} / 1+ e^{2.656})$ = 0.93  
    Difference in probability = 0.93-0.23 = 0.71
   
    <b> Interpretation: </b> The company will have 71 percent points more Work Interference when employee has taken Treatment compare to employees with no Treatment. 

3. <b> Work_Interference = -1.2456+(0.9987*FH)+(3.9010*T)  </b>   
   <b> Considering both Family History constant and the interpretation of Treatment. </b>  
    For FH and T = 1: ln (p/1-p) = -1.234+0.9887+3.89 = 3.644  

    Transform odds into probability -> P = $(e^y/1+e^y)$   
    For FH and T =1 : Probability = $(e^{3.644} / 1+ e^{3.644})$ = 0.975  
   
    <b> Interpretation: </b> The company will have 97.5 percent points more Work Interference when employee has Family History and undergone Treatment.


   





