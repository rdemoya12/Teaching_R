Variables and Data Types in R
================
Ricardo A. DeMoya
6/20/2023

# Variables in R

## WHAT is a variable!

Variables are names or identifiers you assign to a value. This value can
be user provided or calculated and assigned a variable name. You will
use variable all the time in R or any coding language, so it is a good
idea to familiarize yourself with them here.

## Variable naming rules and strategies

The rules/suggestions of variable naming in R are as follows:

1.  Must start with a letter and can be a combination of letters,
    digits, periods(.), and underscores(\_).
2.  Starts with period(.), it cannot be followed by a digit.
3.  Cannot start with a number or underscore (\_)
4.  Are case-sensitive (diff, Diff and DIFF are three different
    variables)
5.  Reserved words are not allowed to be variable names (explained
    below)

### Popular naming conventions

There are a few different naming conventions that have been adopted by
most programmers and are great for keeping things short sweet and to the
point. A few of these include:

### camelCase, PascalCase, snake_case

As you can see below, camel case is when the first word has a lower case
letter and all words in the description afterwards get a capital first
letter. Pascal case is the same but all words get capital first letters.
And finally snake case were each word is separated by an underscore.

``` r
camelCase <- "camels"

PascalCase <- "pascal"

snake_case <- "snakes"
```

These are the most popular systems for variable names out there, so use
one of these or make your own, like one with periods separating words.

``` r
period.case <- "Period"
```

It is good practice to use a standard system for naming your variables
that provide some info on the variable value contained. If not you can
end up with something like this:

``` r
# Bad variable naming conventions
var1 = 30 # age
var2 = TRUE # do they smoke

# Later in your code
var32 = "blue" # color of eyes
```

The problem is, far down the end of your code, you will have no idea
what var2 was by the time you get to var32. The remedy for this is to
use meaningful names when naming variables and come up with a system for
projects that is human readable.

This will make your code more universal and allow others to understand
and build or fix it quickly.

``` r
# Better variable naming conventions
Age <- 30
smokingStatus <- TRUE
eyeColor = "blue"
```

This allows for less commenting and makes for easier to understand code
in the long run. It is important to build good habits now that will make
your coding career sustainable and more accessible to the community of
coders.

### Reserved words in R

In R you can name your variables according the rules above, but there
are still some words that are off limits for users. These include: `if`,
`else`, `repeat`, `while`, `function`, `for`, `in`, `next`, `break`,
`TRUE`, `FALSE`, `NULL`, `Inf`, `NaN`, `NA`, `NA_character_`,
`NA_integer_`, `NA_real_`, `NA_complex_`, and `...`.

``` r
Inf <- 0
```

    ## Error in Inf <- 0: invalid (do_set) left-hand side to assignment

This error shows us that we have an invalid variable name in “Inf” as it
is one of our reserved words in R.

### Best practices when naming variables

Avoid the reserved words and be creative with your naming design. You
will also need to review your variables and be sure the names are not
overly similar.

``` r
# Example of too similar
start <- 1 # starts the analysis at position 1

begin <- 10 # starts the next analysis at position 10

# Not perfect, but better nomenclature
startAnalysis1 <- 1

start_analysis_2 <- 10
```

## Assigning variables

If you haven’t noticed, I suggest you look back at the last excerpts of
code and tell me how many ways of assigning a variable you see? These
are two of three main options for assigning a variable. But which one is
superior?

### `=` operator or the arrow operator `<-`

I showed above how to assign a variable using the equal sign `=`
operator or the arrow `<-` operator. And in most cases either works, but
best practice is to **ALWAYS use the arrow operator `<-`**. This reduces
ambiguity when setting parameters or running concise one line code.

``` r
wow = 2 # Bad practice

whoo <- 2

2->mooo

print(c(wow, whoo, mooo))
```

    ## [1] 2 2 2

Other arrow operators exists to influence global objects and not just
local ones like the above arrow operator. These global arrow operators
are like this (`<<-` or `->>`) the arrow will always point to the object
getting assigned a value from the other end. This goes for all arrow
operators, they point to the object the value to be assigned.

### Using the `assign()` function

This can be a little more confusing compared to the arrow operator, but
in some cases this will allow for more flexibility in your code. Just to
keep in mind for those special cases.

``` r
water <- "bob"
assign(x = water,
       value = "H2O")
water # is still "bob"
```

    ## [1] "bob"

``` r
bob # is now "H2O"
```

    ## [1] "H2O"

### Assigning multiple variables

It is possible to make multiple variables have the same value.

``` r
var10 <- var11 <- var12 <- "Purple"

print(c(var10, var11, var12))
```

    ## [1] "Purple" "Purple" "Purple"

# Data types in R

Data types exist so programming languages can look at multiple types of
data. For example the differences between text and numeric data. Here we
will define these and make some example variables of each type.

## Numeric, integer, and complex data types

Numeric types deal with digits and decimals, while the integer types
deal with only whole numbers without decimals or fractions and can be
denoted by being followed by an L, like `5L`. Complex types deal with
real and imaginary numbers, like `1+4i`

### Numeric values

``` r
some_number <- 5
another_number <- 4
lastNum <- 12
```

### Integer values and complex numbers

``` r
myInteger <- 10L
uno_mas <- 1000L

mas <- 1000
dos <- 1000.25

imagine <- 25+4i
```

When in you have a decimal point like the dos variable above you will
get the integer or whole number of the digits assigned to the integer.
When in doubt of what a number value is use `is.integer()`

``` r
print(c(myInteger,uno_mas))
```

    ## [1]   10 1000

``` r
print(c(mas,dos))
```

    ## [1] 1000.00 1000.25

``` r
print(c(is.integer(myInteger),is.integer(uno_mas)))
```

    ## [1] TRUE TRUE

``` r
print(c(is.integer(mas),is.integer(dos)))
```

    ## [1] FALSE FALSE

The last FALSE statements here show us that the `mas` and `dos`
variables are not integers. Let’s see what type it is using `typeof()`

### The `typeof()` or `class()` functions

The `typeof()` function will return the R internal type or storage mode
of a data object. This can be very helpful when getting to know your
data. The `class()` function will return the implicit class if no class
attribute exist, these are similar to the `typeof()` categories. Don’t
forget your `help()` or `?typeof()` to get information about the
functions we use throughout these tutorials.

``` r
typeof(dos)
```

    ## [1] "double"

``` r
typeof(mas)
```

    ## [1] "double"

Here “double” stands for double precision floating point numbers also
numeric in some cases, while integer refers to whole numbers with an “L”
at the end of the digit.

``` r
print(c(class(dos),class(uno_mas),class(imagine)))
```

    ## [1] "numeric" "integer" "complex"

``` r
# same categories
print(c(typeof(dos),typeof(uno_mas),typeof(imagine)))
```

    ## [1] "double"  "integer" "complex"

## Boolean or logical values

These are the binary `TRUE` or `FALSE` data types.

``` r
dos_mas <- TRUE
no_mas <- FALSE

print(c(typeof(no_mas),class(no_mas),class(dos)))
```

    ## [1] "logical" "logical" "numeric"

## The character data type

This is the data type that handles text data. This can be strings that
are made up of characters, like “abc” or “strings are a thing”

``` r
char <- "char"
stringy <- "a string here"
print(c(class(char), typeof(stringy)))
```

    ## [1] "character" "character"

# Final thoughts

Here we tried to provide some understanding of the R programming
language. We covered assigning variables and the different variable data
types in R. Further exploration of the character and string types
requires its own tutorial. This tutorial is a quick introduction, so to
better understand R you should play with some example data from the
`datasets` package.
