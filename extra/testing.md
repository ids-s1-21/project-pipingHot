Project tests
================
Piping Hot

``` r
library(tidyverse)
library(broom)
```

``` {proposal-stuff}
stroke_risk %>%
  filter(smoking_status != "Unknown") %>%
  count(smoking_status, stroke) %>%
  ggplot(aes(x = stroke, y = n, fill = smoking_status)) +
  geom_col(position = "fill") +
  scale_fill_viridis_d() +
  labs(x = "Stroke", y = "Proportion", fill = "Smoking status") +
  theme_minimal()
```

``` {propsal-stuff2}
stroke_risk %>%
  count(gender, stroke) %>%
  filter(gender != "Other")
```

``` r
stroke_risk <- read.csv(here::here("data/healthcare-dataset-stroke-data.csv"))
```

``` r
 median_age_stroke <- stroke_risk %>%
  mutate( stroke = if_else(stroke == "1", "Yes", "No")) %>%
  group_by(stroke) %>%
  summarise(median_age = median(age))

median_age_stroke %>%
  ggplot(aes(stroke, median_age, fill = stroke)) +
  geom_col() +
  scale_fill_manual(values = c("Purple", "Orange")) +
  labs(x = "Stroke", y = "Midean Age", title = "The Avrage Age of Patients who have had a Stroke") +
  theme(legend.position="none") +
  theme_minimal() 
```

![](testing_files/figure-gfm/photographer-1.png)<!-- -->
