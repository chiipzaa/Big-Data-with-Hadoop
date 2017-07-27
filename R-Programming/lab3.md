# การอ่านค่าจากไฟล์ข้อมูลแบบ csv

``` r
data <- read.csv("input.csv")

print(is.data.frame(data))
```

    ## [1] TRUE

``` r
print(ncol(data))
```

    ## [1] 5

``` r
print(nrow(data))
```

    ## [1] 8

``` r
# Create a data frame.
data <- read.csv("input.csv")

# Get the max salary from data frame.
sal <- max(data$salary)
print(sal)
```

    ## [1] 843.25

``` r
# Create a data frame.
data <- read.csv("input.csv")

# Get the max salary from data frame.
sal <- max(data$salary)

# Get the person detail having max salary.
retval <- subset(data, salary == max(salary))
print(retval)
```

    ##   id name salary start_date    dept
    ## 5 NA Gary 843.25 2015-03-27 Finance

``` r
# Create a data frame.
data <- read.csv("input.csv")

retval <- subset( data, dept == "IT")
print(retval)
```

    ##   id     name salary start_date dept
    ## 1  1     Rick  623.3 2012-01-01   IT
    ## 3  3 Michelle  611.0 2014-11-15   IT
    ## 6  6     Nina  578.0 2013-05-21   IT

``` r
# Create a data frame.
data <- read.csv("input.csv")

info <- subset(data, salary > 600 & dept == "IT")
print(info)
```

    ##   id     name salary start_date dept
    ## 1  1     Rick  623.3 2012-01-01   IT
    ## 3  3 Michelle  611.0 2014-11-15   IT

``` r
# Create a data frame.
data <- read.csv("input.csv")
retval <- subset(data, as.Date(start_date) > as.Date("2014-01-01"))

# Write filtered data into a new file.
write.csv(retval,"output.csv")
newdata <- read.csv("output.csv")
print(newdata)
```

    ##   X id     name salary start_date    dept
    ## 1 3  3 Michelle 611.00 2014-11-15      IT
    ## 2 4  4     Ryan 729.00 2014-05-11      HR
    ## 3 5 NA     Gary 843.25 2015-03-27 Finance
    ## 4 8  8     Guru 722.50 2014-06-17 Finance

``` r
# Create a data frame.
data <- read.csv("input.csv")
retval <- subset(data, as.Date(start_date) > as.Date("2014-01-01"))

# Write filtered data into a new file.
write.csv(retval,"output.csv", row.names = FALSE)
newdata <- read.csv("output.csv")
print(newdata)
```

    ##   id     name salary start_date    dept
    ## 1  3 Michelle 611.00 2014-11-15      IT
    ## 2  4     Ryan 729.00 2014-05-11      HR
    ## 3 NA     Gary 843.25 2015-03-27 Finance
    ## 4  8     Guru 722.50 2014-06-17 Finance
