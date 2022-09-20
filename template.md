Data Input
================

## Data Import: CSVs

``` r
library(tidyverse)
```

    ## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.2 ──
    ## ✔ ggplot2 3.3.6      ✔ purrr   0.3.4 
    ## ✔ tibble  3.1.8      ✔ dplyr   1.0.10
    ## ✔ tidyr   1.2.0      ✔ stringr 1.4.1 
    ## ✔ readr   2.1.2      ✔ forcats 0.5.2 
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()

``` r
library(readxl)
library(haven)
```

``` r
litters_df = read_csv('/Users/qizining/Desktop/Data-Wrangling/FAS_litters.csv')
```

    ## Rows: 49 Columns: 8
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (2): Group, Litter Number
    ## dbl (6): GD0 weight, GD18 weight, GD of Birth, Pups born alive, Pups dead @ ...
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
litters_df = janitor::clean_names(litters_df)
```

Look at the data

``` r
head(litters_df)
```

    ## # A tibble: 6 × 8
    ##   group litter_number gd0_weight gd18_weight gd_of_birth pups_…¹ pups_…² pups_…³
    ##   <chr> <chr>              <dbl>       <dbl>       <dbl>   <dbl>   <dbl>   <dbl>
    ## 1 Con7  #85                 19.7        34.7          20       3       4       3
    ## 2 Con7  #1/2/95/2           27          42            19       8       0       7
    ## 3 Con7  #5/5/3/83/3-3       26          41.4          19       6       0       5
    ## 4 Con7  #5/4/2/95/2         28.5        44.1          19       5       1       4
    ## 5 Con7  #4/2/95/3-3         NA          NA            20       6       0       6
    ## 6 Con7  #2/2/95/3-2         NA          NA            20       6       0       4
    ## # … with abbreviated variable names ¹​pups_born_alive, ²​pups_dead_birth,
    ## #   ³​pups_survive

``` r
skimr::skim(litters_df)
```

`read_csv` options

``` r
read_csv('/Users/qizining/Desktop/Data-Wrangling/FAS_litters.csv', na = c("", "NA", 999, 88), skip = 2)
```

### Other file formats

We need to read in an excwl sheet

``` r
mlb_df = read_excel('/Users/qizining/Desktop/Data-Wrangling/mlb11.xlsx')
```

``` r
lotr_words = read_excel('/Users/qizining/Desktop/Data-Wrangling/LotR_Words.xlsx',
                        range = 'B3:D6')
```

### Read in a SAS dataset.

``` r
pulse_df = read_sas('/Users/qizining/Desktop/Data-Wrangling/public_pulse_data.sas7bdat')
```

## Data export

``` r
write_csv(lotr_words, file = '/Users/qizining/Desktop/Data-Wrangling/LotR_Words.csv')
```

## Why not base r???

``` r
dont_do_this_df = read.csv('/Users/qizining/Desktop/Data-Wrangling/FAS_litters.csv')
```
