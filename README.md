Stroke Risk (working)
================
by pipingHot

## Summary

DISCLAIMER: WE ARE NOT MEDICAL PROFESIONALS!!!

Do factors such as age, blood glucose levels, hypertension, BMI and heart disease increase the risk of a stroke? We aim to see if these factors have any effect on stroke risk. 
We got the dataset from the Kaggle website. The data was collected confidentially because it concerns health of real people so the details about its collection have not been published. Each case is a different individual. There are 12 variables (See data dictionary). 

WHAT IS A STROKE?

A stroke is a potentially deadly condition where the blood supply is cut off from the brain. This can be caused by something blocking a blood vessel (ischemic stroke) or it can be caused by a burst blood vessel (hemorrhagic stroke). What makes strokes so dangerous is that the longer the blood supply is cut of from the brain the more brain cells die. (CDC, 2021) 

HYPOTHISIS

We expect to see a link between old age and stroke risk as it an established factor in stroke risk (Stroke Association, 2021). Also, a possible link between blood glucose and stroke risk as high blood glucose can cause other health issues known to lead to strokes. We expect the factors of BMI and Hypertension to increase stroke risk the most (Diabetes UK). 

METHOD

We decided to remove all individuals form age 15 and below as we want to learn and investigate adult risk and the data about children will affect the findings. we also removed the work type variable as it there are too may external factors effecting what type of job someone has are not relevant to our investigation. We made a simple density graph to see at what value of blood glucose number of stokes increase as well as some simple stats to find the average age of stroke in our data set. We made a logistic regression model using the variables; age, heart disease, hypertension, average blood glucose level, gender and BMI. 

FINDINGS 

“Average glucose level compared to stroke risk”

On this density graph the two ridges peak into different places. Firstly, they peak at an average glucose level of 80mg/dl, those who did not have a stroke peaked much higher than those who did have a stroke. The second peak peaked at an average glucose level of 210 mg/dl, those who did not have a stroke was a relatively low peak but those who did have a stroke leaked significantly higher than those who didn’t. This shows a possible link between high blood glucose levels (anything about 180 mg/dl is considered high) and an increased stroke risk. (Diabetes.co.uk, 2019) 
	
“The Average Age of Patients who have had a Stroke”

The average age of the individuals who had a stroke is 71 years old but the average age of those who did not have a stroke id 22 years younger than those who did at 49 years old. This finding is consistent with the known and proven link between increased age and a higher stroke risk. 

"The Model"

We expected a high BMI and if they had Hypertantion to increase stroke risk and we found that. As our model is logistic, we can’t give exact figures, but we can say that increased age increases risk the most and having hypertension increases risk. 

EVALUATION 

Limitations on the Dataset: 
  --Don’t know medication, (anticoagulants, aspirin blood thinning drugs, combined contraceptive pill). 
  --BMI is not an accurate reflection of a person’s health, especially cholesterol levels (high cholesterol is proven to increase risk of a stroke). 
  --We don’t know other health conditions that can increase risk e.g. sickle cell disease.
  --We don’t have data about physical activity. 
  --Alcohol consumption.
  --Ethnicity.
  --Family history.
  --Second-hand smoking. 

We were able to confirm our hypothesis about a link between age and stroke risk. This is explained by the fact that as age increases, people’s arteries become narrower and the walls become harder which increases the risk of them becoming blocked and this causes strokes. Therefore, we can confirm that age is a factor in stroke risk. 
Since we see a slight link found in our data set between high blood glucose and stroke risk which also confirms our hypothesis and is accurate to what is known outside our dataset.  High blood glucose levels often cause Diabetes which increases risk of cardiovascular disease which significantly increases risk of strokes (Diabetes UK).
With our model we were able to confirm that hypertension did increased risk, but we were wrong on BMI increasing risk, age is a bigger factor. The model is not good at predicting if people will have a stroke because the sample size is far too small to make accurate predictions. We think it’s better if our model has a higher sensitivity which reduced the number of false negatives (people being told that they won’t have a stroke when they will) instead of focusing on specificity that reduced false positives (those who are predicted to have a stroke but will not have one) because in a real-world application, false positives would at best cause panic whereas false negatives will cause people to be less aware of the risks. We are aware that having false positives is bad because we don’t want to cause people panic but our data on those who had a stroke is too small, so we had to decide on what we prioritize.  We are also aware that by doing this, it will decrease the accuracy but the results align with our goal of detecting strokes.  




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

Stroke Assosiation, *Stroke Risk Factors*, viewed on the 24th November 2021, <https://www.stroke.org.uk/what-is-stroke/are-you-at-risk-of-stroke> 

