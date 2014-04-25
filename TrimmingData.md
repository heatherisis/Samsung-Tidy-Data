## These instructions can only be followed after those from "OrganizingData.md" and "CompilingData.md" have been successfully completed
##Now that we have data set with all subject/activity and variable names all in one file, it is time to determine which variables can be eliminated, as some of the 79 variables can be considered derivations of the original measurements

###Of 79 selected variables, those with meanFreq calculations omitted, as derived from original measurements
tidyData <- subset(tidyData, select = -c(49:51,58:60,67:69,72,75,78,81))
###eliminate non-measurement vars, including jerk signals and magnitude, as derived from original measurement mean/std
tidyData <- subset(tidyData, select = -c(15:20,27:42,49:54,61:68))

###Rename all column names with meaningul titles without code
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

###writes Tidy data file with all 10299 observations of 30 variables with column names and activity labels
write.csv(tidyData, "TidySamsungData.csv", row.names = FALSE)
summaryData <- read.csv("TidySamsungData.csv")

varNames <- colnames(summaryData[3:32])
