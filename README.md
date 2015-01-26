# datahandler
Tidy Data Set Project
README Document

Result of this project is a data frame containing average measures for individual subjects for each of six activities. Raw data on the measurements came from the
Human Activity Recognition Using Smartpbhones Dataset. Definitions for measurement variables. subject identification, and definition of activities came from files released for this research.

The raw data used in analysis involved two groups of subjects: a test set (9 individuals) and a training set with data for the remaining 21 subjects. There were three files for each of the two groups:
	Test Set data: subject list(subject_test.txt), activity list (y_test.txt), and results (X_test.txt)
	Training Set data: subject list(subject_train.txt), activity list (y_train.txt), and results (X_train.txt)

In addition, the file features.txt listed the direct and derived measures used in developing Human Activity Recognition Using Smartpbhones Dataset. The training and test files had the same number of columns:
subject_train has 7352 rows and 1 column; subject_test has 2947 rows and 1 column.	
y_train has 7352 rows and 1 column; y_test has 2947 rows and 1 column.
X_train has 7352 rows and 561 columns; X_test has 2947 rows and 561 columns.

A description of the variables used in this analysis is available in the file ProjectCodebook.txt.

The first step in the analysis for this project required combining the test and training datasets into one table. This was accomplished by combining the files for each of the test and training sets separately and then combining the two dataframes into one. The subject and y columns were added to the X data, and then ""rbind"" was used to combine the two sets, each with 563 columns. 
	
The second step required selecting the variables which were derived by calculating means or standard deviations of experiment data from the combined dataset. I identified derived means and standard deviations as those variables with "mean ()" or "std ()" in their names. The Features list included variables that represented mean frequencies, but these were not selected since it was not clear that they were calculated in the same way. 

I used the "grep" function to identify the indices of variable names with either "mean()" or "std()" in their names, and then selected those columns from the combined dataset. The resulting dataframe had 10299 rows and 68 columns.

The raw data file referred to activities by number (1 through 6). To make the final table more readable, the activity numbers were replaced by the name of the activity, by looping through the activity label column (ActLabel).

The variable names from the raw data contained illegal characters in R ("-" and "()") so these were removed. Also, there were several cases of variables with a typo ("BodyBody" rather than "Body"). The function "gsub" was used to carry out removing the illegal characters and in correcting the typos.

The final result for the project is a dataframe with 180 rows and 68 columns, with averages of the values for the selected features for each subject and each activity. The function "ddply" was used to group the data by subject and by activity, and then averages were calculated for each feature. The final result was written to the file AvgActivityMeasures.txt.

