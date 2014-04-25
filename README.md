Getting and Cleaning Samsung Data
=================

## Coursera Course Project

=================

###1. OrganizingData 

* Downloads dataset from website
* Reads in individual files
* Separates data file into individual observations
* Selects only variables with "mean" and 'sd' in name for each observation
* Creates tidy data set for each range of values
* Reads data sets into R
* Combines data sets into one compiled data set

=================

###2. CompilingData - Reads in compiled data set, extracts subject/activity codes from original text files, adds subject/activity columns for all 10299 observations, labels columns, replaces activity code with activities, finds 79 selected variable names, renames each variable with coded name in data set
=================

3. TrimmingData - From cleaned data set, omits columns with meanFreq calculations, jerk signal, and magnitude, as derived from original measurement mean/std, renames remaining 30 columns with readable variable names, writes new data set with all 30 selected variables, including row/column names
=================
4. ReshapedData - From tidy data set, creates a data table with all 30 averages of mean/std measurements for each variable/activity combo, extracts from that data table a vector for each subject/activity combo containing 30 variablemeans, adds "average" label to columns, labels rows with subject and activity label, as is the smallest unit of identification, writes tidiest data table with organized means






