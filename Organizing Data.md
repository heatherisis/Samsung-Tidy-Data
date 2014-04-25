We assume that the zip file from the following URL has been downloard and extracted to a local directory. 

#downloads project file and set downloaded "UCI HAR Dataset" file as working directory
download.file("https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip"
              ,destfile="./samsungData.zip",method="curl")

setwd("/Users/heatherisis/Desktop/Getting and Cleaning Data/UCI HAR Dataset")


#clean up large data files

#Read lines from separate .csv files, including data for 561 variables of all 30 subjects divided
#into training set (7352 observations) and test set (2947 observations)
testValue <- readLines("./test/X_test.txt")
trainValue <- readLines("./train/X_train.txt")
#combnine test set and training set into one data file
AllValues <- c(testValue,trainValue)

#reads coded list of all 561 variable names and extracts all variable names with "mean" (46) or "std" (33)
#in title, then creates an ordered vector of all 79 variables mean/std in name
features <- readLines("./features.txt")
meanVector <- grep("mean()", features)
stdVector <- grep("std()", features)
MeanSTD <- sort(c(meanVector, stdVector))


#Each row is a vector of feature variables corresponding to a unique combination of subject and activity, 
#computer could not process all 10299, so divided into groups of 1000 observations

#Outer loop finds all variables for particular subject in data set, separates list of variables into parts, 
#converts to vector, and removes empty elements in vector leaving 561 variables. Inner loop selects 79 
#mean/std variables from each complete list of variables. With shortened list, writes csv for 79 vars
# first 1000 observations only
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

#Outer loop finds all variables for particular subject in data set, separates list of variables into parts,
#converts to vector, and removes empty elements in vector leaving 561 variables. Inner loop selects 79 
#mean/std variables from each complete list of variables. With shortened list, writes csv for 79 vars
#1001-2000 observations only

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

#Outer loop finds all variables for particular subject in data set, separates list of variables into parts,
#converts to vector, and removes empty elements in vector leaving 561 variables. Inner loop selects 79 
#mean/std variables from each complete list of variables. With shortened list, writes csv for 79 vars
# 2001-3000 observations only
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

#Outer loop finds all variables for particular subject in data set, separates list of variables into parts,
#converts to vector, and removes empty elements in vector leaving 561 variables. Inner loop selects 79 
#mean/std variables from each complete list of variables. With shortened list, writes csv for 79 vars
# 3001-4000 observations only
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

#Outer loop finds all variables for particular subject in data set, separates list of variables into parts,
#converts to vector, and removes empty elements in vector leaving 561 variables. Inner loop selects 79 
#mean/std variables from each complete list of variables. With shortened list, writes csv for 79 vars
# 4001-5000 observations only
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

#Outer loop finds all variables for particular subject in data set, separates list of variables into parts,
#converts to vector, and removes empty elements in vector leaving 561 variables. Inner loop selects 79 
#mean/std variables from each complete list of variables. With shortened list, writes csv for 79 vars
# 5001-6000 observations only
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

#Outer loop finds all variables for particular subject in data set, separates list of variables into parts,
#converts to vector, and removes empty elements in vector leaving 561 variables. Inner loop selects 79 
#mean/std variables from each complete list of variables. With shortened list, writes csv for 79 vars
# 6001-7000 observations only
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

#Outer loop finds all variables for particular subject in data set, separates list of variables into parts,
#converts to vector, and removes empty elements in vector leaving 561 variables. Inner loop selects 79 
#mean/std variables from each complete list of variables. With shortened list, writes csv for 79 vars
# 7001-8000 observations only
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

#Outer loop finds all variables for particular subject in data set, separates list of variables into parts,
#converts to vector, and removes empty elements in vector leaving 561 variables. Inner loop selects 79 
#mean/std variables from each complete list of variables. With shortened list, writes csv for 79 vars
# 8001-9000 observations only
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

myList <- list()

#Outer loop finds all variables for particular subject in data set, separates list of variables into parts,
#converts to vector, and removes empty elements in vector leaving 561 variables. Inner loop selects 79 
#mean/std variables from each complete list of variables. With shortened list, writes csv for 79 vars
# 9001-10000 observations only
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

#Outer loop finds all variables for particular subject in data set, separates list of variables into parts,
#converts to vector, and removes empty elements in vector leaving 561 variables. Inner loop selects 79 
#mean/std variables from each complete list of variables. With shortened list, writes csv for 79 vars
# 10001-10299 observations only
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
