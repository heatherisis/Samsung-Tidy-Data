#Getting and Cleaning Samsung Data: README.md
=================

The following markdown files are included in this Samsung-Tidy-Data repository. They are separated into chunks for convenience at accessing the code to investigate a specific sub-process in the data cleanup. The manuscripts are intended to be followed in the following order (see detailed information below):

* 1. OrganizingData
* 2. CompilingData
* 3. TrimmingData
* 4. ReshapingData


###1. OrganizingData 

* Downloads dataset from website
* Reads in individual files
* Separates data file into individual observations
* Selects only variables with "mean" and 'sd' in name for each observation
* Creates tidy data set for each range of values
* Reads data sets into R
* Combines data sets into one compiled data set

=================

###2. CompilingData 
* Reads in compiled data set
* Extracts subject/activity codes from original text files
* Adds subject/activity columns for all 10299 observations
* Labels columns
* Replaces activity code with activity names
* Finds 79 selected variable names
* Renames each variable with coded name in data set

=================

3. TrimmingData - 
* From cleaned data set, omits columns with meanFreq calculations
* Omits columns with jerk signal and magnitude, as derived from original measurement mean/std 
* Renames remaining 30 columns with readable variable names
* Writes new data set with all 30 selected variables, including row/column names

=================

4. ReshapedData - 
* From tidy data set, creates a data table with all 30 averages of mean/std measurements for each variable/activity combo
* Extracts from that data table a vector for each subject/activity combo containing 30 variable means
* Adds "average" label to columns
* Labels rows with subject and activity label, as is the smallest unit of identification
* Writes tidiest data table with organized means
