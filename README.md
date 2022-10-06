ST558 Project 2 Interacting with APIs: Example with the Financial API
================
Xi Zeng
2022-10-06

# Introduction

This document is a vignette to show how to retrieve data from an API. In
this project, we will be interacting with the API for financial data.
Also, we will build a few functions to interact with some of the
endpoints as well as retrieve data to perform a basic exploratory data
analysis.

# Requirements

To use the functions for interacting with the Financial API, here are
some packages needed:  
- `tidyverse`: Collections of packages with useful functions for data
manipulation and visualization  
- `jsonlite`: Package needed to interact with API and parse data  
- `httr`: Used for load the data we need from API

# API Interaction Functions

Here is the part for the self-defined functions to interact with the
Financial API, as well as some helper functions.

`Function1`

This function is for interacting with the `Daily Open/Close` endpoint
for the Financial API.

``` r
library(tidyverse)
library(httr)
library(jsonlite)
Mydata <- GET("https://api.polygon.io/v2/aggs/ticker/AAPL/range/1/day/2020-06-01/2020-06-17?apiKey=pxkABpfvwGyIl55tOWtNxricS6IwKFYH")
str(Mydata)
```

    ## List of 10
    ##  $ url        : chr "https://api.polygon.io/v2/aggs/ticker/AAPL/range/1/day/2020-06-01/2020-06-17?apiKey=pxkABpfvwGyIl55tOWtNxricS6IwKFYH"
    ##  $ status_code: int 200
    ##  $ headers    :List of 9
    ##   ..$ server                   : chr "nginx/1.19.2"
    ##   ..$ date                     : chr "Thu, 06 Oct 2022 18:36:59 GMT"
    ##   ..$ content-type             : chr "application/json"
    ##   ..$ content-length           : chr "132"
    ##   ..$ connection               : chr "keep-alive"
    ##   ..$ content-encoding         : chr "gzip"
    ##   ..$ vary                     : chr "Accept-Encoding"
    ##   ..$ x-request-id             : chr "c5b9e753fd75dcdec5d77561b7f89e73"
    ##   ..$ strict-transport-security: chr "max-age=15724800; includeSubDomains"
    ##   ..- attr(*, "class")= chr [1:2] "insensitive" "list"
    ##  $ all_headers:List of 1
    ##   ..$ :List of 3
    ##   .. ..$ status : int 200
    ##   .. ..$ version: chr "HTTP/1.1"
    ##   .. ..$ headers:List of 9
    ##   .. .. ..$ server                   : chr "nginx/1.19.2"
    ##   .. .. ..$ date                     : chr "Thu, 06 Oct 2022 18:36:59 GMT"
    ##   .. .. ..$ content-type             : chr "application/json"
    ##   .. .. ..$ content-length           : chr "132"
    ##   .. .. ..$ connection               : chr "keep-alive"
    ##   .. .. ..$ content-encoding         : chr "gzip"
    ##   .. .. ..$ vary                     : chr "Accept-Encoding"
    ##   .. .. ..$ x-request-id             : chr "c5b9e753fd75dcdec5d77561b7f89e73"
    ##   .. .. ..$ strict-transport-security: chr "max-age=15724800; includeSubDomains"
    ##   .. .. ..- attr(*, "class")= chr [1:2] "insensitive" "list"
    ##  $ cookies    :'data.frame': 0 obs. of  7 variables:
    ##   ..$ domain    : logi(0) 
    ##   ..$ flag      : logi(0) 
    ##   ..$ path      : logi(0) 
    ##   ..$ secure    : logi(0) 
    ##   ..$ expiration: 'POSIXct' num(0) 
    ##   ..$ name      : logi(0) 
    ##   ..$ value     : logi(0) 
    ##  $ content    : raw [1:127] 7b 22 74 69 ...
    ##  $ date       : POSIXct[1:1], format: "2022-10-06 18:36:59"
    ##  $ times      : Named num [1:6] 0 0.102 0.125 0.219 0.253 ...
    ##   ..- attr(*, "names")= chr [1:6] "redirect" "namelookup" "connect" "pretransfer" ...
    ##  $ request    :List of 7
    ##   ..$ method    : chr "GET"
    ##   ..$ url       : chr "https://api.polygon.io/v2/aggs/ticker/AAPL/range/1/day/2020-06-01/2020-06-17?apiKey=pxkABpfvwGyIl55tOWtNxricS6IwKFYH"
    ##   ..$ headers   : Named chr "application/json, text/xml, application/xml, */*"
    ##   .. ..- attr(*, "names")= chr "Accept"
    ##   ..$ fields    : NULL
    ##   ..$ options   :List of 2
    ##   .. ..$ useragent: chr "libcurl/7.64.1 r-curl/4.3.2 httr/1.4.4"
    ##   .. ..$ httpget  : logi TRUE
    ##   ..$ auth_token: NULL
    ##   ..$ output    : list()
    ##   .. ..- attr(*, "class")= chr [1:2] "write_memory" "write_function"
    ##   ..- attr(*, "class")= chr "request"
    ##  $ handle     :Class 'curl_handle' <externalptr> 
    ##  - attr(*, "class")= chr "response"

``` r
Mydata$content
```

    ##   [1] 7b 22 74 69 63 6b 65 72 22 3a 22 41 41 50 4c 22 2c 22 71 75 65 72 79 43 6f 75 6e 74 22 3a
    ##  [31] 30 2c 22 72 65 73 75 6c 74 73 43 6f 75 6e 74 22 3a 30 2c 22 61 64 6a 75 73 74 65 64 22 3a
    ##  [61] 74 72 75 65 2c 22 73 74 61 74 75 73 22 3a 22 4f 4b 22 2c 22 72 65 71 75 65 73 74 5f 69 64
    ##  [91] 22 3a 22 63 35 62 39 65 37 35 33 66 64 37 35 64 63 64 65 63 35 64 37 37 35 36 31 62 37 66
    ## [121] 38 39 65 37 33 22 7d

## Including Plots

You can also embed plots, for example:

Note that the `echo = FALSE` parameter was added to the code chunk to
prevent printing of the R code that generated the plot.

``` r
library(rmarkdown)
rmarkdown::render(input = "ST558_update_check.Rmd",
                  output_file = "README.md")
```
