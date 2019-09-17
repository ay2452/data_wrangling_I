Data Import
================
Alicia Yang
9/17/2019

## Load in dataset

``` r
##reads in a dataset
##general rule, use relative path, NOT absolute path 
litters_data = read_csv(file = "./data/FAS_litters.csv")
```

    ## Parsed with column specification:
    ## cols(
    ##   Group = col_character(),
    ##   `Litter Number` = col_character(),
    ##   `GD0 weight` = col_double(),
    ##   `GD18 weight` = col_double(),
    ##   `GD of Birth` = col_double(),
    ##   `Pups born alive` = col_double(),
    ##   `Pups dead @ birth` = col_double(),
    ##   `Pups survive` = col_double()
    ## )

``` r
litters_data = janitor::clean_names(litters_data)
##take janitor & rewriting data 
```

\#\#Load in pups data

``` r
pups_data = read_csv(file = "./data/FAS_pups.csv")
```

    ## Parsed with column specification:
    ## cols(
    ##   `Litter Number` = col_character(),
    ##   Sex = col_double(),
    ##   `PD ears` = col_double(),
    ##   `PD eyes` = col_double(),
    ##   `PD pivot` = col_double(),
    ##   `PD walk` = col_double()
    ## )

``` r
pups_data = janitor::clean_names(pups_data)
##making clear that clean_names function is in janitor function; can also do a library(janitor) so don't have to specify 
tail(pups_data)
```

    ## # A tibble: 6 x 6
    ##   litter_number   sex pd_ears pd_eyes pd_pivot pd_walk
    ##   <chr>         <dbl>   <dbl>   <dbl>    <dbl>   <dbl>
    ## 1 #2/95/2           2       4      12        7       9
    ## 2 #2/95/2           2       3      13        6       8
    ## 3 #2/95/2           2       3      13        7       9
    ## 4 #82/4             2       4      13        7       9
    ## 5 #82/4             2       3      13        7       9
    ## 6 #82/4             2       3      13        7       9

``` r
skimr::skim(pups_data)
```

    ## Skim summary statistics
    ##  n obs: 313 
    ##  n variables: 6 
    ## 
    ## ── Variable type:character ──────────────────────────────────────────────────────────────────
    ##       variable missing complete   n min max empty n_unique
    ##  litter_number       0      313 313   3  15     0       49
    ## 
    ## ── Variable type:numeric ────────────────────────────────────────────────────────────────────
    ##  variable missing complete   n  mean   sd p0 p25 p50 p75 p100     hist
    ##   pd_ears      18      295 313  3.68 0.59  2   3   4   4    5 ▁▁▅▁▁▇▁▁
    ##   pd_eyes      13      300 313 12.99 0.62 12  13  13  13   15 ▂▁▇▁▁▂▁▁
    ##  pd_pivot      13      300 313  7.09 1.51  4   6   7   8   12 ▃▆▇▃▂▁▁▁
    ##   pd_walk       0      313 313  9.5  1.34  7   9   9  10   14 ▁▅▇▅▃▂▁▁
    ##       sex       0      313 313  1.5  0.5   1   1   2   2    2 ▇▁▁▁▁▁▁▇
