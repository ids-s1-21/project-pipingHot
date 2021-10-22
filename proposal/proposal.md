Project proposal
================
Piping Hot

``` r
library(tidyverse)
library(broom)
library(here)
```

## 1. Introduction

Do factors such as age, hypertension and BMI increase the risk of a
stroke?

We got our dataset from the Kaggle website. The data was collected
confidentially because it concerns health so the details about its
collection have not been published. Each case is a different individual.
The 12 variables refer to the attributes of the individuals.

## 2. Data

``` r
stroke_risk <- read.csv(here::here("data/healthcare-dataset-stroke-data.csv"))
```

## 3. Data analysis plan
