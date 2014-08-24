Course Project: Getting and Cleaning Data (Part of the Data Science Specialization offered by Johns Hopkins University)
=======================================================================================================================
This repository contains the details of my work done for the Course project, which involves creating a tidy data set from raw data collected from the accelerometers of the Samsung Galaxy S smartphone. One of the most exciting areas in all of data science right now is wearable computing. Companies like Fitbit, Nike, and Jawbone Up are racing to develop the most advanced algorithms to attract new users and the dataset for this project pertains to this area.

1) RAW DATA:
============
Raw data for this project is present at this location - https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip. The README.txt file that accompanies the dataset has the following details about the raw data.

The experiments have been carried out with a group of 30 volunteers within an age bracket of 19-48 years. Each person performed six activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) wearing a smartphone (Samsung Galaxy S II) on the waist. Using its embedded accelerometer and gyroscope, we captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz. The experiments have been video-recorded to label the data manually. The obtained dataset has been randomly partitioned into two sets, where 70% of the volunteers was selected for generating the training data and 30% the test data. 

The sensor signals (accelerometer and gyroscope) were pre-processed by applying noise filters and then sampled in fixed-width sliding windows of 2.56 sec and 50% overlap (128 readings/window). The sensor acceleration signal, which has gravitational and body motion components, was separated using a Butterworth low-pass filter into body acceleration and gravity. The gravitational force is assumed to have only low frequency components, therefore a filter with 0.3 Hz cutoff frequency was used. From each window, a vector of features was obtained by calculating variables from the time and frequency domain. See 'features_info.txt' for more details. 

For each record it is provided:
======================================
- Triaxial acceleration from the accelerometer (total acceleration) and the estimated body acceleration.
- Triaxial Angular velocity from the gyroscope. 
- A 561-feature vector with time and frequency domain variables. 
- Its activity label. 
- An identifier of the subject who carried out the experiment.

The dataset includes the following files:
=========================================
- 'README.txt'
- 'features_info.txt': Shows information about the variables used on the feature vector.
- 'features.txt': List of all features.
- 'activity_labels.txt': Links the class labels with their activity name.
- 'train/X_train.txt': Training set.
- 'train/y_train.txt': Training labels.
- 'test/X_test.txt': Test set.
- 'test/y_test.txt': Test labels.

The following files are available for the train and test data. Their descriptions are equivalent. 
- 'train/subject_train.txt': Each row identifies the subject who performed the activity for each window sample. Its range is from 1 to 30. 
- 'train/Inertial Signals/total_acc_x_train.txt': The acceleration signal from the smartphone accelerometer X axis in standard gravity units 'g'. Every row shows a 128 element vector. The same description applies for the 'total_acc_x_train.txt' and 'total_acc_z_train.txt' files for the Y and Z axis. 
- 'train/Inertial Signals/body_acc_x_train.txt': The body acceleration signal obtained by subtracting the gravity from the total acceleration. 
- 'train/Inertial Signals/body_gyro_x_train.txt': The angular velocity vector measured by the gyroscope for each window sample. The units are radians/second. 

2) TIDY DATA SET:
=================
After merging the training and test datasets, the script (run_analysis.r) creates a tidy dataset that contains the average of all columns that denotes the mean and standard deviation of the measurements captured in the raw data. This average is computed for every activity and by each subject. The tidy dataset so created has 81 columns (2 columns for Activity and Subject, 79 columns of the mean values) and is written out to the working directory using write.table command. Column level details of tidy data set is given in 'codebook.md' present in this repository. The tidy dataset is also uploaded.

3) R SCRIPT (to create tidy data)
=================================
The R script - run_analysis.R (uploaded into this repository) is created to convert the raw data to tidy dataset and does the following:

1. Reads the training, testing, activity and features files by using the read.csv command. (The files present within the Inertial Signals directory are ignored as they have redundant information).
2. Merges the training and the test sets to create one data set. Pre-requisite is that the UCI HAR dataset should be extracted and present in the working directory.
3. Extracts only the measurements on the mean and standard deviation for each measurement by using the 'grep' command
4. Appropriately labels the data set with descriptive variable names.
5. Creates an initial version of the tidy dataset by using the 'aggregate' command which computes the mean of extracted measurements by activity and by user.
6. Merges the initial version of the tidy dataset with activity labels (using merge command) so that descriptive names are provided for activities. This is the final version of the tidy dataset that has the average of each variable for each activity and each subject.

4) Code Book
=============
The code book markdown file explains the variables present in the tidy dataset. This is uploaded as a separate file in the repository.