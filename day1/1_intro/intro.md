---
title       : "An Introduction to R"
subtitle    : "Day 1: Morning, Session 1"
author      : Daniel Anderson
job         : "R Training: Florida State University, June 21, 2016"
framework   : io2012    # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : zenburn      # 
widgets     : [mathjax]     # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
--- &twocol

<style>
em {
  font-style: italic
}
</style>

<style>
strong {
  font-weight: bold;
}
</style>

## Hi!

*** =left

# Who am I?
Daniel Anderson 
* IES post-doc at UO <span style="color:green; font-size:8pt;"> (Go Ducks!) </span>
* Dad (two daughters: 4 and 2)
* Quantitative educational researcher who **loves** R
* Primary areas of interest
  + R, big data, "educational data science"
  + Growth modeling (primarily through multilevel models)
  + Bayesian estimation (still learning, always learning)
  + Systems-level processes (specifically teachers)

*** =right

<div align = "center">
<img src = ../assets/img/thefam.jpg width = 400 height = 300>
</div>

----
## My jump to R
* Began in earnest about 3 years ago
* Time consuming
* Very frustrating at times 
* One of the most professionally rewarding things I've done
* I'm still learning more every day

----
## Exciting parts of R (to me)
* Dynamic document generation
* Incredible graphing power (which is expanding all the time)
* Extremely flexible
* Substantial gains in efficiency
* Lots of really smart people working hard every day to make R better

---- &twocol
# Dynamic document generation

*** =left
<div align = "right">
<img src = ../assets/img/rMarkdownCode.png width = 500 height = 600>
</div>

*** =right
<div align = "left">
<img src = ../assets/img/fullRMarkdownDoc.png width = 500 height = 600>
</div>

---- &twocol
# More advanced dynamic documents

*** =left
<div align = "right">
<img src = ../assets/img/rnwCode.png width = 500 height = 600>
</div>

*** =right
<div align = "left">
<img src = ../assets/img/rnwPaper.png width = 500 height = 600>
</div>


---- &twocol
# Incredible graphing power

High density scatterplot



*** =left

![plot of chunk standardScatter](assets/fig/standardScatter-1.png)

*** =right

![plot of chunk hdScatter](assets/fig/hdScatter-1.png)


----
## Flexible, clean, displays

![plot of chunk cleanPlot](assets/fig/cleanPlot-1.png)

