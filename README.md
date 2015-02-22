## GnCD_CourseProject

There is one script for this project, 'run_analysis.r'.
When the script is sourced to the console in R studio, it should output, among other data, 
the 180x68 'dfAverages'. dfAverages should show as a table in the top left window of RStudio.

One way to view the text file associated with the project is to do the following:
fileURL <- download.file(url, destfile="./courseProjectAverages.txt",method="curl") 
data <- read.table("courseProjectAverages.txt", header=T)
View(data)

One way to move the run_analysis script into RStudio is to clone the URL for this repo, go to Project>New Project>Version Control>git, paste the URL into Repository URL field, then create project.

The raw data for the project were downloaded from this zip folder: 
https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip 

CodeBook.md explains how and why the data frame is shaped and summarized, 
adds a couple other notes, and includes a table with a summary of each variable.


