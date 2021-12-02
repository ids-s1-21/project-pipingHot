Stroke Risk 
================
by pipingHot🔥

## Summary

## **DISCLAIMER: WE ARE NOT MEDICAL PROFESSIONALS!!!**

Do factors such as age, blood glucose levels, gender, hypertension, BMI and heart disease increase the risk of a stroke? We aim to see if these factors have any effect on stroke risk. 
We got the dataset from the Kaggle website. The data was collected confidentially because it concerns health of real people so the details about its collection have not been published. Each case is a different individual. There are 12 variables ([See data dictionary](https://github.com/ids-s1-21/project-pipingHot/tree/main/data)). 

## WHAT IS A STROKE?

A stroke is a potentially deadly condition where the blood supply is cut off from the brain. This can be caused by something blocking a blood vessel (ischemic stroke) or it can be caused by a burst blood vessel (hemorrhagic stroke). What makes strokes so dangerous is that the longer the blood supply is cut of from the brain the more brain cells die[^1]. 

[^1]: CDC, 2021 

## HYPOTHISIS

We expect to see a link between old age and stroke risk as it is an established factor in stroke risk[^2] Stroke Association, 2021. Also, a possible link should exist between blood glucose and stroke risk - as high blood glucose can cause other health issues known to lead to strokes[^3]. We expect the factors of BMI and hypertension to increase stroke risk the most. 

[^2]: Stroke Association 
[^3]: Diabetes UK

## METHOD

We decided to remove all individuals from age 15 and below as we want to learn and investigate stoke risk in adults and the data about children will negatively affect the reliability of our findings. We made a simple density graph to see at what value of blood glucose does the number of stokes increase as well as some simple statistics to find the average age at which people have a stroke in our data set. We made a logistic regression model using the variables; age, heart disease, hypertension, average blood glucose level, gender and BMI. 

## FINDINGS 

**“Average glucose level compared to stroke risk”**

On this density graph the two ridges peak into different places. Firstly, they peak at an average glucose level of 80mg/dl, those who did not have a stroke peaked much higher than those who did have a stroke. The second peak peaked at an average glucose level of 210 mg/dl, those who did not have a stroke was a relatively low peak but those who did have a stroke leaked significantly higher than those who didn’t. This shows a possible link between high blood glucose levels (anything about 180 mg/dl is considered high) and an increased stroke risk[^4].

[^4]: Diabetes.co.uk, 2019 
	
**“The Average Age of Patients who have had a Stroke”**

The average age of the individuals who had a stroke is 71 years old but the average age of those who did not have a stroke id 22 years younger than those who did at 49 years old. This finding is consistent with the known and proven link between increased age and a higher stroke risk. 

## THE MODEL 

We expected a high BMI and having hypertension to increase stroke risk the most. As our model is logistic, we can’t give exact figures, but we found that age and hypertension increase stroke risk the most. 

The base model uses the variables: age, hypertension, heart disease, gender, BMI and average glucose level. AIC (Akaike Information Criterion) helps decide the least amount of variables needed to explain the greatest amount of variation - the lower AIC value the more preferable the model. Since the AIC penalises the model with more variables but explains the same amount of variation. 

|        Model          |  AIC |
|-----------------------|------|
| Base                  | 1108 |
| Base & Work type      | 1110 |
| Base & Residence Type | 1109 |
| Base & Smoking Status | 1110 |
| Base & Ever Married   | 1110 |
| Base without Gender   | 1106 |

We did not remove gender despite the AIC being preferable because by removing gender the sensitivity of our model fell by 32.5%, which led to the increase in the false negative rate by the same amount.  

|                               | Did have a stroke | Did not have a stroke |
|-------------------------------|-------------------|-----------------------|
|Predicted to have a stroke     |        25         |          128          |
|Predicted to not have a stroke |        15         |          669          |

This gives us the sensitivity of the model as 62.5% and a specificity of 83.9%.[^5]  

The accuracy of the model is 82.9% - which basically measures how well our model identified people who had a stroke and who did not.[^6] The AUC is 81.6% which is good because the model is better at distinguishing between people who have had a stroke and those who have not. We also did a 10 fold cross validation to avoid over fitting, from which we got the average accuracy of our model as 95% and average AUC as 82.6%.


[^5]: All figures given to 1 decimal place
[^6]: Accuracy is measured on the data set aside for testing and is dependent on the cut-off probability which decides how the model distinguishes between people who had a stroke and those who did not. For this reason, the AUC is a better form of measuring the performance of the model since it does not depend on any cut-off value.


## EVALUATION 

Limitations on the Dataset: 
  + Don’t know medication, (anticoagulants, aspirin, blood thinning drugs, combined contraceptive pill, etc). Blood thinning drugs can reduce risk of colts forming, this reduces stroke risk[^9]. The Combined Pill can cause high blood presser and increase risk of blood clots[^10]. 
  + BMI is not an accurate reflection of a person’s health, especially **cholesterol levels** (high cholesterol is proven to increase risk of a stroke[^11]). 
  + We don’t know other health conditions that can increase risk e.g. sickle cell disease[^12].
  + We don’t have data about physical activity. Regular exercise can reduce cholesterol levels and keep blood pressure at a normal level[^13].  
  + Alcohol consumption. Excessive alcohol consumption can increase blood pressure[^14].
  + Ethnicity. some ethnicities are at a higher risk of having a stroke partly due to having a higher risk of diabetes. Also Sickle cell disease (a disease which effects the red blood cells and increases risk of stroke) mostly effects people of African, Asian, Caribbean and Mediterranean origin[^15]. 
  + Family history. it is common to see higher risk of stroke in people who have has a family member who also had a stroke.
  + Second-hand smoking. Even if you do not smoke and you are around people who smoke, you are still inhaling the smoke and so getting similar long term effects as a smoker. Stroke risk is increased by second hand smoking by 20-30%[^16].  

[^9]: Stroke Assosiation
[^10]: NHS
[^11]: CDC, 2020 
[^12]: CDC, 2020
[^13]: NHS, 2021
[^14]: NHS, 2021 
[^15]: Stroke Assosiation
[^16]: NHS Inform, 2020

We were able to confirm our hypothesis about a link between age and stroke risk. This is explained by the fact that as age increases, people’s arteries become narrower and the walls become harder which increases the risk of them becoming blocked and this causes strokes[^7]. Therefore, we can confirm that age is a factor in stroke risk. 
Since we see a slight link found in our data set between high blood glucose and stroke risk which also confirms our hypothesis and is accurate to what is known outside our dataset.  High blood glucose levels often cause diabetes which increases risk of cardiovascular disease which significantly increases risk of strokes[^8].

[^7]: Stroke Assosiation
[^8]: Diabetes UK


With our model we were able to confirm that hypertension did increase risk, but we were wrong on BMI increasing risk the most, age is a bigger factor. The model is not good at predicting if people will have a stroke because the sample size is far too small to make accurate predictions. We think it’s better if our model has a higher sensitivity which reduced the number of false negatives (people being told that they won’t have a stroke when they will) instead of focusing on specificity that reduced false positives (those who are predicted to have a stroke but will not have one) because in a real-world application, false positives would at best cause panic whereas false negatives will cause people to be less aware of the risks. We are aware that having false positives is not ideal because we don’t want to cause people panic but our data on those who had a stroke is too small, so we had to decide on what we prioritize.  We are also aware that by doing this, it will decrease the accuracy, but the results align with our goal of detecting strokes.  




## Presentation

Our presentation can be found [here](presentation/presentation.html).

## Data

fedesoriano, Janurary 2021, *Stroke Prediction Data set 11 clinical
features for predicting stroke events*, Electronic data set, Kaggle,
Viewed 14th October 2021,
<https://www.kaggle.com/fedesoriano/stroke-prediction-dataset>

## References

National Health Service 2021, *Stroke*, viewed on 17th November
2021, <https://www.nhs.uk/conditions/stroke/>

Centers for disease control and prevention 2021, *About Stroke*,
viewed on the 17th November 2021, <https://www.cdc.gov/stroke/about.htm>

Centers for disease control and prevention 2020, *Conditions that
Increase the Risk for Stroke*, viewed on the 17th November 2021,
<https://www.cdc.gov/stroke/conditions.htm>

Diabeties.co.uk 2019, *Blood Sugar Level Ranges*, viewed on the 24th November 2021, <https://www.diabetes.co.uk/diabetes_care/blood-sugar-level-ranges.html>

Diabeties uk, *Diabetes and stroke*, viewed on the 24th November 2021, <https://www.diabetes.org.uk/guide-to-diabetes/complications/stroke>

National Health Service 2020, *Combined Pill*, viewed on 2nd December 2021, <https://www.nhs.uk/conditions/contraception/combined-contraceptive-pill/>

Stroke Assosiation, *Blood-thining Medication and Stroke*, viewd on 2nd of December 2021, <https://www.stroke.org.uk/what-is-stroke/blood-thinning-medication-and-stroke>

Stroke Assosiation, *Stroke Risk Factors*, viewed on the 24th November 2021, <https://www.stroke.org.uk/what-is-stroke/are-you-at-risk-of-stroke> 

NHS Inform 2020, *Second-Hand Smoke*, viewed on the 2nd of December 2021, <https://www.nhsinform.scot/healthy-living/stopping-smoking/reasons-to-stop/second-hand-smoke#:~:text=%20Some%20short-term%20effects%20from%20exposure%20to%20second-hand,and%20nasal%20irritation%204%20sore%20throat%20More%20>


