Getting and Cleaning Samsung Data
=================

# Coursera Course Project


#Reads new files of 1000 observations each into R
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

#then binds rows into complete list of 10299 observations with 79 variables
totalList <- rbind(myList1000, myList2000, myList3000, myList4000, myList5000,
                   myList6000, myList7000, myList8000, myList9000, myList10000,
                   myList10299)

#Writes compiled and cleaner data set, not yet tidy, reads data table back into R
write.csv(totalList, "CompiledSamsungData.csv")
totalData <- read.csv("CompiledSamsungData.csv")

##### now that we have cleaner data set all in one file

#Reads complete list of 2947 subject IDs and activity combos in test set
testSubject <- readLines("./test/subject_test.txt")
testActivity <- readLines("./test/y_test.txt")
#Reads complete list of 7352 subject IDs and activity combos in training set
trainSubject <- readLines("./train/subject_train.txt")
trainActivity <- readLines("./train/y_train.txt")
#binds subject and activity columns into one data table for test set
testTable <- cbind(testSubject, testActivity)
#binds subject and activity columns into one data table for training set
trainTable <- cbind(trainSubject, trainActivity)
#merges test set and training set into two subject/activity columns for all 10299 observations
mergedData <- rbind(testTable, trainTable)

#adds subject/activity columns to total data file, replacing unnecessary first two columns. Orders data
# table by subject number in increasing order
tidyData <- cbind(mergedData, totalData[,3:81])
tidyData <- tidyData[order(as.numeric(as.character(tidyData$testSubject))),]

#reads activity code book from original data file, names subject and activity columns appropriately 
activities <- readLines("./activity_labels.txt")
colnames(tidyData)[1] <- "Subject"
colnames(tidyData)[2] <- "Activity"

#Renames all numbers in Activity column with activity corresponding to that number from activity code book
tidyData[[2]] <- gsub("1", "Walking", tidyData[[2]])
tidyData[[2]] <- gsub("2", "Walking Upstairs", tidyData[[2]])
tidyData[[2]] <- gsub("3", "Walking Downstairs", tidyData[[2]])
tidyData[[2]] <- gsub("4", "Sitting", tidyData[[2]])
tidyData[[2]] <- gsub("5", "Standing", tidyData[[2]])
tidyData[[2]] <- gsub("6", "Laying", tidyData[[2]])
  
#This loop finds names of the 79 selected activities
selectedFeatures = c()

for (i in MeanSTD)
{
  features[i]
  selectedFeatures <- c(selectedFeatures, features[i])
}
selectedFeatures

#This loops renames each column with coded name
for (i in 1:79)
{
  colnames(tidyData)[i+2] <- selectedFeatures[i]                 
}

#Of 79 selected variables, those with meanFreq calculations omitted, as derived from original measurements
tidyData <- subset(tidyData, select = -c(49:51,58:60,67:69,72,75,78,81))
#eliminate non-measurement vars, including jerk signals and magnitude, as derived from original 
#measurement mean/std
tidyData <- subset(tidyData, select = -c(15:20,27:42,49:54,61:68))

#Rename all column names with meaningul titles without code
colnames(tidyData)[3] <- "Time Body Accelerometer X Mean"
colnames(tidyData)[4] <- "Time Body Accelerometer Y Mean"
colnames(tidyData)[5] <- "Time Body Accelerometer Z Mean"
colnames(tidyData)[6] <- "Time Body Accelerometer X Standard Deviation"
colnames(tidyData)[7] <- "Time Body Accelerometer Y Standard Deviation"
colnames(tidyData)[8] <- "Time Body Accelerometer Z Standard Deviation"

colnames(tidyData)[9] <- "Time Gravity Accelerometer X Mean"
colnames(tidyData)[10] <- "Time Gravity Accelerometer Y Mean"
colnames(tidyData)[11] <- "Time Gravity Accelerometer Z Mean"
colnames(tidyData)[12] <- "Time Gravity Accelerometer X Standard Deviation"
colnames(tidyData)[13] <- "Time Gravity Accelerometer Y Standard Deviation"
colnames(tidyData)[14] <- "Time Gravity Accelerometer Z Standard Deviation"

