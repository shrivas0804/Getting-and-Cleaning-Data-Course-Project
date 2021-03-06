README
Synopsis

As the course project to Getting and Cleaning Data on Coursera, this project will download and extract raw data from https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip automatically, and complete the following steps as is instructed.

Merges the training and the test sets to create one data set.
Extracts only the measurements on the mean and standard deviation for each measurement.
Uses descriptive activity names to name the activities in the data set
Appropriately labels the data set with descriptive variable names.
Creates a second, independent tidy data set with the average of each variable for each activity and each subject.
Requirements

Libraries
reshape2
Usage

> source("run_analysis.R") # Might run for quite a while if you have a slow connection / disk.
>                          # Check "tidyData.txt" in working directory
Files & Folders

CodeBook.md - the code book
README.md - this file
run_analysis.R - Primary script to process data
lib/ - libraries to be loaded via source()
fetch.R - download, verify, and extract raw data file from internet
main.R - functions used by run_analysis.R to process the data
data/ - placeholder to downloaded and extracted data files
On Picking Variables

I'd pick raw data (from accelerometer and gyroscope) as measurements if they were in the data set and well documented. However, data in "Inertial Signals" are ill-defined, and the formulation deriving tBodyAcc and tGravityAcc from body acceleration does not exist in the documents.

So I relaxed my restriction to include derived data columns as each measurement stated in step 2. Most columns with mean or std falls into this category, including *meanFreq. Exceptions are those enclosed with angle(), for they are angle between vector means rather than means on angle measurements.