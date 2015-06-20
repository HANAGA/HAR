#Human Activity Recognition : Prediction Assignment Writeup


![](images/on-body-sensing-schema.png) Human Activity Recognition **HAR** has emerged as a key research area in the last years and is gaining increasing attention by the pervasive computing research community. Using devices such as Jawbone Up, Nike FuelBand, and Fitbit it is now possible to collect a large amount of data about personal activity relatively inexpensively.  

Six young health participants were asked to perform one set of 10 repetitions of the Unilateral Dumbbell Biceps Curl in five different fashions: exactly according to the specification (Class A), throwing the elbows to the front (Class B), lifting the dumbbell only halfway (Class C), lowering the dumbbell only halfway (Class D) and throwing the hips to the front (Class E).

Class A corresponds to the specified execution of the exercise, while the other 4 classes correspond to common mistakes. Participants were supervised by an experienced weight lifter to make sure the execution complied to the manner they were supposed to simulate. The exercises were performed by six male participants aged between 20-28 years, with little weight lifting experience. We made sure that all participants could easily simulate the mistakes in a safe and controlled manner by using a relatively light dumbbell (1.25kg).

This human activity recognition research has traditionally focused on discriminating between different activities, i.e. to predict "how (well)" an activity was performed by the wearer.

## Data Loading and Cleaning
```R

path="D:/CoursEra2014/Data Science/Course08 Machine Learning/Week5 Project 1"
setwd(path)
pml.test <- read.csv("pml-testing.csv",header=T)
pml.train <- read.csv("pml-training.csv",header=T)

#removing unnecessary 1st column
pml.train <- pml.train[,-1]

# function to verify whether a column contains NA value or not
notNAcolumn <- function(x){ !any(is.na(x)) }


# applying above function on every column of train data and to get list of columns with status
cols.status <- apply(pml.train,2,notNAcolumn)
# extracting all columns which do not contain NA values

dim(pml.train)
pml.train <- pml.train[, cols.status]

dim(pml.train)





```