<span style="color:gray; font-size:10pt;">Credit: Mijke Rhemtulla 
 (http://shinyapps.org/apps/RGraphCompendium/index.php#densities) </span>

----
# Other exciting aspects
* Flexibility comes from ability to write custom functions (which we'll discuss)
  + Essentially nothing is out of the question ("the question is not if, but how") 
* Efficiency
  + Batch processing
  + Loops
* Extensions of R
  + RStudio people
      - Hadley Wickham
      - Yihui Xie
  + *lme4* team
      - Douglas Bates
      - Martin Mächler
      - Ben Bolker
  + Many, many others


--- &twocol
*** =left
## Welcome to R

![plot of chunk welcomFig](assets/fig/welcomFig-1.png)

*** =right
* Moving from point-and-click interfaces to R is a substantial shift 
* It will take time to get used to a code-based interface 
* It will take time to shift the way you think about data 
* Be patient with yourself.

---- &twocol
## Overview of this training
*** =left
### Basic philosophy
* Part art, part science, part technical details
  - Analogy to songwriting: tools vs process
* The only way to **truly** become proficient at the art, is through doing.
  - you learn from me, I learn from you.
  - You'll practice throughout this training (more today than
    tomorrow)
* This course is about jumping into a whole new framework for the processing,
  analysis, and visualization of data. 
* It's meant to be hard. It hopefully will also be rewarding.

*** =right

<div align = "center">
<img src = ../assets/img/artDataScience.png width = 500 height = 600>
</div>

----
## General advice for learning R
* Be stubborn, stick with it (it's worth it)
* Invest the time
* Try to work with it regularly (especially at first)
* Allow yourself to struggle (you're not alone)
* Understand the learning curve (you'll reach plateaus)
* Don't feel bad about writing bad code (you'll get better quickly)

----
## Agenda

# Today
* Basic intro to R (right now)
* Directory management, reading and writing data, data structures
* Intro to data visualizations with base graphics
* Lists, a complete applied example

# Tomorrow
* Intro to R Markdown and dynamic documents
* Data visualizations with *ggplot*
* Functions
* Loops


**Note:** I also have slides on a bunch of "routine" functions, if we can possibly squeeze them in (my guess is not).


---- &twocol
## Overview of this morning

* House cleaning
  + Text editors/R environments
* Very basics of R
  + Object assignment, vectors, matrices, and subsetting 

This morning will be mostly about the nuts and bolts. The afternoon will start with some more fun things (plotting) and end with a complete, applied example (with little bit of nuts and bolts in-between).

<br>

Also, note that I had to make some sacrifices in the content coverage, because time is limited. There's a lot more to R than what I will be able to present in these two days. I'm happy to talk with any of individually (or perhaps collectively) about other topics of interest.

----- &twocol
## Logistics: Enviornment
Find an environment that works for you  

*** =left
![Sublime text](../assets/img/SublimeText.png)

*** =right
![RStudio](../assets/img/RStudio.png)


----
## A note on syntax
* Just like there are rules of writing, there are generally accepted guidelines
  for writing code to make it more readable. For example


```r
matRow <- matrix(c(
           10, 11, 12, 13, 
           20, 21, 22, 23,
           30, 31, 32, 33
          ), 
  nrow = 3, ncol = 4, byrow = TRUE)
```
Is more readable, and easy to understand than


```r
matRow<-matrix(c(10,11,12,13,20,21,22,23,30,31,32,33),nrow=3,ncol=4,byrow=TRUE)
```

----
## The grammar of syntax

* Proper spacing and indentation is *critical* for code to be easily 
  interpretable.
* After you get used to applying the rules, poorly formatted code is like nails
  on a chalkboard
![Takei](../assets/img/Takei.png)

---- &twocol
## Style guide
**Please** review a style guide, and follow those protocols religiously

*** =left

* I recommend starting with Wickham's http://adv-r.had.co.nz/Style.html 
    + It's short (will take < 20 minutes to go through)

* Will make you look better if you ever end up posting on online forums
* Your coding friends will thank you 

*** =right

<div align = "center">
<img src = ../assets/img/WickhamStyle.png width = 600 height = 800>
</div>

-----
## One more qualifier

* The slides I will present will be primarily on functions and operations using
  base R (with the lecture on *ggplot* being the primary exception).
* Many people adhere to the "Hadleyverse", which basically includes using
  packages developed by Hadley Wickham (a *really* smart guy) for basically all
  data manipulations and visualizations.
* My philosophy: Learn base first, then move to his packages if they are
  helpful
    + His packages are primarily just wrappers for base functions, but are
      generally more efficient than the approach you or I would take when
      programming "on the fly"

![hadleyverse](../assets/img/hadleyverse.png)


------
## Onto R
R as a big calculator


```r
3 + 2
```

```
## [1] 5
```


```r
(1/-(3/2)^2) / 2^-1/9
```

```
## [1] -0.09876543
```

------ &twocol

*** =left

# Object Assignment


```r
a <- 3
b <- 2
a + b
```

```
## [1] 5
```

```r
a / (a + b)
```

```
## [1] 0.6
```

*** =right

# Object re-assignment


```r
a <- 3
a
```

```
## [1] 3
```

```r
a <- 7
a
```

```
## [1] 7
```

------ &twocol
## Object Assignment (continued)
*** =left
Objects can be of a variety of types, which we'll talk about 
  much more after the break. But here are just a few


```r
string <- "Hello world!"
logical <- TRUE
double <- 3.2587021
Integer <- 6
```
*** =right
In this case, we can't exactly do arithmetic with all of these. 
  For example


```r
string + double
```

```
## Error in string + double: non-numeric argument to binary operator
```
But, these objects can be extremely useful in programming, as we
  will see.


------
## Playing a trick on a colleague
Object assignment can be helpful to play a trick on somebody (this is one I 
  actually did with a friend from Ohio, who loves the Buckeyes).
  

```r
Ducks <- 2
Buckeyes <- 1
```
Then clear the console, so they can't see the code you've previously written.

------ bg:url(/Users/Daniel/Dropbox/Teaching/CourseR/Weeks/Week1p1/assets/img/fightingduck.jpg)


```r
Ducks > Buckeyes
```

```
## [1] TRUE
```

```r
Ducks < Buckeyes
```

```
## [1] FALSE
```

```r
Buckeyes > Ducks
```

```
## [1] FALSE
```

---- &twocol
## R Environment

*** =left

# R functions
* Anything that carries out an operation in R is a function, even `+`. 
* Functions (outside of infix functions) are preceded by `()`
    + e.g., `sum()`, `lm()`

*** =right

# Getting help
* `?` is your best friend 
    + e.g., `?lm` will tell you all the arguments for the `lm` function
* Google is your other best friend
    + If the documentation from `?` is too confusing (often the case), try 
      google.
* Other good websites
    + http://stackoverflow.com
    + Resource list: 
          - http://www.ats.ucla.edu/stat/r/
    + Mailing lists: 
          - https://stat.ethz.ch/mailman/listinfo/r-help
    

---- &twocol
## R Packages
An R package is a suite of functions generally organized around a common theme.

*** =left

* Examples
    + `stringr`
        - Functions to make working with string variables more 
          simplistic and potentially efficient
    + `lme4`
        - Functions for Linear Mixed Effects Regression modeling 
    +  `ggplot2`
        - Wrapper functions for grid graphics to quickly produce complex 
          plots

*** =right

* As of this writing (06/09/16), there are 8,557 packages available 
  through CRAN (up from 7,239 in early October!).
    + These can all be installed via `install.packages("packageName")`

* Countless other packages on github, personal websites, etc. Often come with 
  installation instructions.
    + My `r2Winsteps` and `sundry` packages

* We will be using packages throughout the training (although most of the 
  training will be focused on base operations)

---- &twocol
## Vectors

# Two global rules for R: 

1. Anything that carries out an operation is a function, even `+`. 
2. Essentially every object in R is stored as a vector or a list (e.g., data
   frames, matrices).

*** =left


```r
is.vector(Ducks)
```

```
## [1] TRUE
```
* The object `Ducks` is a vector, of length one
* So what is a vector?
  - essentially equivalent to the math definition
* <span style="color:blue" > A vector of dimension **n** is an ordered 
  collection of *n* elements, which are called components. </span>
  [math.com](http://www.math.com/tables/oddsends/vectordefs.htm)

*** =right
# Column Vector
$$
\begin{equation*}
 \qquad \begin{bmatrix}
    p_{1} \\\
    p_{2} \\\
    \vdots \\\
    p_{n}
  \end{bmatrix}
\end{equation*}
$$

# Row Vector

$$
\begin{equation*}
 \qquad \begin{bmatrix}
    p_{1} & p_{2} & \ldots & p_{n}
  \end{bmatrix}
\end{equation*}
$$

* Note that a vector of length one is typically referred to as a **scalar**,
  but in R it is still a vector of length 1.

----
## Creating vectors
$$
\begin{equation*}
 \qquad \begin{bmatrix}
    1 & 2 & 3
  \end{bmatrix}
\end{equation*}
$$


```r
numVec <- c(1, 2, 3)
numVec
```

```
## [1] 1 2 3
```

$$
\begin{equation*}
 \qquad \begin{bmatrix}
    A & B & C
  \end{bmatrix}
\end{equation*}
$$


```r
letVec <- c("A", "B", "C")
letVec
```

```
## [1] "A" "B" "C"
```
* `c()` function, which stands for **concatenate** or **combine**. 
* Perhaps the most common function in all of R

---- &twocol
## Matrices
*** =left
* Technically - a vector with a dimension attribute
* Conceptually - vectors of the same length bound together

$$
\begin{equation*}
  \textbf{M} = \qquad 
  \begin{bmatrix}
    p_{11} & p_{12} & \ldots
    & p_{1n} \\
    p_{21} & p_{22} & \ldots
    & p_{2n} \\
    \vdots & \vdots & \ddots
    & \vdots \\
    p_{m1} & p_{m2} & \ldots
    & p_{mn}
  \end{bmatrix}
\end{equation*}
$$


*** =right
* Matrices can be constructed by the conceptual method


```r
v1 <- c(10, 11, 12, 13)
v2 <- c(20, 21, 22, 23)
v3 <- c(30, 31, 32, 33)

mat <- matrix(c(v1, v2, v3), 
	nrow = 3, ncol = 4, byrow = TRUE)
mat
```

```
##      [,1] [,2] [,3] [,4]
## [1,]   10   11   12   13
## [2,]   20   21   22   23
## [3,]   30   31   32   33
```

----
## More on constructing matrices


```r
?matrix
```
![matrixHelp](../assets/img/matrixHelp.png)

---- &twocol
## `byrow` or `bycol`?
*** =left


```r
matRow <- matrix(c(v1, v2, v3), 
	nrow = 3, ncol = 4, byrow = TRUE)
matRow
```

```
##      [,1] [,2] [,3] [,4]
## [1,]   10   11   12   13
## [2,]   20   21   22   23
## [3,]   30   31   32   33
```

```r
matCol <- matrix(c(v1, v2, v3), 
	nrow = 3, ncol = 4, byrow = FALSE)
matCol
```

```
##      [,1] [,2] [,3] [,4]
## [1,]   10   13   22   31
## [2,]   11   20   23   32
## [3,]   12   21   30   33
```
*** =right


```r
v1 <- c(10, 11, 12, 13)
v2 <- c(20, 21, 22, 23)
v3 <- c(30, 31, 32, 33)
```

---- &twocol
## One final note (for now)

*** =left
* Vectors can be entered directly into the matrix function, but they still need
  to be entered as a vector or group of vectors


```r
matRow <- matrix(c(
		c(10, 11, 12, 13), 
		c(20, 21, 22, 23),
		c(30, 31, 32, 33)
		), 
	nrow = 3, ncol = 4, byrow = TRUE)
matRow
```

```
##      [,1] [,2] [,3] [,4]
## [1,]   10   11   12   13
## [2,]   20   21   22   23
## [3,]   30   31   32   33
```
*** =right


```r
matRow <- matrix(c(
                   10, 11, 12, 13, 
				   20, 21, 22, 23,
				   30, 31, 32, 33
					), 
	nrow = 3, ncol = 4, byrow = TRUE)
matRow
```

```
##      [,1] [,2] [,3] [,4]
## [1,]   10   11   12   13
## [2,]   20   21   22   23
## [3,]   30   31   32   33
```
* Note again, the importance of the `byrow` argument

---- &twocol
## Check-in

*** =left

Which snippets of code will produce the matrix below

$$
\begin{equation*}
  \textbf{mat} = \qquad 
  \begin{bmatrix}
    23 & 41 & 18 & 27 \\
    16 & 11 & 72 & 29 \\
    18 & 51 & 32 & 63 \\
  \end{bmatrix}
\end{equation*}
$$

*** =right


```r
A <- matrix(c(
           23, 41, 18, 27, 
           16, 11, 72, 29,
           18, 51, 32, 63), 
  nrow = 3, ncol = 4)

B <- matrix(c(
           c(23, 41, 18, 27), 
           c(16, 11, 72, 29),
           c(18, 51, 32, 63)
           ), 
  nrow = 3, ncol = 4, byrow = TRUE)

C <- matrix(c(
          c(23, 16, 18), 
          c(41, 11, 51),
          c(18, 72, 32),
          c(27, 29, 63)
          ), 
  nrow = 3, ncol = 4)
```

----
## Your turn
Produce the following matrix and vector. 
$$
\begin{equation*}
  \textbf{m} = \qquad 
  \begin{bmatrix}
    67 & 11 & 10 \\
    44 & 22 & 33 \\
    39 & 94 & 85 \\
    49 & 6 & 12 \\
    22 & 86 & 61 \\
  \end{bmatrix}
\end{equation*}
$$

$$
\begin{equation*}
  \textbf{v} = \qquad 
  \begin{bmatrix}
    11 & 22 & 33 & 44 & 55 \\
  \end{bmatrix}
\end{equation*}
$$

<br>
Try adding them together. What do you get?

<span style="color:gray" > (You can work with a partner) </span>


----

```r
c1 <- c(67, 44, 39, 49, 22)
c2 <- c(11, 22, 94, 6, 86)
c3 <- c(10, 33, 85, 12, 61)

m <- matrix(c(c1, c2, c3), ncol = 3)
v <- c(11, 22, 33, 44, 55)

v + m
```

```
##      [,1] [,2] [,3]
## [1,]   78   22   21
## [2,]   66   44   55
## [3,]   72  127  118
## [4,]   93   50   56
## [5,]   77  141  116
```

---- .segue
# Subsetting Vectors and Matrices

---- &twocol
## Subsetting vectors
*** =left


```r
v1 <- c(11, 12, 13, 14, 15,
	    16, 17, 18, 19, 20)
```
* Indexing
  - select the fifth element 


```r
v1[5]
```

```
## [1] 15
```
* Exclude the fifth element


```r
v1[-5]
```

```
## [1] 11 12 13 14 16 17 18 19 20
```

*** =right
* select the 7th - 10th elements


```r
sevenToTen <- 7:10
sevenToTen
```

```
## [1]  7  8  9 10
```

```r
v1[sevenToTen]
```

```
## [1] 17 18 19 20
```

```r
v1[7:10]
```

```
## [1] 17 18 19 20
```

---- 
## Subsetting vectors (continued)


```r
v1 <- c(11, 12, 13, 14, 15, 16, 17, 18, 19, 20)
```
* Logical
  - select elements greater than 13


```r
gt13 <- v1 > 13
gt13
```

```
##  [1] FALSE FALSE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
```

```r
v1[gt13]
```

```
## [1] 14 15 16 17 18 19 20
```

---- &twocol
## Subsetting vectors (continued)


```r
v1 <- c(11, 12, 13, 14, 15, 16, 17, 18, 19, 20)
```
*** =left
* Logical
  - select odd elements


```r
v1 %% 2 # modulo operator
```

```
##  [1] 1 0 1 0 1 0 1 0 1 0
```

```r
oddDummy <- v1 %% 2
oddDummy > 0
```

```
##  [1]  TRUE FALSE  TRUE FALSE  TRUE FALSE  TRUE FALSE  TRUE FALSE
```
Actually could coerce directly to logical (but we haven't talked about coercions yet, and this works just as well)

*** =right


```r
v1[oddDummy > 0]
```

```
## [1] 11 13 15 17 19
```

---- &twocol
## Negation


```r
v1 <- c(11, 12, 13, 14, 15, 16, 17, 18, 19, 20)
```

*** =left

Remove the third through fifth elements


```r
v1[-3:-5]
```

```
## [1] 11 12 16 17 18 19 20
```
Note that you must have the negative on each side, to create the appropriate sequence. For example, the following fails


```r
v1[-3:5]
```

```
## Error in v1[-3:5]: only 0's may be mixed with negative subscripts
```

*** =right

Remove the third, fifth, and tenth elements


```r
v1[c(-3, -5, -10)]
```

```
## [1] 11 12 14 16 17 18 19
```

```r
v1[-c(3, 5, 10)]
```

```
## [1] 11 12 14 16 17 18 19
```

----
## Your turn

* Create the following vector

$$
\begin{equation*}
  \textbf{v} = \qquad 
  \begin{bmatrix}
    18 & 16 & 13 & 35 & 2 & 17 & 92 & 4 \\
  \end{bmatrix}
\end{equation*}
$$

Subset the vector by:
* Selecting the first 3 values
* Removing the last two values (somewhat tricky)
* Keeping all values greater than 15

----

```r
v <- c(18, 16, 13, 35, 2, 17, 92, 4)
```
Selecting the first 3 values


```r
v[1:3]
```

```
## [1] 18 16 13
```

Removing the last two values


```r
v[-c(7:8)]
v[-7:-8]
```

```
## [1] 18 16 13 35  2 17
```

Values greater than 15


```r
v[v > 15]
```

```
## [1] 18 16 35 17 92
```

---- &twocol
## Subsetting Matrices

*** =left


* indexing
  - Matrices can be subset by using `[]` with the same conventions as 
    mathematical matrices, i.e., `[row , column]`.

    *** 

$$
\begin{equation*}
  \textbf{mat} = \qquad 
  \begin{bmatrix}
    10 & 11 & 12 & 13 \\
    20 & 21 & 22 & 23 \\
    30 & 31 & 32 & 33 \\
  \end{bmatrix}
\end{equation*}
$$


*** =right

* Select the third element of the second column


```r
mat[3,2]
```

```
## [1] 31
```

* Select the second element of the fourth column


```r
mat[2,4]
```

```
## [1] 23
```

---- &twocol
## Subsetting Matrices (continued)
*** =left
#### Select an entire row: Leave the column indicator blank

* Select the entire second row


```r
mat[2, ]
```

```
## [1] 20 21 22 23
```
$$
\begin{equation*}
  \textbf{mat} = \qquad 
  \begin{bmatrix}
    10 & 11 & 12 & 13 \\
    20 & 21 & 22 & 23 \\
    30 & 31 & 32 & 33 \\
  \end{bmatrix}
\end{equation*}
$$

*** =right
#### Select an entire column: Leave the row indicator blank

* Select the entire third column


```r
mat[ ,3]
```

```
## [1] 12 22 32
```

---- &twocol
## Subsetting Matrices (continued)
*** =left
* The return from subsetting a matrix is a vector, which can also be
  subset.


```r
column3 <- mat[ ,3]
column3
```

```
## [1] 12 22 32
```
* select the second element of the new vector


```r
column3[2]
```

```
## [1] 22
```
*** =right

* Alternatively


```r
mat[ ,3][2]
```

```
## [1] 22
```
... which is the same as


```r
mat[2,3]
```

```
## [1] 22
```

$$
\begin{equation*}
  \textbf{mat} = \qquad 
  \begin{bmatrix}
    10 & 11 & 12 & 13 \\
    20 & 21 & 22 & 23 \\
    30 & 31 & 32 & 33 \\
  \end{bmatrix}
\end{equation*}
$$


----
## Additional arguments

* You can avoid data being reduced to vectors by using the options `drop = FALSE`
  argument


```r
mat[ ,2, drop = FALSE]
```

```
##      [,1]
## [1,]   11
## [2,]   21
## [3,]   31
```

* Use a vector to select multiple rows/columns


```r
col1_3 <- c(1,3)
mat[ ,col1_3]
```

```
##      [,1] [,2]
## [1,]   10   12
## [2,]   20   22
## [3,]   30   32
```

---- &twocol
## Subsetting Matrices (continued)
### Logical

*** =left


```r
log1 <- mat > 13 & mat < 23
log1
```

```
##       [,1]  [,2]  [,3]  [,4]
## [1,] FALSE FALSE FALSE FALSE
## [2,]  TRUE  TRUE  TRUE FALSE
## [3,] FALSE FALSE FALSE FALSE
```

```r
mat[log1]
```

```
## [1] 20 21 22
```
$$
\begin{equation*}
  \textbf{mat} = \qquad 
  \begin{bmatrix}
    10 & 11 & 12 & 13 \\
    20 & 21 & 22 & 23 \\
    30 & 31 & 32 & 33 \\
  \end{bmatrix}
\end{equation*}
$$

*** =right


```r
log2 <- (mat > 13 & mat < 23) | 
	 	(mat > 30 & mat < 33)
log2
```

```
##       [,1]  [,2]  [,3]  [,4]
## [1,] FALSE FALSE FALSE FALSE
## [2,]  TRUE  TRUE  TRUE FALSE
## [3,] FALSE  TRUE  TRUE FALSE
```

```r
mat[log2]
```

```
## [1] 20 21 31 22 32
```
Note the odd order, because the subsetting is occuring by column, rather than
  row.


----
## Brief practice
# We'll go directly to break from here, and review the answers when you get back at 10:45

<br>

Create the following matrix:

$$
\begin{equation*}
  \textbf{m} = \qquad 
  \begin{bmatrix}
    18 & 32 & 11 & 41 & 73 \\
    61 & 47 & 22 & 87 & 63 \\
    44 & 52 & 23 & 42 & 77 \\
    23 & 17 & 5 & 72 & 83 \\
  \end{bmatrix}
\end{equation*}
$$

Subset the matrix by:

* Selecting the third column
* Excluding the second column
* Selecting the third and fifth elements from the second row (somewhat tricky)
* Selecting values greater than 25
* Create a vector that is the sum of the first and fourth rows

----

```r
m <- matrix(c(
    18, 32, 11, 41, 73,
    61, 47, 22, 87, 63,
    44, 52, 23, 42, 77,
    23, 17, 5, 72, 83
    ), 
  byrow = TRUE, ncol = 5
)
```
Select the third column


```r
m[ ,3]
```

```
## [1] 11 22 23  5
```

Exclude the second column


```r
m[ ,-2]
```

```
##      [,1] [,2] [,3] [,4]
## [1,]   18   11   41   73
## [2,]   61   22   87   63
## [3,]   44   23   42   77
## [4,]   23    5   72   83
```

----

Select third and fifth elements from the second row


```r
m[2,c(3,5)]
```

```
## [1] 22 63
```

Select values greater than 25


```r
m[m > 25]
```

```
##  [1] 61 44 32 47 52 41 87 42 72 73 63 77 83
```

Create a vector that is the sum of the first and fourth rows


```r
m[1, ] + m[4, ]
```

```
## [1]  41  49  16 113 156
```