colnames(tidyData)[15] <- "Time Body Gyroscope X Mean"
colnames(tidyData)[16] <- "Time Body Gyroscope Y Mean"
colnames(tidyData)[17] <- "Time Body Gyroscope Z Mean"
colnames(tidyData)[18] <- "Time Body Gyroscope X Standard Deviation"
colnames(tidyData)[19] <- "Time Body Gyroscope Y Standard Deviation"
colnames(tidyData)[20] <- "Time Body Gyroscope Z Standard Deviation"

colnames(tidyData)[21] <- "Frequency Body Accelerometer X Mean"
colnames(tidyData)[22] <- "Frequency Body Accelerometer Y Mean"
colnames(tidyData)[23] <- "Frequency Body Accelerometer Z Mean"
colnames(tidyData)[24] <- "Frequency Body Accelerometer X Standard Deviation"
colnames(tidyData)[25] <- "Frequency Body Accelerometer Y Standard Deviation"
colnames(tidyData)[26] <- "Frequency Body Accelerometer Z Standard Deviation"

colnames(tidyData)[27] <- "Frequency Body Gyroscope X Mean"
colnames(tidyData)[28] <- "Frequency Body Gyroscope Y Mean"
colnames(tidyData)[29] <- "Frequency Body Gyroscope Z Mean"
colnames(tidyData)[30] <- "Frequency Body Gyroscope X Standard Deviation"
colnames(tidyData)[31] <- "Frequency Body Gyroscope Y Standard Deviation"
colnames(tidyData)[32] <- "Frequency Body Gyroscope Z Standard Deviation"

#writes Tidy data file with all 10299 observations of 30 variables with column names and activity labels
write.csv(tidyData, "TidySamsungData.csv", row.names = FALSE)
summaryData <- read.csv("TidySamsungData.csv")

varNames <- colnames(summaryData[3:32])

#Creates a second, independent tidy data set with the average of each variable for each activity and 
#each subject. 

library(reshape2)

#This loop creates a data table with all 30 averages of mean/std measurements for each variable/activity
#combo, then extracts from that data table a vector for each subject/activity combo containing 30 variable 
#means, (30 subjects with 6 activities each yields 180 rows)
myList <- list()

for (i in 3:32) {
  reshapedData <- dcast(summaryData[i], summaryData$Activity ~ summaryData$Subject, mean)
  reshapedData2 <- as.vector(rbind(reshapedData[,2], reshapedData[,3], reshapedData[,4], reshapedData[,5], 
                                   reshapedData[,6], reshapedData[,7],reshapedData[,8], reshapedData[,9], 
                                   reshapedData[,10], reshapedData[,11], reshapedData[,12], reshapedData[,13], 
                                   reshapedData[,14], reshapedData[,15], reshapedData[,16], reshapedData[,17],
                                   reshapedData[,18], reshapedData[,19], reshapedData[,20], reshapedData[,21], 
                                   reshapedData[,22], reshapedData[,23], reshapedData[,24], reshapedData[,25], 
                                   reshapedData[,26], reshapedData[,27], reshapedData[,28], reshapedData[,29], 
                                   reshapedData[,30], reshapedData[,31]))
  myList <- cbind(myList, reshapedData2)
}

#Adds "average" label to previous column titles, to label computation
colnames(myList) <- paste("Average", gsub("\\."," ",varNames))

#This loop creates row names for all 180 observations in tidy data set (30 subjects with 6 activities), 
#as subject/activiy combination is smallest unit label 
summaryRowNames = c()

for (i in 1:30)
{
  walk <- paste("Subject", i, "Walking")
  walkup <- paste("Subject", i, "Walking Upstairs")
  walkdown <- paste("Subject", i, "Walking Downstairs")
  sitting <- paste("Subject", i, "Sitting")
  standing <- paste("Subject", i, "Standing")
  laying <- paste("Subject", i, "Laying")  
  
  summaryRowNames = c(summaryRowNames, walk, walkup, walkdown, sitting, standing, laying)
}

#updates row names in reshaped data of subj/activity means for each variable 
rownames(myList) <- summaryRowNames

#writes tidiest of data tables for submission
write.csv(myList, "SummarySamsungData.csv")
write.table(myList, file = "SummarySamsungData.txt")

