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
    For T =0 : Probability = $(e^{-1.234} / 1+ e^{-1.234})$ = 0.23  
    T =1 : Probability = $(e^{2.656} / 1+ e^{2.656})$ = 0.93  
    Difference in probability = 0.93-0.23 = 0.71
   
    <b> Interpretation: </b> The company will have 71 percent points more Work Interference when employee has taken Treatment compare to employees with no Treatment. 

3. <b> Work_Interference = -1.2456+(0.9987*FH)+(3.9010*T)  </b>   
   <b> Considering both Family History constant and the interpretation of Treatment. </b>  
    For FH and T = 1: ln (p/1-p) = -1.234+0.9887+3.89 = 3.644  

    Transform odds into probability -> P = $(e^y/1+e^y)$   
    For FH and T =1 : Probability = $(e^{3.644} / 1+ e^{3.644})$ = 0.975  
   
    <b> Interpretation: </b> The company will have 97.5 percent points more Work Interference when employee has Family History and undergone Treatment.

Using R "predict" function, the prediction results are predicted for all the observations of the variables.  
Syntax: - predlogit <- predict(logit, data, type= 'response').  
It is necessary to compute the error percent and measure of fitness to understand the improvement.  
Therefore, from the prediction results confusion matrix is constructed to measure the error percentage.  

<img src="https://github.com/NishaPardeshi/Regression_MentalHealthIllness/blob/master/Logistic_Regression/cfprob1.PNG" >  

### Strengths:  
ROC(Receiver Operating Characteristics) curve: This curve determine the performance of the logit regression model.  
The area under the curve tending to 1 will determine the performance of the logit model. The more near to 1 is best considered as good performance and below 0.5 means we should reconsider our model. 
In this case, 0.895 area under curve value represents best performance by logit model.  

<img src="https://github.com/NishaPardeshi/Regression_MentalHealthIllness/blob/master/Logistic_Regression/prob1roc.PNG" >  

### Limitations:  
i. From the dataset, we might require more information about Treatment period, which is a limitation to analyze the effectiveness of the treatment taken by the employees.  

### Conclusion:  
a. <b> Managerial Implication / Recommendation </b>  

<img src="https://github.com/NishaPardeshi/Regression_MentalHealthIllness/blob/master/Logistic_Regression/prob1concl1.PNG" >  

## Problem 2
### Problem Statement
1. Whether the employers in USA are perceived to recognize the importance of mental health?
2. Below are the few survey questions from the dataset to determine the problem statement:  
    - <b>Leave(L):</b> How easy is it for you to take medical leave for a mental health condition?  
    - <b>Mental vs physical(M&P):</b> Do you feel that your employer takes mental health as seriously as physical health?  
    - <bSupervisor(S):</b> Would you be willing to discuss a mental health issue with your direct supervisor(s)?  

### Results and Interpretation
Using General Linear Model and specifying the link function logit in R program to perform regression analysis.

<img src="https://github.com/NishaPardeshi/Regression_MentalHealthIllness/blob/master/Logistic_Regression/prob2call.PNG" width="900" height="500">  

<b>Probabilities:</b> Finding the impact probability of independent variables on dependent variable.   
1. <b> Leave = -1.40 +(1.33*Mental vs physical)+(0.67*Supervisor)  </b>  
   <b> Considering Supervisor constant and the interpretation of Leave.  </b>   
    For Mental vs Physical =0 : ln(p/1-p) = -1.40    
        Mental vs Physical = 1: ln (p/1-p) = -1.40+1.33 = -0.07  
    b1 is change in log odds comparing having No Mental vs Physical and Mental vs Physical 
    
    Transform odds into probability -> P = $(e^y/1+e^y)$   
    For Mental vs Physical =0 : Probability = $(e^{-1.40} / 1+ e^{-1.40})$ = 0.20  
    For Mental vs Physical =1 : Probability = $(e^{-0.07} / 1+ e^{-0.07})$ = 0.48     
    Difference in probability = 0.48-0.20 = 0.28  
   
    <b>Interpretation: </b> The company will have 28 percent points more Leave when employee has Mental vs Physical compare to employees with no Mental vs Physical.  

2. <b> Leave = -1.40 +(1.33*Mental vs physical)+(0.67*Supervisor)  </b>   
   <b> Considering Mental vs Physical constant and the interpretation of Leave. </b>    
    For Supervisor =0 : ln(p/1-p) = -1.40  
        Supervisor =1 : ln(p/1-p) = 1.40+0.67 = -0.74   
    b1 is change in log odds comparing having No Supervisor and Supervisor.    
   
    Transform odds into probability -> P = $(e^y/1+e^y)$   
    For Supervisor =0 : Probability = $(e^{-1.40} / 1+ e^{-1.40})$ = 0.20  
        Supervisor =1 : Probability = $(e^{-0.74} / 1+ e^{-0.74})$ = 0.32  
    Difference in probability = 0.32 - 0.2 = 0.12  
   
    <b> Interpretation: </b> The company will have 12 percent points more Leave when employee has Supervisor cooperation compare to employees with no Supervisor cooperation.  

3. <b> Leave = -1.40 +(1.33*Mental vs physical)+(0.67*Supervisor)  </b>   
   <b> Considering Mental vs Physical and supervisor, the interpretation of Leave. </b>  
    For Supervisor =1, Mental vs Physical =1 : ln(p/1-p) = 0.59  

    Transform odds into probability -> P = $(e^y/1+e^y)$   
    For Supervisor =1 and Mental vs Physical =1 : Probability = $(e^{0.59} / 1+ e^{0.59})$ = 0.64  
   
    <b> Interpretation: </b> The company will have 64 percent points more Leave when employer consider mental vs physical and supervisor of employee is approachable.  

Using R "predict" function, the prediction results are predicted for all the observations of the variables.  
Syntax: - predlogit <- predict(logit, data, type= 'response').  
It is necessary to compute the error percent and measure of fitness to understand the improvement.  
Therefore, from the prediction results confusion matrix is constructed to measure the error percentage.  

<img src="https://github.com/NishaPardeshi/Regression_MentalHealthIllness/blob/master/Logistic_Regression/cfprob2.PNG" >  

### Strengths:  
ROC(Receiver Operating Characteristics) curve: This curve determine the performance of the logit regression model.  
The area under the curve tending to 1 will determine the performance of the logit model. The more near to 1 is best considered as good performance and below 0.5 means we should reconsider our model. 
In this case, 0.6952 area under curve value represents good performance by logit model.    

<img src="https://github.com/NishaPardeshi/Regression_MentalHealthIllness/blob/master/Logistic_Regression/prob2roc.PNG" >  

The above model has area under ROC curve 69.52%, which is good.  

### Limitations:  
i. From the dataset, we might require more information about Treatment period, which is a limitation to analyze the effectiveness of the treatment taken by the employees.  

### Conclusion:  
a. <b> Managerial Implication / Recommendation </b>  

<img src="https://github.com/NishaPardeshi/Regression_MentalHealthIllness/blob/master/Logistic_Regression/prob2concl1.PNG" >  






   





