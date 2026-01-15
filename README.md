# Mental Health Program Awareness

<img width="1536" height="1024" alt="mental-health-program" src="https://github.com/user-attachments/assets/8c6399e2-07ea-4ebb-9783-a68138d5b3f4" />

This project analyzes employee mental health survey data from U.S. technology companies to understand work interference, employer awareness, and wellness program effectiveness using logistic regression models. <br>

## Problem Statement
- How does mental health affect employee work performance in U.S. tech companies?
- Do employers recognize mental health as seriously as physical health?
- Are workplace wellness programs effective in supporting employees?

## Dataset
- Source: Open Sourcing Mental Illness (OSMI)
- Year: 2014–2015
- Population: Employees in U.S. technology companies
- Key Variables:
  - Family History
  - Treatment
  - Work Interference
  - Employer Support Indicators
  - Model evaluation using ROC-AUC and confusion matrices
 
## Methodology
- Applied Generalized Linear Models with logit link function
- Built three logistic regression models for:
  1. Work Interference
  2. Employer Mental Health Awareness
  3. Wellness Program Effectiveness

## Key Results
- ROC-AUC of 0.89 for work interference model
- 71 percentage-point increase in work interference among employees seeking treatment
- 21 percentage-point higher interference for employees with family history
- Strong association between employer awareness and ease of taking mental health leave

## Impact
- Provided data-driven insights for improving workplace mental health policies
- Demonstrated strong model performance in identifying work interference
- Highlighted key factors influencing employee well-being in tech organizations

## Tools & Technologies
- R Programming
- Logistic Regression (GLM)
- ROC Curve & AUC
- Confusion Matrix
- Statistical Data Analysis

## How to Run
1. Clone the repository
2. Load the dataset in R
3. Run the regression scripts
4. Evaluate results using ROC and confusion matrix

## Limitations
- Treatment duration and severity were not available
- Self-reported survey data may introduce bias

## Future Improvements
- Incorporate longitudinal mental health data
- Extend analysis using machine learning models
- Compare trends across countries and industries
 
# Detailed Overview & Insights:
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

<img src="https://github.com/NishaPardeshi/Regression_MentalHealthIllness/blob/master/Logistic_Regression/prob2call.PNG">  

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

### Conclusion:  
a. <b> Managerial Implication / Recommendation </b>  

<img src="https://github.com/NishaPardeshi/Regression_MentalHealthIllness/blob/master/Logistic_Regression/prob2concl1.PNG" >  

## Problem 3  
### Problem Statement
1.To analyze the effectiveness of the health program for the employees working in USA and determine the employer offers privileges to their employees to tackle mental health issues?  
2. Below are the few survey questions from the dataset to determine the problem statement:  
    - <b>Benefits(B):</b> Does your employer provide mental health benefits?  
    - <b>Care options(CO):</b> Do you know the options for mental health care your employer provides?  
    - <b>Wellness Program (WP):</b>Has your employer ever discussed mental health as part of an employee program ?  
    - <b>Seek help(SH):</b> Does your employer provide resources to learn more about mental health issues and how to seek help?  

### Results and Interpretation
Using General Linear Model and specifying the link function logit in R program to perform regression analysis.

<img src="https://github.com/NishaPardeshi/Regression_MentalHealthIllness/blob/master/Logistic_Regression/prob3call.PNG">

<b>Probabilities:</b> Finding the impact probability of independent variables on dependent variable.   
1. <b> Wellness program = -3.5248+(2.4588*SH)+(1.7236*B)  </b>  
   <b> Considering Benefits constant and the interpretation of SH.  </b>   
    For SH = 0 : ln(p/1-p) = -3.5248  
        SH = 1 : ln(p/1-p) = -3.5248+2.4588 = -1.066   
    b1 is change in log odds comparing having no SH   
    
    Transform odds into probability -> P = $(e^y/1+e^y)$   
    For SH =0 : Probability = $(e^{-3.5248} / 1+ e^{-3.5248})$ = 0.03  
    SH = 1 : Probability = $(e^{-1.066} / 1+ e^{-1.066})$ = 0.26  
    Difference in probability = 0.26-0.03 = 0.23   
   
    <b>Interpretation: </b> The company will have 23 percent points more Wellness Program when employee has Seek Help compare to employees with no Seek Help.  

2. <b> Wellness program = -3.5248+(2.4588*SH)+(1.7236*B) </b>   
   <b> Considering Benefits interpretation and constant for SH. </b>    
    For B =0 : ln(p/1-p) = -3.5248  
    B = 1: ln (p/1-p) = -3.5248+1.7236 = -1.8012   
    b1 is change in log odds comparing having no Benefits.    
   
    Transform odds into probability -> P = $(e^y/1+e^y)$   
    For B =0 : Probability = $(e^{-3.5248} / 1+ e^{-3.5248})$ = 0.03   
    B =1 : Probability = $(e^{-1.8012} / 1+ e^{-1.8012})$ = 0.14    
    Difference in probability = 0.14-0.03 = 0.11  
   
    <b> Interpretation: </b> The company will have 0.11 percent points more Wellness Program when employee has Benefits compare to employees with no Benefits.
   
4. <b> Wellness program = -3.5248+(2.4588*SH)+(1.7236*B) </b>   
   <b> Considering Benefits and Seek Help for the interpretation. </b>
    For SH =1 and B =1: ln (p/1-p) = 3.5248+2.4588+1.7236 = 0.6576  

    Transform odds into probability -> P = $(e^y/1+e^y)$   
    For FH and T =1 : Probability = $(e^{-0.6576} / 1+ e^{-0.6576})$ = 0.66  
   
    <b> Interpretation: </b> The company will have 66 percent points more Wellness Program when employee is aware of Benefits and seeks help.  

Using R "predict" function, the prediction results are predicted for all the observations of the variables.  
Syntax: - predlogit <- predict(logit, data, type= 'response').  
It is necessary to compute the error percent and measure of fitness to understand the improvement.  
Therefore, from the prediction results confusion matrix is constructed to measure the error percentage.  

<img src="https://github.com/NishaPardeshi/Regression_MentalHealthIllness/blob/master/Logistic_Regression/cfprob3.PNG" >  

### Strengths:  
ROC(Receiver Operating Characteristics) curve: This curve determine the performance of the logit regression model.  
The area under the curve tending to 1 will determine the performance of the logit model. The more near to 1 is best considered as good performance and below 0.5 means we should reconsider our model. 
In this case, 0.8632 area under curve value represents best performance by logit model.  

<img src="https://github.com/NishaPardeshi/Regression_MentalHealthIllness/blob/master/Logistic_Regression/prob3roc.PNG" >  

### Conclusion:  
a. <b> Managerial Implication / Recommendation </b>  

<img src="https://github.com/NishaPardeshi/Regression_MentalHealthIllness/blob/master/Logistic_Regression/prob3concl1.PNG" >  

### Limitations:  
i. From the dataset, we might require more information about Treatment period, which is a limitation to analyze the effectiveness of the treatment taken by the employees.  





   





