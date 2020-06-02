# **Week 4 Quiz: Survival and hazard functions**

### Notice that I only list correct options.

1. Person 1 has hazard h_1(t) = 1 and Person 2 has hazard h_2(t) = 2. What is the probability of dying within the first year for each patient?
Hint:
The survival function S(t)S(t) in terms of the hazard function is:
S(t) = e^{-\int_{0}^{t} h(s)ds}
- **0.63,0.86**

Correct!
Note that since the hazards are constant,
S_1(1) = e^{(-h_1(0))} = e^{(-1)}
S_2(1) = e^{(-h_2(0))} = e^{(-2)}
Since we want the probability of death, we take 1-S(t)1−S(t).
This gives us for person 1: 1-e^{(-1)} = 0.631−e 
(−1)
 =0.63.
For person 2, 1 - e^{(-2)} = 0.861−e 
(−2)
 =0.86.
 
 2. Let T > 0T>0.
For patient 1, let the survival function be S_1(t) and the hazard function be h_1(t)
For patient 2, let the survival function be S_2(t) and the hazard function be h_2(t)
You see that S_1(T) > S_2(T). The survival probability of patient 1 at time T is higher than the survival probability of patient 2 at time T.
Which of the following is true about the hazard of patient 1 and 2 at time T?
Hint: S(t) = e^{-\int_{0}^{t} h(s)ds}
- **None of the above**

Correct!
The answer is none of the above.
Recall that S(t)S(t) decays exponentially in the integral of the hazard (it's e raised to the power of negative 1 times the integral of the hazard).
So just because you know S(T)S(T) at one point does not say anything about h(T)h(T) at that point, since S(T)S(T) also depends on what happened from time t=0t=0 up to time t=Tt=T.

3. Now assume that the hazards for patient 1, h_1 and for patient 2, h_2 are proportional to each other. Also assume that S_1(T) > S_2(T) for some T > 0.
Then which of the following is true about the hazards?
- **h_1(T) < h_2(T)**

Correct!
Since the hazards are proportional, we know that they cannot cross each other when we vary the time T.
Therefore if the survival function of Person 1 is above the survival function of Person 2 at any point, it must be above the person 2 survival function everywhere.
Since the survival function decays exponentially with the hazards (it is e raised to the power of negative 1 times the integral of the hazard) it means that the hazard of Person 1 is LESS than the hazard of Person 2.
Since the hazards are proportional, this must be true for any time T.
In particular h_1(T) < h_2(T)

4. You’ve fit a Cox model on 2 features: age and smoking status.
The coefficients of these features are:
beta_{age} = 0.9 and beta_{smoker} = 10.0 What is the hazard ratio between Person 1, a 40 year old non-smoker, and Person 2, a 30 year old smoker?
Recall that Cox Proportional Hazards assumes a model of the form:
h(t) = \lambda_{0}(t) e^{(\beta_{age} \times Age + \beta_{smoker} \times Smoker)}
We're asking you to find the ratio:
frac{h_1(t)}{h_2(t)} 
- **0.36**

Correct!
frac{h_1(t)}{h_1(t)} = frac{\lambda_{0}(t) e^{(\beta_{age} \times Age_{1} + \beta_{smoker} \times Smoker_{1})}}{\lambda_{0}(t) e^{(\beta_{age} \times Age_{1} + \beta_{smoker} \times Smoker_{2})}} 
When we take the ratio, the lambda_{0} will drop out.
So we just compute:
frac{h_1(t)}{h_2(t)} = frac{e^{(0.9 \times 40 + 10 \times 0)}}{e^{(0.9 \times 30 + 10 \times 1)}} = e^{(36 - (27 + 10))}
frac{h_1(t)}{h_2(t)} = e^{(-1)} = 0.36 

5. You’ve fit a cox model and have the following coefficients:
beta_{female} = -1.0β 
beta_{age} = 1.0β 
beta_{BP} = 0.6β 
h(t)=λ0(t)e^^((β female×female)+(β age×Age)+(β BP×BP))
Which of the following interpretations is most correct?
- **All other things held equal, being a female decreases your risk**

Correct!
Note that the effect of increasing a feature x by 1 unit will be to multiply the hazard by e^{(\beta_{x})}
Since e^{(0)} = 1, a coefficient less than 0 (a negative coefficient) reduces the hazard. A coefficient greater than 0 (positive) increases the hazard.
Therefore the only correct interpretation is that being a female decreases the hazard, since beta_{female} < 0

6. Assume h_1(t) = t, and h_2(t) = 1.0. At which time T > 0 does S_1(T) = S_2(T)?
- **2**

Correct!
Remember that the Cumulative hazard is the integral from 0 to t of the hazard function. Using calculus, one can see that the cumulative hazard for Person 1 is 0.5t^2 and for person 2, the cumulative hazard is t.
Since S(t) = exp(-H(t)), the survival functions are equal if and only if the cumulative hazard is equal.
Setting these equal to each other, we get t = 2. A common mistake is just to set the hazards equal, which would give you t = 1.

7. Using the Nelson-Aalen estimator estimate H(7), the value of the cumulative hazard at t=7 for this dataset.
ID	Outcome
1	3
2	4
3	8
4	6+
The Nelson-Aalen estimator is: H(t) = sum_{i=0}^t frac{d_i}{n_i}H(t)
- **7/12**

Correct!
Evaluating this for t = 7t=7, we get
frac{d_3}{n_3} + frac{d_6}{n_6} = frac{1}{4} + frac{1}{3} = frac{7}{12} 

8. Which risk assignments would make this pair concordant?
- **The pair is not permissible**

Correct!
The pair is in fact not permissible. Since Patient 2 was censored before Patient 1 had the event, we cannot say who had a worse outcome.

9. Compute the Harrell C-index for the following dataset and risk scores:
ID	Outcome	Score
1	4	1.6
2	6+	1.2
3	5	0.8
4	7	0.1
Step 1: Find all the permissible pairs
Step 2: of the permissible pairs, determine which ones are concordant.
Step 3: of the permissible pairs, determine which ones are risk ties.
Harrell's c-index = \frac{concordant + 0.5 \times riskties}{permissible} 
- **0.8**

Correct!
The permissible pairs are
(1, 2), (1, 3), (1, 4), (2, 3), (3, 4).
Of these, the concordant ones are
(1, 2), (1, 3), (1, 4), and (3, 4).
Since there are no ties, the harrell’s c-index is the number of concordant pairs over the number of permissible pairs, which is \frac{4}{5} = 0.8 
