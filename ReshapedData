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
