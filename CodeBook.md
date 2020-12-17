# Description
The file `run_analysis.R` script was coded focusing on the data preparation and the five steps as required by the coursera project.

# Steps
**Step 0. Download data and load into data frames**

*Download the dataset*
- Download and extract dataset into the `UCI HAR Dataset` folder  

*Load data into data frames*
- `features` <- **features.txt** - resulting in 2 columns, 561 observations
- `activities` <- **activity_labels.txt** - resulting in 2 columns, 6 observations
- `subject_test` <- **test/subject_test.txt** - resulting in 1 column, 2947 observations
- `x_test` <- **test/X_test.txt** - resulting in 561 columns, 2947 observations
- `y_test` <- **test/y_test.txt** - resulting in 1 columns, 2947 observations
- `subject_train` <- **test/subject_train.txt** - resulting in 1 column, 7352 observations
- `x_train` <- **test/X_train.txt** - resulting in 561 columns, 7352 observations
- `y_train` <- **test/y_train.txt** - resulting in 1 columns, 7352 observations

**Step 1. Merge the training and the test sets to create one data set**
- `X` resulted by merging **x_train** and **x_test** using **rbind()** - 561 columns 10299 rows
- `Y` resulted by merging **y_train** and **y_test** using **rbind()** - 1 col 10299 rows
- `subject` resulted by merging **subject_train** and **subject_test** using **rbind()** - 1 column 10299 rows
- `mergedData` resulted by merging **subject**, **Y** and **X** using **cbind()** function - 563 columns 10299 rows

**Step 2. Extract only the measurements on the mean and standard deviation for each measurement**
- `fullDataset` resulted by subsetting **mergedData**, selecting the requested columns - 88 columns 10299 rows

**Step 3. Use descriptive activity names to name the activities in the data set**
- Integer data into column `fullDataset$code` was replaced by **activity** name 

**Step 4. Appropriately label the data set with descriptive variable names**
- The `code` column in `fullDataset` was renamed as `activities`
- Occurrences of `Acc` in column's name were replaced by `Accelerometer`
- Occurrences of `BodyBody` in column's name were replaced by `Body`
- Occurrences of `Gyro` in column's name were replaced by `Gyroscope`
- Occurrences of `Mag` in column's name were replaced by `Magnitude`
- Occurrences beginning with character `f` in column's name were replaced by `Frequency`
- Occurrences beginning with character `t` in column's name were replaced by `Time`
- Occurrences of `tBody` in column's name were replaced by `TimeBody` 
- Occurrences of `-mean()` in column's name were replaced by `Mean` 
- Occurrences of `-std()` in column's name were replaced by `STD`
- Occurrences of `-freq()` in column's name were replaced by `Frequency` 
- Occurrences of `angle` and `gravity` in column's name just replaced with the capitalized word.  

**Step 5. From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject**
- `resultDataset` resulted by sumarizing `fullDataset` taking the means of each variable for each activity and each subject, after groupped by subject and activity:  88 columns, 180 rows
- Finally export the `resultDataset` into **resultDataset.txt** file.

