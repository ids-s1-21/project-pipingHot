Project title
================
by Team name

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


Write-up of your project and findings go here. Think of this as the text
of your presentation. The length should be roughly 5 minutes when read
out loud. Although pacing varies, a 5-minute speech is roughly 750
words. To use the word count addin, select the text you want to count
the words of (probably this is the Summary section of this document, go
to Addins, and select the `Word count` addin). This addin counts words
using two different algorithms, but the results should be similar and as
long as you’re in the ballpark of 750 words, you’re good! The addin will
ignore code chunks and only count the words in prose.

You can also load your data here and present any analysis results /
plots, but I strongly urge you to keep that to a minimum (maybe only the
most important graphic, if you have one you can choose). And make sure
to hide your code with `echo = FALSE` unless the point you are trying to
make is about the code itself. Your results with proper output and
graphics go in your presentation, this space is for a brief summary of
your project.

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

