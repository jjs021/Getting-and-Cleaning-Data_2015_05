# Codebook
A description of the cleaning done to the data, and its meaning.

## Running `run_analysis.R` RE: your workspace
Running run_analysis.R (with the prerequisites mentioned in the file) will add the following to your workspace:
- `file.dir.name`  
 "UCI HAR Dataset"  
 The name of the data directory.  
- `file.test.subject.path`  
 "test/subject_test.txt"  
 The path to the test set subject data in the data directory.  
- `file.test.x.path`  
 "test/X_test.txt"  
 The path to the test set feature data in the data directory.
- `file.test.y.path`  
 "test/y_test.txt"  
 The path to the test set activity label data in the data directory.
- `file.train.subject.path`  
 "train/subject_train.txt"  
 The path to the training set subject data in the data directory.
- `file.train.x.path`  
 "train/X_train.txt"  
 The path to the training set feature data in the data directory.
- `file.train.y.path`  
 "test/y_test.txt"  
 The path to the training set activity label data in the data directory.
- `activity.mapping`  
 A named vector that maps the numbered activity labels to named activity labels as described in the Activity label definitions section. Used by assignment step 3.
- `columns.limited`  
 A vector of which of the columns from the merged data, should be retained in the limited data. As per the assignment's step 2 only mean and standard deviation data is kept for the features. Also angles with the mean are kept.
- `columns.names`  
 A vector of all the column names for the merged data. This is more extensive than the ones described in the next section, and are described in the dataset's `features_info.txt`
- `data.merged`  
 The result of assignment step 1 which merges the training and test set data back into a single data set as a table with subject, features, and activity labels. After assignment step 3 these labels are plain text from the `activity.mapping`. And after assignment step 4 the columns are given names as in the next section.
- `data.limited`  
 The result of assignment step 2 which limits the feature data to only mean and standard deviation for the features, and angles with the mean. After assignment step 3 these labels are plain text from the `activity.mapping`. And after assignment step 4 the columns are given names as in the next section.
- `data.means`  
 The result of assignment step 5 which reduces the limited data to the average or mean of each feature when per subject and activity type.


## The columns of `data.limited` and `data.means`
The following list uses short-hand notation. For example *tBodyAcc mean(X,Y,Z) std(X,Y,Z)* expands to: tBodyAcc-mean()-X, tBodyAcc-mean()-Y, tBodyAcc-mean()-Z, tBodyAcc-std()-X, tBodyAcc-std()-Y, tBodyAcc-std()-Z. *tGravityAcc mean(X,Y,Z) std(X,Y,Z)* expands to: tGravityAcc-mean()-X, tGravityAcc-mean()-Y, tGravityAcc-mean()-Z, tGravityAcc-std()-X, tGravityAcc-std()-Y, tGravityAcc-std()-Z. While *tBodyAccMag mean std* expands to: tBodyAccMag-mean(), tBodyAccMag-std(). All the expanded column names appear in the vector `columns.names`

These 75 columns are the same between `data.means` and `data.limited`. However the 10299 observations in `data.limited` are averaged for each subject's activity resulting in 180 mean feature measurements.

Note that where jerk is used it means the body linear acceleration and angular velocity were derived to get jerk signals.

Also note that frequency means the fast Fourier transformation of the time domain data.

- 1 *Subject*  
 Unique ID of each volunteer
- 2-7 *tBodyAcc             mean(X,Y,Z) std(X,Y,Z)*  
 The time domain body accelerometer acceleration,  
 as a mean for the time window and as a standard deviation,  
 in X, Y, and Z vectors.
- 8-13  *tGravityAcc           mean(X,Y,Z) std(X,Y,Z)*  
 The time domain gravity accelerometer acceleration,  
 as a mean for the time window and as a standard deviation,  
 in X, Y, and Z vectors.
