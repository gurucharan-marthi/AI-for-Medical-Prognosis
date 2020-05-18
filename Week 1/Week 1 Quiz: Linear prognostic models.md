# **Week 1 Quiz: Linear prognostic models**

### **Notice that I only list correct options.**

1. Which of the following is not an example of a clinical application of a prognostic model?
- **Detecting atrial fibrillation automatically using a EKG**

Correct!
Correct answer. Prognosis involves predicting the risk of future events. Detecting atrial fibrillation involves determining something that has already happened, so it is NOT an example applying prognosis.

2. Recall the MELD score from the lesson. What is the output for a person with
Creatinine = 0.8 mg/dL, Bilirubin total = 1.5 mg/dL, INR = 1.3
Remember that the final score is multiplied by 10. Please use natural logarithm instead of base 10 log. You can also watch the video "Liver Disease Mortality" to review the calculation of the MELD score.
Variable	Coefficient
Ln Creatinine (mg/dL)	0.957
Ln Bilirubin total (mg/dL)	0.378
Ln INR	1.120
Intercept	0.643
- **8.76**

Correct! Evaluating the formula, we get ln(0.8)* 0.957 + ln(1.5)* 0.378 + ln(1.3)* 1.12 + 0.643 = 0.876. Multiplying this by 10 we get 8.76.

3. You’ve fit a linear model with no interaction terms, and which include Age (in years) as an input feature of the model. Also, you don't multiply the sum product by any scaling number (unlike the MELD score, for instance).
The risk score for a patient measured today is 0.56. The model's coefficient for age is 0.24.
What will this patient's risk score be one year later, if all other features remain the same?
