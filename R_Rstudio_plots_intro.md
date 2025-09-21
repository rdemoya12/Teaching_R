Introduction to R & RStudio
================
Ricardo A. DeMoya
6/19/2023

# R and Rstudio

This introduction assumes you have downloaded R and RStudio, if not you
can get both here [R and
Rstudio](https://posit.co/download/rstudio-desktop/). Learning the
syntax (or way of writing) in the R programming language will come with
time and free online cheat sheets provide you more resources to sharpen
your skills. But for now just start playing with data and then you can
plan more specific projects. This programming language can be used to
make nearly any document type using rmarkdown, the same package used to
make this tutorial. By the end of the lesson you will be able to:

1.  Know how to find help within RStudio
2.  Access data sets included with R for practicing purposes
3.  And some basic plotting

We will go through this step by step together. Please ask questions and
I will be happy to answer them and suggest best practices in R. Also to
be fair R programming syntax and layouts differ among the best
programmers, so comment on your experiences and let me know what you
think at the end of the tutorial.

### Use the `help()` function to get information

The `help()` function is a great tool for beginners to get the help they
need on specific functions, packages, or data sets in R. The
documentation accessed with the `help()` function provides you all the
parameters used and their default values if not specified, as well as
descriptions of each parameter and values produced by the function.
Sometime you even get examples of how to use the function at the bottom
of the help page. Let’s use the the `help()` function to learn about the
`help()` function! Run the code below in your console and you will see
the documentation for the `help()` function appear in a browser window
or the help tab of your bottom right window in RStudio.

``` r
help("help") # Can use the help() function to get package info
```

As you can see, when you run the above code you have all the parameters
and descriptions of each for the `help()` function. This allows you to
understand the function well and to see what options are available.

Looking for information on packages is just as easy as above just enter
the package name into`help()` and you will be provided a description of
the package and parameters involved.

``` r
help("Math") # help() on a package
```

Data sets can also be queried. Here we will look at the `datasets`
package so we can see what is available for us to practice.

``` r
help("datasets")

# To see the data sets available
library(help = "datasets")
```

### Getting started: The datasets library in R

This `datasets` library contains plenty of data and data types to keep
you occupied for a long while. Here we will use them to just explore
some functions.

``` r
# Upload the datasets library
library("datasets")
```

### Importing one data set from Australia

First we upload some data from the country of Australia, the number of
residents over so many years measured quarterly.

``` r
# A dataset of quarterly time series data
data("austres")
```

Thinking of practical uses for data like these would include population
growth rates, and could be correlated with other factors like natural
disasters or tourism fluctuations. The most important thing to do when
working with new data you haven’t seen before that you get to know your
data.

### Understanding the data

It is good practice to always look at the data you are working on by
printing it to the console or exporting it as a file. But we will cover
making files in another tutorial so let’s just focus on printing to the
console. Using the `print()` function allows us to print anything to the
console and helps with trouble shooting errors. Here we see that the
data is the population taken quarterly from 1971 to 1993.

``` r
print(austres) # Print all data to the console 
```

    ##         Qtr1    Qtr2    Qtr3    Qtr4
    ## 1971         13067.3 13130.5 13198.4
    ## 1972 13254.2 13303.7 13353.9 13409.3
    ## 1973 13459.2 13504.5 13552.6 13614.3
    ## 1974 13669.5 13722.6 13772.1 13832.0
    ## 1975 13862.6 13893.0 13926.8 13968.9
    ## 1976 14004.7 14033.1 14066.0 14110.1
    ## 1977 14155.6 14192.2 14231.7 14281.5
    ## 1978 14330.3 14359.3 14396.6 14430.8
    ## 1979 14478.4 14515.7 14554.9 14602.5
    ## 1980 14646.4 14695.4 14746.6 14807.4
    ## 1981 14874.4 14923.3 14988.7 15054.1
    ## 1982 15121.7 15184.2 15239.3 15288.9
    ## 1983 15346.2 15393.5 15439.0 15483.5
    ## 1984 15531.5 15579.4 15628.5 15677.3
    ## 1985 15736.7 15788.3 15839.7 15900.6
    ## 1986 15961.5 16018.3 16076.9 16139.0
    ## 1987 16203.0 16263.3 16327.9 16398.9
    ## 1988 16478.3 16538.2 16621.6 16697.0
    ## 1989 16777.2 16833.1 16891.6 16956.8
    ## 1990 17026.3 17085.4 17106.9 17169.4
    ## 1991 17239.4 17292.0 17354.2 17414.2
    ## 1992 17447.3 17482.6 17526.0 17568.7
    ## 1993 17627.1 17661.5

Sometimes it is better to only look at a portion of the data, especially
when the sample size increases by hundreds or thousands. The n
parameter, set to 5 in the `head()` function, allows you to see only the
first 5 entries in the data set

``` r
head(austres,n=5) # Prints out the first 5 lines of the data
```

    ## [1] 13067.3 13130.5 13198.4 13254.2 13303.7

### A little practice to see if you understand the `help()` function

Since we learned to use the `help()` function I have introduced three
new functions `data()`, `print()`, and `head()`. So take a minute and
use the `help()` on each of these to learn about the parameters
available.

- Can you tell me what the default S3 integer for the n parameter in the
  `head()` function is?
- What does the quote parameter from the `print()` function do?

## Now let’s explore some data sets and make plots

Many base functions exist to inspect the data you input like `max()`,
`min()`, `range()` and `summary()`. Using these functions helps you see
all sides of the data, which can be critical for down stream analysis
and plotting. Remember if you want to learn more about anything we do
going forward the `help()` function works well.

``` r
print(paste0("Max value: ", max(austres))) # the max value in the data
```

    ## [1] "Max value: 17661.5"

``` r
print(paste0("Min value: ", min(austres))) # the min value in the data
```

    ## [1] "Min value: 13067.3"

``` r
quantile(austres) # the upper and lower quantile of the data
```

    ##      0%     25%     50%     75%    100% 
    ## 13067.3 14110.1 15184.2 16398.9 17661.5

``` r
range(austres) # the range of the data
```

    ## [1] 13067.3 17661.5

``` r
summary(austres) # Summary of data
```

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ##   13067   14110   15184   15273   16399   17662

### Plotting your data so others can see what you see

Plotting data is the number one way to convince others of your analysis
and interpretation of the data. This is critical for any project that
needs to show a lot of complex data in a more digestible way. Below we
plot the `austres` data set using a built in `plot()` function.

``` r
plot(austres) # to visualize the data
```

![](R_Rstudio_intro_v2_files/figure-gfm/austres1-1.png)<!-- -->

From this plot you can clearly see an increase in residents in Australia
between 1971 and 1993. This graph could be used in publications to show
that is the case and others would see it and either agree or disagree.
The `plot()` function works fine for this data set, but another more
powerful package for plotting exist in `ggplot2`.

### Plotting with `ggplot2`

Because the `austres` data set is kinda boring, let’s use another data
set. The `iris` data set contains different data on flowers and the
length of various structures. This is a little more complicated compared
to the `austres` data set, but we can explore the data like before.

``` r
data("iris") # Load another data set
```

### **ALWALYS** inspect your data

Do not forget to look at the data, this will help you to understand the
data and make the right choices for downstream analyses.

``` r
print(head(iris))
```

    ##   Sepal.Length Sepal.Width Petal.Length Petal.Width Species
    ## 1          5.1         3.5          1.4         0.2  setosa
    ## 2          4.9         3.0          1.4         0.2  setosa
    ## 3          4.7         3.2          1.3         0.2  setosa
    ## 4          4.6         3.1          1.5         0.2  setosa
    ## 5          5.0         3.6          1.4         0.2  setosa
    ## 6          5.4         3.9          1.7         0.4  setosa

``` r
summary(iris)
```

    ##   Sepal.Length    Sepal.Width     Petal.Length    Petal.Width   
    ##  Min.   :4.300   Min.   :2.000   Min.   :1.000   Min.   :0.100  
    ##  1st Qu.:5.100   1st Qu.:2.800   1st Qu.:1.600   1st Qu.:0.300  
    ##  Median :5.800   Median :3.000   Median :4.350   Median :1.300  
    ##  Mean   :5.843   Mean   :3.057   Mean   :3.758   Mean   :1.199  
    ##  3rd Qu.:6.400   3rd Qu.:3.300   3rd Qu.:5.100   3rd Qu.:1.800  
    ##  Max.   :7.900   Max.   :4.400   Max.   :6.900   Max.   :2.500  
    ##        Species  
    ##  setosa    :50  
    ##  versicolor:50  
    ##  virginica :50  
    ##                 
    ##                 
    ## 

### Also explore the data if you do not have experience with it

``` r
dim(iris) # Tells you what the dimensions are for the iris dataset, (rows, columns)
```

    ## [1] 150   5

``` r
names(iris) # Gives you the column names of the iris dataset
```

    ## [1] "Sepal.Length" "Sepal.Width"  "Petal.Length" "Petal.Width"  "Species"

## The ggplot2 library is great for making figures in R

There are many libraries for plotting data in r. These include
`ggplot2`, `Lattice`, `RGL`, `Esquisse`, `highcharter`, `Leaflet`,
`RColorBrewer`, `sunburstR`, and `dygraphs`. It is up to the user to
decide what packages meet your needs. Here we use `ggplot2` to just plot
a few simple graphs. It is also encouraged to use the base `plot()`
function or others.

``` r
library("ggplot2") # Upload the ggplot2 library
```

### Histogram of sepal length frequency

``` r
bar <- ggplot(iris, aes(x=Sepal.Length))+ # Sets up the stage for ggplot
  geom_histogram(bins = 15)+ # This actually sets the ggplot to a histogram type
  ylab("Frequency") # Changes the labels of the axis, xlab() or ylab()
bar
```

![](R_Rstudio_intro_v2_files/figure-gfm/plots2-1.png)<!-- -->

One great part about the `ggplot2` package is the built-in customization
of any graph, like fill and alpha.

``` r
bar2 <- ggplot(iris, aes(x=Sepal.Length))+ # Sets up a ggplot canvas
  geom_histogram(fill="lightblue",colour = "purple",bins = 15,alpha=0.5)+ # This sets the ggplot to a histogram type
  ylab("Frequency") # Changes the labels of the axis, xlab() or ylab()
bar2
```

![](R_Rstudio_intro_v2_files/figure-gfm/unnamed-chunk-1-1.png)<!-- -->

### A box plot for species vs septal length

``` r
box <- ggplot(iris, aes(x= Species, y= Sepal.Length))+
  geom_boxplot(fill="green",colour = "blue")+
  ylab("Sepal Length")
box
```

![](R_Rstudio_intro_v2_files/figure-gfm/plots3-1.png)<!-- -->

### Labeling data is easy with `ggplot2`

Here we label the outlier in the virginica species with a red asterisk
by adding code into the `geom_boxplot()` function. You can also change
the other aspects of the plot with `ggplot()`, like `ylab()` or `main()`

``` r
box2 <- ggplot(iris, aes(x= Species, y= Sepal.Length))+
  geom_boxplot(fill="green",colour = "blue",
               outlier.colour = "red", outlier.shape = 8,
               outlier.size = 4)+ # Labels the outlier in red
  ylab("Sepal Length") # Renames the y axis label
box2
```

![](R_Rstudio_intro_v2_files/figure-gfm/plots4-1.png)<!-- -->

### A dot plot can also show patterns

``` r
dot <- ggplot(data = iris) +
  aes(x = Petal.Length, y = Petal.Width) +
  geom_point(aes(color = Species, shape = Species)) +
  geom_smooth(method = lm,formula = y ~ x)+
  ylab("Petal Length")+ # Renames the y axis label
  xlab("") # Removes the label for x-axis since legend is present
dot
```

![](R_Rstudio_intro_v2_files/figure-gfm/plots5-1.png)<!-- -->

The `ggplot2` package allows for many different kinds of plots and the
customization options are plentiful. Another tutorial will be avaiable
that will focus on just `ggplot2` and `theme()` another powerful
function for plots.

## Challenges

1.  Use the `help()` function to learn about `dim()`, `ggplot()`,
    `plot()`, `names()`.
2.  Design a project of your own, maybe on your current work

## Ending remarks

Hopefully this introduction to R and RStudio was not too intense. The
open source R program allows for plenty of variation among code and
processes, so don’t feel overwhelmed. There is too much to learn all at
once but taking it a piece at a time is best. The resources online are
endless and soon you will know what to search for to get the most direct
answer you need. Just keep at it and don’t give up. Together we will
tackle R and you will be coding your own projects in no time!
