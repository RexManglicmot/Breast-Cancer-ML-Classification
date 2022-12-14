Breast Cancer ML Classifcation Linear Discriminant Analysis
================
Rex Manglicmot

-   <a href="#status-continuing-working-document"
    id="toc-status-continuing-working-document">Status: Continuing Working
    Document</a>
-   <a href="#introduction" id="toc-introduction">Introduction</a>
-   <a href="#loading-the-libraries" id="toc-loading-the-libraries">Loading
    the Libraries</a>
-   <a href="#loading-the-data" id="toc-loading-the-data">Loading the
    Data</a>
-   <a href="#cleaning-the-data" id="toc-cleaning-the-data">Cleaning the
    Data</a>
-   <a href="#exploratory-data-analysis"
    id="toc-exploratory-data-analysis">Exploratory Data Analysis</a>
-   <a href="#modeling-linear-discriminant-analysis"
    id="toc-modeling-linear-discriminant-analysis">Modeling: Linear
    Discriminant Analysis</a>
-   <a href="#limitations" id="toc-limitations">Limitations</a>
-   <a href="#conclusion" id="toc-conclusion">Conclusion</a>
-   <a href="#inspiration-for-this-project"
    id="toc-inspiration-for-this-project">Inspiration for this project</a>

## Status: Continuing Working Document

Hi everyone. I’m continuing building my data analysis and R skills. As
such, I would love feedback to better improve this project via
<rexmanglicmot@gmail.com>. Any mistakes and misrepresentation of the
data are my own.

Things Need To Do/Questions:

-   More concepts about LDA + include mathematical expressions and the
    verbal walkthrough of such.
-   Grammar.
-   Get feedback and incorporate
-   Fill in intro

## Introduction

There are many factors that attribute to formation cancer, but there is
one dominant factor among all cancers, and that is gene expression.
There are numerous studies that have shown that having a certain gene
may likely contribute to a formation of a certain cancer. The human
genome is estimated to have about 20,000 genes.[^1] These genes then go
through mechanisms of protein synthesis which in the end create a vast
array of proteins (estimated to be 20,000 or even more[^2]) and these
proteins then have the capability to form cells (and eventually cancer).

Studying genes and their expressions provide scientist the opportunity
to idneitfy which patients are susceptible to certain cancers.

The project is structured in the following chapters:

1.  Introduction
2.  Loading the Libraries
3.  Loading the Data
4.  Cleaning the Data
5.  Exploratory Data Analysis
6.  Modelling: Linear Discriminant Analysis
7.  Limitations
8.  Conclusion
9.  Inspiration for this project

A special acknowledgement to the University of Irvine Data Repository
for providing the dataset to the public.[^3] A special acknowledgement
for Samuele Fiorini from University of Genoa for the original
dataset.[^4]

The dataset contains 20,531 genes and unfortunately the name of the
genes could not be identified (still in the processing of contacting
dataset owner). There are 801 observations and each observation is
classified as having one of 5 types of cancers.

## Loading the Libraries

``` r
# Load the libraries
library(tidyverse)
library(dplyr)
```

## Loading the Data

``` r
#load the dataset
#data <- read.csv('data.csv')
#data_labels <- read.csv('labels.csv')

#view the first few rows of the data
#head(data, 10)
#head(data_labels, 10)

#look at the number of the rows and columns we have
#dim(data)
```

the data dataset with \>20K columns abd the data_label has the
classification of the patient.

## Cleaning the Data

First, we need to do is combine the datasets by using an join function
by using the X variable and store the new data set into an new object,
data2.

``` r
#left-join on a single coumn, the X variable
#data2 <- merge (x=data, y= data_labels,
                #by='X', all.x=TRUE)

#check if the joined worked
#ncol(data)
#which(colnames(data2)=='Class')
```

We see that data we have a total of 20532 and in data2 we 20533, we can
assume that we added the Class column. But just to make sure, we called
the which function that allowed to us locate the Class column, which was
30532. We have successfully added the column.

Now for more data cleaning, we have quite a few genes, how about we see
and get rid of genes that are not present in any of the 801
observations.

``` r
#stored all columns that had all zeros 
#Note. IT was working before butit was not working now. 
#Had to include dyplyr library for it to work 
#data3 <- data2 %>%
  #select(where(~ all(. ==0)))
```

``` r
#create a new object with columns with numeric value
#data4 <- data2 %>%
  #select(where(~ any(. !=0)))
```

## Exploratory Data Analysis

## Modeling: Linear Discriminant Analysis

![](https://repository-images.githubusercontent.com/13402862/b8473680-4379-11ea-8d72-e87a518def4b)

**Linear Discriminant Analysis** is a dimensional reduction technique
used to separate two or more classes.[^5] The goal is to **project the
data onto a lower-dimensional space** that has decent class
separability.[^6]

LDA is a type of dimensional reduction technique that reduces the number
of dimensions in the dataset.[^7] The objective is to reduce a high
dimensional dataset to a lower dimensional space and to have separation
between classes (therefore, our classification)[^8] Recall that
Multidimensional data has many features (i.e. variables) that be are
correlated to one another and dimensional reduction reduces this to 2 or
3 dimensions.[^9]

I decided to pput this in another object for closer inspection and saw
that 267 variables out of the 20531 variables had zero values. Now let’s
get rid of this of these columns and create a new object, data4, that
contains all non-zero, numeric values.

Below are the Steps to do an LDA[^10]:

1.  Compute Mean vectors of each class of dependent variables

2.  Compute with-in class and between-class scatter matrices

3.  Compute Eigenvalues and Eigenvector for SW and SB

4.  Sort the Eigenvalues in discending order and select the top k

5.  Create a new matrix containing eignevectors that map the k
    eigenvalues

6.  Contain the new features (linear discriminants) by taking the dot
    plot of the data and the matrix.

![](https://media.geeksforgeeks.org/wp-content/uploads/20190423132508/1dlda.jpg)

## Limitations

## Conclusion

## Inspiration for this project

[^1]: <https://sitn.hms.harvard.edu/flash/2012/issue127a/>

[^2]: <https://theconversation.com/what-is-a-protein-a-biologist-explains-152870#>:\~:text=Scientists%20are%20not%20exactly%20sure,causing%20your%20muscles%20to%20work.

[^3]: <https://archive.ics.uci.edu/ml/datasets/gene+expression+cancer+RNA-Seq>

[^4]: Samuele Fiorini, samuele.fiorini ‘@’ dibris.unige.it, University
    of Genoa

[^5]: <https://www.geeksforgeeks.org/ml-linear-discriminant-analysis/#>:\~:text=Linear%20Discriminant%20Analysis%20or%20Normal,separating%20two%20or%20more%20classes.

[^6]: <https://sebastianraschka.com/Articles/2014_python_lda.html>

[^7]: <https://www.mygreatlearning.com/blog/linear-discriminant-analysis-or-lda/>

[^8]: <https://www.digitalvidya.com/blog/linear-discriminant-analysis/>

[^9]: <https://www.digitalvidya.com/blog/linear-discriminant-analysis/>

[^10]: <https://www.mygreatlearning.com/blog/linear-discriminant-analysis-or-lda/>
