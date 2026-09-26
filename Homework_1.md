Homework 1
================
Natasha Woon
2026-09-25

# Problem 1

## Load Packages

``` r
library(tidyverse)
```

    ## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ## ✔ dplyr     1.2.1     ✔ readr     2.2.0
    ## ✔ forcats   1.0.1     ✔ stringr   1.6.0
    ## ✔ ggplot2   4.0.3     ✔ tibble    3.3.1
    ## ✔ lubridate 1.9.5     ✔ tidyr     1.3.2
    ## ✔ purrr     1.2.2     
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()
    ## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors

``` r
data("penguins", package = "palmerpenguins")
```

## Description of Penguins Data set

The `penguins` data set contains data on penguins from three different
species (Adelie, Chinstrap and Gentoo). Important variables include
species, island, bill length, bill depth, flipper length, body mass,
sex, and year.

This data set has 344 observations and 8 columns.

The mean flipper length is 200.9152047 mm.

## Scatterplot

``` r
ggplot(data = penguins,
       mapping = aes(bill_length_mm, flipper_length_mm, color = species)) + geom_point()
```

![](Homework_1_files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->

``` r
ggsave("scatterplot.png")
```

    ## Saving 7 x 5 in image

# Problem 2

``` r
set.seed(123)

problem2_df = 
  tibble(
    random_sample = rnorm(10),
    logical_vector = (random_sample > 0),
    character_vector = c("Dog", "Giraffe", "Hamster", "Frog", "Elephant", "Cat", "Moose", "Otter", "Lizard", "Kangaroo"), 
    factor_vector = factor (c("Medium", "Large", "Small", "Small", "Large", "Medium", "Large", "Medium", "Small", "Large"))
  )

problem2_df
```

    ## # A tibble: 10 × 4
    ##    random_sample logical_vector character_vector factor_vector
    ##            <dbl> <lgl>          <chr>            <fct>        
    ##  1       -0.560  FALSE          Dog              Medium       
    ##  2       -0.230  FALSE          Giraffe          Large        
    ##  3        1.56   TRUE           Hamster          Small        
    ##  4        0.0705 TRUE           Frog             Small        
    ##  5        0.129  TRUE           Elephant         Large        
    ##  6        1.72   TRUE           Cat              Medium       
    ##  7        0.461  TRUE           Moose            Large        
    ##  8       -1.27   FALSE          Otter            Medium       
    ##  9       -0.687  FALSE          Lizard           Small        
    ## 10       -0.446  FALSE          Kangaroo         Large

``` r
mean(pull(problem2_df, random_sample))
```

    ## [1] 0.07462564

``` r
mean(pull(problem2_df, logical_vector))
```

    ## [1] 0.5

``` r
mean(pull(problem2_df, character_vector))
```

    ## Warning in mean.default(pull(problem2_df, character_vector)): argument is not
    ## numeric or logical: returning NA

    ## [1] NA

``` r
mean(pull(problem2_df, factor_vector))
```

    ## Warning in mean.default(pull(problem2_df, factor_vector)): argument is not
    ## numeric or logical: returning NA

    ## [1] NA

After taking the mean of each variable in the dataset, it is clear that
the mean value can only be generated for numerical and logical vectors.
Numerical variables can be averaged. Logical variables treat TRUE as 1
and FALSE and 0, and can therefore produce and average. However,
character and factor vectors produced a warning NA result, and were not
able to generate a mean value when utilizing the mean() function. This
makes sense because R cannot generate a mean of values such as `dog` and
and `lizard`.

``` r
as.numeric(pull(problem2_df, logical_vector))
as.numeric(pull(problem2_df, character_vector))
```

    ## Warning: NAs introduced by coercion

``` r
as.numeric(pull(problem2_df, factor_vector))
```

Applying the `as.numeric` function to the logical vector works since
TRUE or FALSE can be converted to 1 or 0s, and thus, a mean can be
taken. However, the `as.numeric` function cannot be applied to character
vectors because the character strings cannot be converted into numbers.
Lastly, the `as.numeric` function converts the factor variables into the
number assigned to each factor level, and does not actually convey the
factors (Small, Medium or Large) into numbers, and therefore taking the
mean here would not be meaningful.
