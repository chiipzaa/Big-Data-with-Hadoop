# เรียนรู้เรื่องการประกาศตัวแปรชนิดต่าง ๆ
======================================

``` r
myString <- "Hello, World!"
print ( myString)
```

    ## [1] "Hello, World!"

``` r
# My first program in R Programming
myString <- "Hello, World!"

print ( myString)
```

    ## [1] "Hello, World!"

``` r
# My first program in R Programming
if(FALSE) {
   "This is a demo for multi-line comments and it should be put inside either a single
      OR double quote"
}

myString <- "Hello, World!"
print ( myString)
```

    ## [1] "Hello, World!"

``` r
# Create a vector.
apple <- c('red','green',"yellow")
print(apple)
```

    ## [1] "red"    "green"  "yellow"

``` r
# Get the class of the vector.
print(class(apple))
```

    ## [1] "character"

``` r
# Create a list.
list1 <- list(c(2,5,3),21.3,sin)

# Print the list.
print(list1)
```

    ## [[1]]
    ## [1] 2 5 3
    ## 
    ## [[2]]
    ## [1] 21.3
    ## 
    ## [[3]]
    ## function (x)  .Primitive("sin")

``` r
# Create a matrix.
M = matrix( c('a','a','b','c','b','a'), nrow = 2, ncol = 3, byrow = TRUE)
print(M)
```

    ##      [,1] [,2] [,3]
    ## [1,] "a"  "a"  "b" 
    ## [2,] "c"  "b"  "a"

``` r
# Create an array.
a <- array(c('green','yellow'),dim = c(3,3,2))
print(a)
```

    ## , , 1
    ## 
    ##      [,1]     [,2]     [,3]    
    ## [1,] "green"  "yellow" "green" 
    ## [2,] "yellow" "green"  "yellow"
    ## [3,] "green"  "yellow" "green" 
    ## 
    ## , , 2
    ## 
    ##      [,1]     [,2]     [,3]    
    ## [1,] "yellow" "green"  "yellow"
    ## [2,] "green"  "yellow" "green" 
    ## [3,] "yellow" "green"  "yellow"

``` r
# Create a vector.
apple_colors <- c('green','green','yellow','red','red','red','green')

# Create a factor object.
factor_apple <- factor(apple_colors)

# Print the factor.
print(factor_apple)
```

    ## [1] green  green  yellow red    red    red    green 
    ## Levels: green red yellow

``` r
print(nlevels(factor_apple))
```

    ## [1] 3

``` r
# Create the data frame.
BMI <-  data.frame(
   gender = c("Male", "Male","Female"), 
   height = c(152, 171.5, 165), 
   weight = c(81,93, 78),
   Age = c(42,38,26)
)
print(BMI)
```

    ##   gender height weight Age
    ## 1   Male  152.0     81  42
    ## 2   Male  171.5     93  38
    ## 3 Female  165.0     78  26
