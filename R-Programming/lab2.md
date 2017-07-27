# การเขียน และ การเรียก function

``` r
# Create a sequence of numbers from 32 to 44.
print(seq(32,44))
```

    ##  [1] 32 33 34 35 36 37 38 39 40 41 42 43 44

``` r
# Find mean of numbers from 25 to 82.
print(mean(25:82))
```

    ## [1] 53.5

``` r
# Find sum of numbers frm 41 to 68.
print(sum(41:68))
```

    ## [1] 1526

``` r
# Create a function to print squares of numbers in sequence.
new.function <- function(a) {
   for(i in 1:a) {
      b <- i^2
      print(b)
   }
}   
```

``` r
new.function <- function(a) {
   for(i in 1:a) {
      b <- i^2
      print(b)
   }
}

# Call the function new.function supplying 6 as an argument.
new.function(6)
```

    ## [1] 1
    ## [1] 4
    ## [1] 9
    ## [1] 16
    ## [1] 25
    ## [1] 36

``` r
# Create a function without an argument.
new.function <- function() {
   for(i in 1:5) {
      print(i^2)
   }
}   

# Call the function without supplying an argument.
new.function()
```

    ## [1] 1
    ## [1] 4
    ## [1] 9
    ## [1] 16
    ## [1] 25

``` r
# Create a function with arguments.
new.function <- function(a,b,c) {
   result <- a * b + c
   print(result)
}

# Call the function by position of arguments.
new.function(5,3,11)
```

    ## [1] 26

``` r
# Call the function by names of the arguments.
new.function(a = 11, b = 5, c = 3)
```

    ## [1] 58

``` r
# Create a function with arguments.
new.function <- function(a = 3, b = 6) {
   result <- a * b
   print(result)
}

# Call the function without giving any argument.
new.function()
```

    ## [1] 18

``` r
# Call the function with giving new values of the argument.
new.function(9,5)
```

    ## [1] 45

``` r
# Create a function with arguments.
new.function <- function(a, b) {
   print(a^2)
   print(a)
   print(b)
}

# Evaluate the function without supplying one of the arguments.
new.function(6,9)
```

    ## [1] 36
    ## [1] 6
    ## [1] 9

``` r
a <- 'Start and end with single quote'
print(a)
```

    ## [1] "Start and end with single quote"

``` r
b <- "Start and end with double quotes"
print(b)
```

    ## [1] "Start and end with double quotes"

``` r
c <- "single quote ' in between double quotes"
print(c)
```

    ## [1] "single quote ' in between double quotes"

``` r
d <- 'Double quotes " in between single quote'
print(d)
```

    ## [1] "Double quotes \" in between single quote"

``` r
a <- "Hello"
b <- 'How'
c <- "are you? "

print(paste(a,b,c))
```

    ## [1] "Hello How are you? "

``` r
print(paste(a,b,c, sep = "-"))
```

    ## [1] "Hello-How-are you? "

``` r
print(paste(a,b,c, sep = "", collapse = ""))
```

    ## [1] "HelloHoware you? "

``` r
# Total number of digits displayed. Last digit rounded off.
result <- format(23.123456789, digits = 9)
print(result)
```

    ## [1] "23.1234568"

``` r
# Display numbers in scientific notation.
result <- format(c(6, 13.14521), scientific = TRUE)
print(result)
```

    ## [1] "6.000000e+00" "1.314521e+01"

``` r
# The minimum number of digits to the right of the decimal point.
result <- format(23.47, nsmall = 5)
print(result)
```

    ## [1] "23.47000"

``` r
# Format treats everything as a string.
result <- format(6)
print(result)
```

    ## [1] "6"

``` r
# Numbers are padded with blank in the beginning for width.
result <- format(13.7, width = 6)
print(result)
```

    ## [1] "  13.7"

``` r
# Left justify strings.
result <- format("Hello", width = 8, justify = "l")
print(result)
```

    ## [1] "Hello   "

``` r
# Justfy string with center.
result <- format("Hello", width = 8, justify = "c")
print(result)
```

    ## [1] " Hello  "

``` r
# Changing to Upper case.
result <- toupper("Changing To Upper")
print(result)
```

    ## [1] "CHANGING TO UPPER"

``` r
# Changing to lower case.
result <- tolower("Changing To Lower")
print(result)
```

    ## [1] "changing to lower"