- 14-19 *tBodyAccJerk         mean(X,Y,Z) std(X,Y,Z)*  
The time domain body accelerometer acceleration jerk,  
as a mean for the time window and as a standard deviation,  
in X, Y, and Z vectors.
- 20-25 *tBodyGyro            mean(X,Y,Z) std(X,Y,Z)*  
The time domain body gyroscopic acceleration,  
as a mean for the time window and as a standard deviation,  
in X, Y, and Z vectors.
- 26-31 *tBodyGyroJerk        mean(X,Y,Z) std(X,Y,Z)*  
The time domain body gyroscopic acceleration jerk,  
as a mean for the time window and as a standard deviation,  
in X, Y, and Z vectors.
- 32-33 *tBodyAccMag          mean        std*  
The time domain body accelerometer acceleration magnitude,  
as a mean for the time window and as a standard deviation.
- 34-35 *tGravityAccMag       mean        std*  
The time domain gravity accelerometer acceleration magnitude,  
as a mean for the time window and as a standard deviation.
- 36-37 *tBodyAccJerkMag      mean        std*  
The time domain body accelerometer acceleration jerk magnitude,  
as a mean for the time window and as a standard deviation.
- 38-39 *tBodyGyroMag         mean        std*  
The time domain body gyroscopic acceleration magnitude,  
as a mean for the time window and as a standard deviation.
- 40-41 *tBodyGyroJerkMag     mean        std*  
The time domain body gyroscopic acceleration jerk magnitude,  
as a mean for the time window and as a standard deviation.
- 42-47 *fBodyAcc             mean(X,Y,Z) std(X,Y,Z)*  
The frequency body accelerometer acceleration,  
as a mean for the time window and as a standard deviation,  
in X, Y, and Z vectors.
- 48-53 *fBodyAccJerk         mean(X,Y,Z) std(X,Y,Z)*  
The frequency body accelerometer acceleration jerk,  
as a mean for the time window and as a standard deviation,  
in X, Y, and Z vectors.
- 54-59 *fBodyGyro            mean(X,Y,Z) std(X,Y,Z)*  
The frequency body gyroscopic acceleration,  
as a mean for the time window and as a standard deviation,  
in X, Y, and Z vectors.
- 60-61 *fBodyAccMag          mean        std*  
The frequency body accelerometer acceleration magnitude,  
as a mean for the time window and as a standard deviation.  - 62-63 *fBodyAccJerkMag  mean        std*  
The frequency body accelerometer acceleration jerk magnitude,  
as a mean for the time window and as a standard deviation.  - 64-65 *fBodyGyroMag     mean        std*  
The frequency body gyroscopic acceleration magnitude,  
as a mean for the time window and as a standard deviation.  - 66-67 *fBodyGyroJerkMag mean        std*  
The frequency body gyroscopic acceleration jerk magnitude,  
as a mean for the time window and as a standard deviation.  - 68 *angle(tBodyAccMean,gravity)*  
The angle between the time domain body accelerometer acceleration mean and gravity.
- 69 *angle(tBodyAccJerkMean),gravityMean)*  
The angle between the time domain body accelerometer acceleration jerk mean and mean gravity.
- 70 *angle(tBodyGyroMean,gravityMean)*  
The angle between the time domain body gyroscopic acceleration mean and mean gravity.
- 71 *angle(tBodyGyroJerkMean,gravityMean)*  
The angle between the time domain body gyroscopic acceleration jerk mean and mean gravity.
- 72 *angle(X,gravityMean)*  
The angle between the X axis and mean gravity.
- 73 *angle(Y,gravityMean)*  
The angle between the Y axis and mean gravity.
- 74 *angle(Z,gravityMean)*  
The angle between the Z axis and mean gravity.
- 75 *Activity*  
  The type of activity the subject performed. Assigned value 1:6 in the source, and mapped according to the next section.

## Activity label definitions
1. `Walking`
2. `Walking Upstairs`
3. `Walking Downstairs`
4. `Sitting`
5. `Standing`
6. `Laying`
