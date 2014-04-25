## These instructions can only be followed after those from "Organizing Data" have been successfully completed
##Now that we have cleaner data set all in one file

###Reads compiled data set from "Organizing Data" markdown file into R
totalData <- read.csv("CompiledSamsungData.csv")

###Reads complete list of 2947 subject IDs and activity combos in test set
testSubject <- readLines("./test/subject_test.txt")
testActivity <- readLines("./test/y_test.txt")
###Reads complete list of 7352 subject IDs and activity combos in training set
trainSubject <- readLines("./train/subject_train.txt")
trainActivity <- readLines("./train/y_train.txt")
###binds subject and activity columns into one data table for test set
testTable <- cbind(testSubject, testActivity)
###binds subject and activity columns into one data table for training set
trainTable <- cbind(trainSubject, trainActivity)
###merges test set and training set into two subject/activity columns for all 10299 observations
mergedData <- rbind(testTable, trainTable)

###adds subject/activity columns to total data file, replacing unnecessary first two columns. Orders data table by subject number in increasing order
tidyData <- cbind(mergedData, totalData[,3:81])
tidyData <- tidyData[order(as.numeric(as.character(tidyData$testSubject))),]

###reads activity code book from original data file, names subject and activity columns appropriately 
activities <- readLines("./activity_labels.txt")
colnames(tidyData)[1] <- "Subject"
colnames(tidyData)[2] <- "Activity"

###Renames all numbers in Activity column with activity corresponding to that number from activity code book
tidyData[[2]] <- gsub("1", "Walking", tidyData[[2]])
tidyData[[2]] <- gsub("2", "Walking Upstairs", tidyData[[2]])
tidyData[[2]] <- gsub("3", "Walking Downstairs", tidyData[[2]])
tidyData[[2]] <- gsub("4", "Sitting", tidyData[[2]])
tidyData[[2]] <- gsub("5", "Standing", tidyData[[2]])
tidyData[[2]] <- gsub("6", "Laying", tidyData[[2]])
  
###This loop finds names of the 79 selected activities
selectedFeatures = c()

for (i in MeanSTD)
{
  features[i]
  selectedFeatures <- c(selectedFeatures, features[i])
}
selectedFeatures

###This loops renames each column with coded name
for (i in 1:79)
{
  colnames(tidyData)[i+2] <- selectedFeatures[i]                 
}
