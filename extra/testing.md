Project proposal
================
Piping Hot

``` r
library(tidyverse)
library(broom)
```

``` r
stroke_risk <- read.csv(here::here("data/healthcare-dataset-stroke-data.csv"))
stroke_risk <- stroke_risk %>%
  mutate(
    #hypertension = if_else(hypertension == 1, TRUE, FALSE),
    #heart_disease = if_else(heart_disease == 1, TRUE, FALSE),
    #stroke = if_else(stroke == 1, TRUE, FALSE),
    bmi = if_else(bmi == "N/A", NA_real_, as.numeric(bmi))
  )
glimpse(stroke_risk)
```

    ## Rows: 5,110
    ## Columns: 12
    ## $ id                <int> 9046, 51676, 31112, 60182, 1665, 56669, 53882, 10434…
    ## $ gender            <chr> "Male", "Female", "Male", "Female", "Female", "Male"…
    ## $ age               <dbl> 67, 61, 80, 49, 79, 81, 74, 69, 59, 78, 81, 61, 54, …
    ## $ hypertension      <int> 0, 0, 0, 0, 1, 0, 1, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 1…
    ## $ heart_disease     <int> 1, 0, 1, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 1, 1, 0, 1, 0…
    ## $ ever_married      <chr> "Yes", "Yes", "Yes", "Yes", "Yes", "Yes", "Yes", "No…
    ## $ work_type         <chr> "Private", "Self-employed", "Private", "Private", "S…
    ## $ Residence_type    <chr> "Urban", "Rural", "Rural", "Urban", "Rural", "Urban"…
    ## $ avg_glucose_level <dbl> 228.69, 202.21, 105.92, 171.23, 174.12, 186.21, 70.0…
    ## $ bmi               <dbl> 36.6, NA, 32.5, 34.4, 24.0, 29.0, 27.4, 22.8, NA, 24…
    ## $ smoking_status    <chr> "formerly smoked", "never smoked", "never smoked", "…
    ## $ stroke            <int> 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1…

``` r
stroke_risk %>%
  mutate(stroke = if_else(stroke == 1, "Yes", "No"), stroke = fct_rev(stroke)) %>%
  ggplot(aes(x = avg_glucose_level, fill = stroke)) +
  geom_density(alpha = 0.5) +
  labs(
    x = "Average Glucose Level",
    y = "Density",
    title = "Average glucose level compared to stroke risk",
    fill = "Stroke"
  ) +
  scale_fill_viridis_d() +
  theme_minimal()
```

![](testing_files/figure-gfm/makeup-artist-1.png)<!-- -->
