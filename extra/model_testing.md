Project tests
================
Piping Hot

``` r
library(tidyverse)
library(broom)
library(rsample)
library(knitr)
library(tidymodels)
library(janitor)
```

``` r
stroke_risk <- read.csv(here::here("data/healthcare-dataset-stroke-data.csv"))

stroke_risk <- stroke_risk %>%                          #Cleanup by Alex
  filter(age >= 16, gender != "Other") %>%
  mutate(
    bmi = if_else(bmi == "N/A", 
                  NA_real_, as.numeric(bmi)),
    work_type = if_else(age == 16 & work_type == "children", 
                        "Never_worked", 
                        work_type)
  ) %>%
clean_names()
```

    ## Warning in replace_with(out, !condition, false, fmt_args(~false), glue("length
    ## of {fmt_args(~condition)}")): NAs introduced by coercion

``` r
stroke_risk <- stroke_risk %>%                         #Cleanup by Ishan
    filter(!(is.na(bmi))) %>%
    mutate(stroke  = as.factor(stroke)) 

logit2prob <- function(logit){                         #Function to get probability for a logsitic reg
  odds <- exp(logit)
  prob <- (odds / (1 + odds)) * 100
  return(prob)
}


set.seed(16)

stroke_split <- initial_split(stroke_risk, prop = 0.8) #Splitting 80% for training and 20% testing 

train_data <- training(stroke_split)
test_data  <- testing(stroke_split)

stroke_rec <- recipe(stroke  ~ ., data = train_data) %>%    
  step_rm(id, work_type, residence_type, smoking_status, ever_married) %>%
  step_dummy(all_nominal(), -all_outcomes()) %>%
  step_zv(all_predictors())

stroke_fit_base <- logistic_reg() %>%
  set_engine("glm")

stroke_wflow <- workflow() %>%
  add_model(stroke_fit_base) %>%
  add_recipe(stroke_rec)

stroke_fit <- stroke_wflow %>%
  fit(data = train_data)

stroke_pred <- predict(stroke_fit, test_data, type = "prob") %>% 
  bind_cols(test_data %>% select(stroke))


cutoff_prob <- 0.1                       # low cut-off probability in order to reduce the false negative rate (i.e having strokes go undetected)

stroke_pred_accuracy <- stroke_pred %>%  # for accuracy 
  mutate(
    stroke_pred = if_else(.pred_1 > cutoff_prob, 1, 0)
    )

stroke_pred %>%                          # gets a value for the area under the ROC curve 
  roc_auc(
    truth = stroke,
    .pred_1,
    event_level = "second"
  ) 
```

    ## # A tibble: 1 × 3
    ##   .metric .estimator .estimate
    ##   <chr>   <chr>          <dbl>
    ## 1 roc_auc binary         0.816

``` r
stroke_pred %>%                         # plots the ROC curve  
  roc_curve(
    truth = stroke,
    .pred_1,
    event_level = "second"
  ) %>%
  autoplot()
```

![](model_testing_files/figure-gfm/model%20testing-1.png)<!-- -->

``` r
stroke_pred %>%                                  # prediction model 
  mutate(
    stroke      = if_else(stroke == 1, 
                          "Person has had a stroke", 
                          "Person has not had a stroke"),
    stroke_pred = if_else(.pred_1 > cutoff_prob, 
                          "It is predicted that the person has had a stroke ", 
                          "It is predicted that the person has not had a stroke")
    ) %>%
  count(stroke_pred, stroke) %>%
  pivot_wider(names_from = stroke, values_from = n) %>%
  kable(col.names = c("", "Person has had a stroke", "Person has not had a stroke"))
```

|                                                      | Person has had a stroke | Person has not had a stroke |
|:-----------------------------------------------------|------------------------:|----------------------------:|
| It is predicted that the person has had a stroke     |                      25 |                         128 |
| It is predicted that the person has not had a stroke |                      15 |                         669 |

``` r
#62.5% sensitivity, 83.9% for specificity (to one d.p)


stroke_pred_accuracy %>%                
  accuracy(truth = stroke, factor(stroke_pred))
```

    ## # A tibble: 1 × 3
    ##   .metric  .estimator .estimate
    ##   <chr>    <chr>          <dbl>
    ## 1 accuracy binary         0.829

``` r
#82.9% accuracy 


folds <- vfold_cv(train_data, v = 10)   # for cross-validation

stroke_fit_rs <- stroke_wflow %>%       # use collect_metrics(stroke_fit_rs) to see average accuracy/AUC
  fit_resamples(folds)


# Use the code below to get AIC values for various models 

# AIC_determiner <- function(x) 
# {
#   glance(x)$AIC 
# }
# AIC_determiner(stroke_fit_base)
# map(models,AIC_determiner)
```
