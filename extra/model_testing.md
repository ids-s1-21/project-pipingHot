Project tests
================
Piping Hot

``` r
library(tidyverse)
library(broom)
library(janitor)
```

``` r
stroke_risk <- read.csv(here::here("data/healthcare-dataset-stroke-data.csv"))
stroke_risk_cleaned <- stroke_risk %>%
  filter(gender != "Other") %>%
  mutate(
    #hypertension = if_else(hypertension == 1, TRUE, FALSE),
    #heart_disease = if_else(heart_disease == 1, TRUE, FALSE),
    #stroke = if_else(stroke == 1, TRUE, FALSE),
    bmi = if_else(bmi == "N/A", NA_real_, as.numeric(bmi))
  )
```

    ## Warning in replace_with(out, !condition, false, fmt_args(~false), glue("length
    ## of {fmt_args(~condition)}")): NAs introduced by coercion

``` r
stroke_ds <- stroke_risk_cleaned %>%
  select(-c(id, ever_married, work_type, Residence_type))

logit2prob <- function(logit){
  odds <- exp(logit)
  prob <- (odds / (1 + odds)) * 100
  return(prob)
}


set.seed(16)

 # stroke_split <- initial_split(stroke_risk, prop = 0.7) #Splitting 70% for training and 30% testing 

#stroke_fit <- logistic_reg() %>%
#  set_engine("glm") %>%
#  fit(factor(stroke) ~ ., data = stroke_ds, family = "binomial") 
  
  
# tidy(stroke_fit)
```
