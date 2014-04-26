#Getting and Cleaning Samsung Data:  Code Book



###This is a code book that describes the variables, the data, and any transformations or work that I performed to clean up the data


##Introduction

Smart phones are advancing daily. The Samsung Galaxy S-III is a phone that has built-in sensors, including a compass, gyroscope, accelerometer, and barometer [1]. The information collected from these sensors purportedly serves to alert the phone of the user’s state of action, allowing such features as the light staying on, automatic calls, and vibrating to alert you of calls when the phone is simply held upright [2]. Graduate students at The University of California at Irvine (UCI) created the Machine Learning Repository (MLR) in 1987 to house databases, domain theories, and data generators to be used by students, educators, and researchers as a primary source of machine learning data sets [3]. UCI’s “Human Activity Recognition Using Smartphones Data Set” tracked the activity of 30 volunteers between the ages of 19 and 48 who performed a variety of activities with a Samsung Galaxy X III phone tied at their waist [4]. The six activities performed in the collection included laying, sitting, standing, walking on flat ground, walking down stairs, and walking up stairs [4]. The phone’s internal accelerometer and gyroscope measured a variety of variables, upon which a set of calculations was performed to obtain five-hundred and sixty-one numeric values for each person performing each activity [4]. 

##Data Collection

For analysis, I used the data downloaded from UCI’s website [4], which was added to the repository on December 10, 2012. The data were downloaded from the cited source [10] using the R programming language [11]. The downloaded data consist of a sample of 10299 observations of one of thirty participants performing one of the six actions [10]. The thirty participants included in the data set were randomly divided into a training set and a test set [4]. 

* The training set included twenty-one subjects.
     [1]  1  3  5  6  7  8 11 14 15 16 17 19 21 22 23 25 26 27 28 29 30

* The test set included nine subjects.
     [1]  2  4  9 10 12 13 18 20 24

An accelerometer and a gyroscope were used to collect the 561 one values for each participant performing each activity (10299 combinations). With both devices, three axial linear acceleration and three axial angular velocity measures were captured at a constant rate (50Hz) and with a noise filter [5]. The accelerometer measures collected were divided into body and gravity acceleration signals [5]. All measures were collected along an X, Y, and Z axis, the X-axis along a horizontal side-to-side plane, the Y-axis along an up-and-down vertical plane, and the Z-axis along a horizontal forward-backward plane [6]. The body acceleration measure is considered proper acceleration, or the speed increase relative to a free fall [7] while the gravity acceleration measure was collected with a low frequency filter (cutoff 0.3Hz) [5]. The data taken from the gyroscope measure orientation based on principles of angular momentum [8]. Linear body acceleration and angular velocity over time were used to calculate a “jerk” magnitude (the rate of change of acceleration [9]).  

Of the 561 variables, only 79 were included in the cleaning up the data set. The values were initially selected based on those containing "mean" or "std" (standard deviation) in the title. Upon later inspection, those with mean frequency, jerk signal, and magnitude calculations were omitted, as they were determined to be derived from original measurements, leaving 30 variables in the data set to be tidied. 

* "1 tBodyAcc-mean()-X" "2 tBodyAcc-mean()-Y" "3 tBodyAcc-mean()-Z" "4 tBodyAcc-std()-X" "5 tBodyAcc-std()-Y" "6 tBodyAcc-std()-Z"      
* "41 tGravityAcc-mean()-X" "42 tGravityAcc-mean()-Y" "43 tGravityAcc-mean()-Z" "44 tGravityAcc-std()-X" "45 tGravityAcc-std()-Y" "46 tGravityAcc-std()-Z"  
* "121 tBodyGyro-mean()-X" "122 tBodyGyro-mean()-Y" "123 tBodyGyro-mean()-Z" "124 tBodyGyro-std()-X" "125 tBodyGyro-std()-Y" "126 tBodyGyro-std()-Z"   
* "266 fBodyAcc-mean()-X" "267 fBodyAcc-mean()-Y" "268 fBodyAcc-mean()-Z" "269 fBodyAcc-std()-X" "270 fBodyAcc-std()-Y" "271 fBodyAcc-std()-Z"    
* "424 fBodyGyro-mean()-X" "425 fBodyGyro-mean()-Y" "426 fBodyGyro-mean()-Z" "427 fBodyGyro-std()-X" "428 fBodyGyro-std()-Y" "429 fBodyGyro-std()-Z" 

All of the coded column names were renamed with meaningul titles without code.

* "Time Body Accelerometer X/Y/Z Mean"
  "Time Body Accelerometer X/Y/Z Standard Deviation"
* "Time Gravity Accelerometer X/Y/Z Mean"
  "Time Gravity Accelerometer X/Y/Z Standard Deviation"
* "Time Body Gyroscope X/Y/Z Mean"
  "Time Body Gyroscope X/Y/Z Standard Deviation"
* "Frequency Body Accelerometer X/Y/Z Mean"
  "Frequency Body Accelerometer X/Y/Z Standard Deviation"
* "Frequency Body Gyroscope X/Y/Z Mean"
  "Frequency Body Gyroscope X/Y/Z Standard Deviation"

##Reproducibility

All analyses performed in this manuscript are reproduced in an R markdown file [12]. To reproduce exactly what was performed in this data analysis, the same data set that was published in December 2012 must be used [4].

##References

1. Samsung Galaxy S X III “Specifications” Page. URL: http://www.samsung.com/global/galaxys3/specifications.html. Accessed 12/6/2013.

2. Samsung Galaxy S X III “Features” Page. URL:
http://www.samsung.com/global/galaxys3/smartstay.html. Accessed 4/14/2014.

3. UCI Machine Learning Repository “About” Page. URL: http://archive.ics.uci.edu/ml/about.html/. Accessed 4/14/2014.

4. UCI Machine Learning Repository “Human Activity Recognition Using Smartphones Data Set” Page. URL: http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones. Accessed 4/14/2014.

5. UCI HAR Dataset “Feature Selection” text in “features_info.txt” File. URL: http://archive.ics.uci.edu/ml/machine-learning-databases/00240/UCI%20HAR%20Dataset.zip.

6. Stack Overflow “How to Use Gyro Z Axis on the IPhone” http://stackoverflow.com/questions/7254088/how-to-use-gyro-z-axis-on-the-iphone. Accessed 12/7/13.

7. Wikipedia “Accelerometer” Page. URL: http://en.wikipedia.org/wiki/Accelerometer. Accessed 12/6/2013.

8. Wikipedia “Gyroscope” Page. URL: http://en.wikipedia.org/wiki/Gyroscope. Accessed 12/6/2013.

9. Wikipedia “Jerk (physics)” Page. URL: http://en.wikipedia.org/wiki/Jerk_(physics). Accessed 12/6/2013.

10. Anguita, D., Ghio, A., Oneto, L., Parra, X., and Reyes-Ortiz, J.L. Human Activity Recognition on Smartphones using a Multiclass Hardware-Friendly Support Vector Machine. International Workshop of Ambient Assisted Living (IWAAL 2012). Vitoria-Gasteiz, Spain. Dec 2012. Samsung data downloaded from page. URL: https://spark-public.s3.amazonaws.com/dataanalysis/samsungData.rda. Accessed 12/1/13.

11. R Core Team (2012). “R: A language and environment for statistical computing.” URL: http://www.R-project.org.

12. R Markdown Page. URL: http://www.rstudio.com/ide/docs/authoring/using_markdown. Accessed 4/23/14.
