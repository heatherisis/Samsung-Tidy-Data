This OrganizingData markdown file is intended to be the first in a series of four manuscripts describing the process for data cleanup. 

* 1. OrganizingData
* 2. CompilingData
* 3. TrimmingData
* 4. ReshapingData


####We assume that the zip file from the following URL has been downloaded and extracted to a local directory. Downloads project file and set downloaded "UCI HAR Dataset" file as working directory

download.file("https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip"
              ,destfile="./samsungData.zip",method="curl")

setwd("/Users/heatherisis/Desktop/Getting and Cleaning Data/UCI HAR Dataset")


####Clean up large data files, read lines from separate .csv files, including data for 561 variables of all 30 subjects divided into training set (7352 observations) and test set (2947 observations)
testValue <- readLines("./test/X_test.txt")
trainValue <- readLines("./train/X_train.txt")

####Combine test set and training set into one data file
AllValues <- c(testValue,trainValue)

####Reads coded list of all 561 variable names and extracts all variable names with "mean" (46) or "std" (33) in title, then creates an ordered vector of all 79 variables mean/std in name
features <- readLines("./features.txt")
meanVector <- grep("mean()", features)
stdVector <- grep("std()", features)
MeanSTD <- sort(c(meanVector, stdVector))

####When running loop of all 10299 observations, computer could not process all at once, so divided into groups of 1000 observations. Within each loop, outer loop finds all variables for particular subject in data set, separates list of variables into parts, converts to vector, and removes empty elements in vector leaving 561 variables. Inner loop selects 79 mean/std variables from each complete list of variables. With shortened list, writes .csv file for 79 variables. 

####First 1000 observations only:  

myList <- list()

for (i in 1:1000)
{
  one <- AllValues[i]                  
  result <- unlist(as.vector(strsplit(one, " ")))    
  result2 <- result[result != ""]    
  complete = c()        
  for (i in MeanSTD)
  {
    result2[i]
    complete<-c(complete,result2[i])
  }
  myList <- rbind(myList, complete)    
  write.csv(myList, "tidySamsungData1000.csv")  
}

####1001-2000 observations only:  

myList <- list()

for (i in 1001:2000)
{
  one <- AllValues[i]
  result <- unlist(as.vector(strsplit(one, " ")))
  result2 <- result[result != ""]
  complete = c()
  for (i in MeanSTD)
  {
    result2[i]
    complete<-c(complete,result2[i])
  }
  myList <- rbind(myList, complete)
  write.csv(myList, "tidySamsungData2000.csv")
}

####2001-3000 observations only: 

myList <- list()

for (i in 2001:3000)
{
  one <- AllValues[i]
  result <- unlist(as.vector(strsplit(one, " ")))
  result2 <- result[result != ""]
  complete = c()
  for (i in MeanSTD)
  {
    result2[i]
    complete<-c(complete,result2[i])
  }
  myList <- rbind(myList, complete)
  write.csv(myList, "tidySamsungData3000.csv")  
}

####3001-4000 observations only: 

myList <- list()

for (i in 3001:4000)
{
  one <- AllValues[i]
  result <- unlist(as.vector(strsplit(one, " ")))
  result2 <- result[result != ""]
  complete = c()
  for (i in MeanSTD)
  {
    result2[i]
    complete<-c(complete,result2[i])
  }
  myList <- rbind(myList, complete)
  write.csv(myList, "tidySamsungData4000.csv")  
}

####4001-5000 observations only: 

myList <- list()

for (i in 4001:5000)
{
  one <- AllValues[i]
  result <- unlist(as.vector(strsplit(one, " ")))
  result2 <- result[result != ""]
  complete = c()
  for (i in MeanSTD)
  {
    result2[i]
    complete<-c(complete,result2[i])
  }
  myList <- rbind(myList, complete)
  write.csv(myList, "tidySamsungData5000.csv")  
}

####5001-6000 observations only: 

myList <- list()

for (i in 5001:6000)
{
  one <- AllValues[i]
  result <- unlist(as.vector(strsplit(one, " ")))
  result2 <- result[result != ""]
  complete = c()
  for (i in MeanSTD)
  {
    result2[i]
    complete<-c(complete,result2[i])
  }
  myList <- rbind(myList, complete)
  write.csv(myList, "tidySamsungData6000.csv")  
}

####6001-7000 observations only: 

myList <- list()

for (i in 6001:7000)
{
  one <- AllValues[i]
  result <- unlist(as.vector(strsplit(one, " ")))
  result2 <- result[result != ""]
  complete = c()
  for (i in MeanSTD)
  {
    result2[i]
    complete<-c(complete,result2[i])
  }
  myList <- rbind(myList, complete)
  write.csv(myList, "tidySamsungData7000.csv")
}

####7001-8000 observations only: 
myList <- list()

for (i in 7001:8000)
{
  one <- AllValues[i]
  result <- unlist(as.vector(strsplit(one, " ")))
  result2 <- result[result != ""]  
  complete = c()
  for (i in MeanSTD)
  {
    result2[i]
    complete<-c(complete,result2[i])
  }
  myList <- rbind(myList, complete)
  write.csv(myList, "tidySamsungData8000.csv")
}

####8001-9000 observations only: 

myList <- list()

for (i in 8001:9000)
{
  one <- AllValues[i]
  result <- unlist(as.vector(strsplit(one, " ")))
  result2 <- result[result != ""]
  complete = c()
  for (i in MeanSTD)
  {
    result2[i]
    complete<-c(complete,result2[i])
  }
  myList <- rbind(myList, complete)
  write.csv(myList, "tidySamsungData9000.csv")  
}

####9001-10000 observations only: 

myList <- list()

for (i in 9001:10000)
{
  one <- AllValues[i]
  result <- unlist(as.vector(strsplit(one, " ")))
  result2 <- result[result != ""]  
  complete = c()
  for (i in MeanSTD)
  {
    result2[i]
    complete<-c(complete,result2[i])
  }
  options(digits=1)
  myList <- rbind(myList, complete)
  write.csv(myList, "tidySamsungData10000.csv")
}

####10001-10299 observations only: 

myList <- list()

for (i in 10001:10299)
{
  one <- AllValues[i]
  result <- unlist(as.vector(strsplit(one, " ")))
  result2 <- result[result != ""]
  complete = c()
  for (i in MeanSTD)
  {
    result2[i]
    complete<-c(complete,result2[i])
  }
  myList <- rbind(myList, complete)
  write.csv(myList, "tidySamsungData10299.csv")  
}

####Reads new files of 1000 observations each into R
myList1000 <- read.csv("tidySamsungData1000.csv")
myList2000 <- read.csv("tidySamsungData2000.csv")
myList3000 <- read.csv("tidySamsungData3000.csv")
myList4000 <- read.csv("tidySamsungData4000.csv")
myList5000 <- read.csv("tidySamsungData5000.csv")
myList6000 <- read.csv("tidySamsungData6000.csv")
myList7000 <- read.csv("tidySamsungData7000.csv")
myList8000 <- read.csv("tidySamsungData8000.csv")
myList9000 <- read.csv("tidySamsungData9000.csv")
myList10000 <- read.csv("tidySamsungData10000.csv")
myList10299 <- read.csv("tidySamsungData10299.csv")

####Then binds rows into complete list of 10299 observations with 79 variables
totalList <- rbind(myList1000, myList2000, myList3000, myList4000, myList5000,
                   myList6000, myList7000, myList8000, myList9000, myList10000,
                   myList10299)

####Writes compiled and cleaner data set, not yet tidy
write.csv(totalList, "CompiledSamsungData.csv")
