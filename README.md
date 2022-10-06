ST558 Project 2 Interacting with APIs: Example with the Financial API
================
Xi Zeng
2022-10-06

\#Introduction  
This document is a vignette to show how to retrieve data from an API. In
this project, we will be interacting with the API for financial data.
Also, we will build a few functions to interact with some of the
endpoints as well as retrieve data to perform a basic exploratory data
analysis.

\#Requirements  
To use the functions for interacting with the Financial API, here are
some packages needed:  
- `tidyverse`: Collections of packages with useful functions for data
manipulation and visualization  
- `jsonlite`: Package needed to interact with API and parse data

\#API Interaction Functions  
Here is the part for the self-defined functions to interact with the
Financial API, as well as some helper functions.

## Including Plots

You can also embed plots, for example:

Note that the `echo = FALSE` parameter was added to the code chunk to
prevent printing of the R code that generated the plot.

``` r
library(rmarkdown)
rmarkdown::render(input = "ST558_update_check.Rmd",
                  output_file = "README.md")
```
