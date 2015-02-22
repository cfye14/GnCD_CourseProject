##Data Cleaning Explanation and Other Notes
The final data frame is assigned to dfAverages. The final command should show dfAverages as a table in the top left window of RStudio.

dfAverages has 180 rows and 68 columns. The 180 rows are for the 30 different subjects measured on 6 different activities. 
The data is arranged by subject and then activity, and the order of the columns as such with subject id in the first column. 
The following 66 columns are average of the mean and standard deviation ('std') of the 33 measurements 
captured by the accelerometer and gyroscope of the Samsung phones. The labels were taken from the 'features.txt' file and not altered,
because changing the variable names was not perceived as worthwhile from an offhand benefit/cost calculation. 

The 'run_analysis.r' script assumes the 'UCI HAR Dataset' is unzipped in the working directory such that arguments of the form
'read.csv("./UCI HAR Dataset/..."' work.

The data was cleaned and transformed in the following steps:

1. ####created a combined data frame of the test and training data. 

  * The three data frames for the test and training data each were combined, 
by the columns [subject id];[activity id];[1:561 measurement variables]. Then, the test and training data were combined, 
creating a longer data frame with the same number of columns. 

2. ####reduced and rearranged the data frame from the previous step

  * The mean and standard deviation of each measurement, 66 columns in total, were extracted from the 561 measurement variables from the original data.
The columns were extraced via the logical grep function, grepl. The data frame was then re-arranged by subject and activity by means of 
the arrange function from the dplyr package.

3. ####reshape and take mean of each measurement

  * The data was reshaped via the melt function, which created a (temporary) very long data frame, before being cast (via dcast from the reshape2 library)
into the final data frame, with the measurement averages in separate columns for each subject/activity grouping.

4. ####replace activity IDs with descriptive activity names

  * This step was the most unconventional in the context of the course as a function not covered up to this course was used. The mapvalues function
from the plyr package 'mapped' from the values 1:6 to the corresponding activity names for each activity ID. The activity description names are lowercase
and not uppercase as in the 'activity-labels.txt' file in the UCI Dataset folder.

Note: The tidy data form of the final data frame is 'wide,' in that each measurement are appended to each subject/activity group. The other option 
would have been to create a 'long' data frame, with one measurement value column for each subject/activity/measurement group.

##Codebook   

Explanation: There are 66 column variables that are the average for the mean and standard deviation of 33 measurements from the Samsung smartphones. Note that the value recorded in the final data frame for the 66 measurements is an average. In the table below, 'value explained' describes what each measurement is, or what is being averaged.


<!DOCTYPE html>
<html>
<body>

<table style="width:80%">
	<tr>
		<th>var.name</th>
		<th>column</th>
		<th>class</th>
		<th>value explained</th>
	</tr>
	<tr>
	    <td>subject</td>
	    <td>1</td>		
	    <td>integer</td>
		<td>1:30</td>
	</tr>
	<tr>
	    <td>activity</td>
	    <td>2</td>		
	    <td>character</td>
		<td>walking;walking_upstairs; walking_downstairs;sitting; standing;laying</td>
	</tr>
	<tr>
	    <td>tBodyAcc-mean()-X</td>
	    <td>3</td>		
	    <td>numeric</td>
		<td>Mean accelerometer reading, body motion acceleration along x-axis, time domain</td>
	</tr>
	<tr>
	    <td>tBodyAcc-mean()-Y</td>
	    <td>4</td>		
	    <td>numeric</td>
		<td>Mean accelerometer reading, body motion acceleration along y-axis, time domain</td>
	</tr>
	<tr>
	    <td>tBodyAcc-mean()-Z</td>
	    <td>5</td>		
	    <td>numeric</td>
		<td>Mean accelerometer reading, body motion acceleration along z-axis, time domain</td>
	</tr>
	<tr>
	    <td>tBodyAcc-std()-X</td>
	    <td>6</td>		
	    <td>numeric</td>
		<td>St.Dev of accelerometer reading, body motion acceleration along x-axis, time domain</td>
	</tr>
	<tr>
	    <td>tBodyAcc-std()-Y</td>
	    <td>7</td>		
	    <td>numeric</td>
		<td>St.Dev of accelerometer reading, body motion acceleration along y-axis, time domain</td>
	</tr>
	<tr>
	    <td>tBodyAcc-std()-Z</td>
	    <td>8</td>		
	    <td>numeric</td>
		<td>St.Dev of accelerometer reading, body motion acceleration along z-axis, time domain</td>
	</tr>
	<tr>
	    <td>tGravityAcc-mean()-X</td>
	    <td>9</td>		
	    <td>numeric</td>
		<td>Mean accelerometer reading, gravitational acceleration along x-axis, time domain</td>
	</tr>
	<tr>
	    <td>tGravityAcc-mean()-Y</td>
	    <td>10</td>		
	    <td>numeric</td>
		<td>Mean accelerometer reading, gravitational acceleration along y-axis, time domain</td>
	</tr>
	<tr>
	    <td>tGravityAcc-mean()-Z</td>
	    <td>11</td>		
	    <td>numeric</td>
		<td>Mean accelerometer reading, gravitational acceleration along z-axis, time domain</td>
	</tr>
	<tr>
	    <td>tGravityAcc-std()-X</td>
	    <td>12</td>		
	    <td>numeric</td>
		<td>St.Dev of accelerometer reading, gravitational acceleration along x-axis, time domain</td>
	</tr>
	<tr>
	    <td>tGravityAcc-std()-Y</td>
	    <td>13</td>		
	    <td>numeric</td>
		<td>St.Dev of accelerometer reading, gravitational acceleration along y-axis, time domain</td>
	</tr>
	<tr>
	    <td>tGravityAcc-std()-Z</td>
	    <td>14</td>		
	    <td>numeric</td>
		<td>St.Dev of accelerometer reading, gravitational acceleration along z-axis, time domain</td>
	</tr>
	<tr>
	    <td>tBodyAccJerk-mean()-X</td>
	    <td>15</td>		
	    <td>numeric</td>
		<td>Mean jerk signal* of accelerometer reading, body motion acceleration along x-axis, time domain</td>
	</tr>
	<tr>
	    <td>tBodyAccJerk-mean()-Y</td>
	    <td>16</td>		
	    <td>numeric</td>
		<td>Mean jerk signal* of accelerometer reading, body motion acceleration along y-axis, time domain</td>
	</tr>
	<tr>
	    <td>tBodyAccJerk-mean()-Z</td>
	    <td>17</td>		
	    <td>numeric</td>
		<td>Mean jerk signal* of accelerometer reading, body motion acceleration along z-axis, time domain</td>
	</tr>
	<tr>
	    <td>tBodyAccJerk-std()-X</td>
	    <td>18</td>		
	    <td>numeric</td>
		<td>St.Dev of jerk signal* of accelerometer reading, body motion acceleration along x-axis, time domain</td>
	</tr>
	<tr>
	    <td>tBodyAccJerk-std()-Y</td>
	    <td>19</td>		
	    <td>numeric</td>
		<td>St.Dev of jerk signal* of accelerometer reading, body motion acceleration along y-axis, time domain</td>
	</tr>
	<tr>
	    <td>tBodyAccJerk-std()-Z</td>
	    <td>20</td>		
	    <td>numeric</td>
		<td>St.Dev of jerk signal* of accelerometer reading, body motion acceleration along z-axis, time domain</td>
	</tr>
	<tr>
	    <td>tBodyGyro-mean()-X</td>
	    <td>21</td>		
	    <td>numeric</td>
		<td>Mean gyroscope reading along x-axis, time domain</td>
	</tr>
	<tr>
	    <td>tBodyGyro-mean()-Y</td>
	    <td>22</td>		
	    <td>numeric</td>
		<td>Mean gyroscope reading along y-axis, time domain</td>
	</tr>
	<tr>
	    <td>tBodyGyro-mean()-Z</td>
	    <td>23</td>		
	    <td>numeric</td>
		<td>Mean gyroscope reading along z-axis, time domain</td>
	</tr>
	<tr>
	    <td>tBodyGyro-std()-X</td>
	    <td>24</td>		
	    <td>numeric</td>
		<td>St.Dev of gyroscope reading along x-axis, time domain</td>
	</tr>
	<tr>
	    <td>tBodyGyro-std()-Y</td>
	    <td>25</td>		
	    <td>numeric</td>
		<td>St.Dev of gyroscope reading along y-axis, time domain</td>
	</tr>
	<tr>
	    <td>tBodyGyro-std()-Z</td>
	    <td>26</td>		
	    <td>numeric</td>
		<td>St.Dev of gyroscope reading along z-axis, time domain</td>
	</tr>
	<tr>
	    <td>tBodyGyroJerk-mean()-X</td>
	    <td>27</td>		
	    <td>numeric</td>
		<td>Mean jerk signal* of gyroscope reading along x-axis, time domain</td>
	</tr>
	<tr>
	    <td>tBodyGyroJerk-mean()-Y</td>
	    <td>28</td>		
	    <td>numeric</td>
		<td>Mean jerk signal* of gyroscope reading along y-axis, time domain</td>
	</tr>
	<tr>
	    <td>tBodyGyroJerk-mean()-Z</td>
	    <td>29</td>		
	    <td>numeric</td>
		<td>Mean jerk signal* of gyroscope reading along z-axis, time domain</td>
	</tr>
	<tr>
	    <td>tBodyGyroJerk-std()-X</td>
	    <td>30</td>		
	    <td>numeric</td>
		<td>St.Dev of jerk signal* of gyroscope reading along x-axis, time domain</td>
	</tr>
	<tr>
	    <td>tBodyGyroJerk-std()-Y</td>
	    <td>31</td>		
	    <td>numeric</td>
		<td>St.Dev of jerk signal* of gyroscope reading along y-axis, time domain</td>
	</tr>
	<tr>
	    <td>tBodyGyroJerk-std()-Z</td>
	    <td>32</td>		
	    <td>numeric</td>
		<td>St.Dev of jerk signal* of gyroscope reading along z-axis, time domain</td>
	</tr>
	<tr>
	    <td>tBodyAccMag-mean()</td>
	    <td>33</td>		
	    <td>numeric</td>
		<td>Mean Euclidean norm magnitude** of x-y-z variables, body motion acceleration, time domain</td>
	</tr>
	<tr>
	    <td>tBodyAccMag-std()</td>
	    <td>34</td>		
	    <td>numeric</td>
		<td>St.Dev of Euclidean norm magnitude** of x-y-z variables, body motion acceleration, time domain</td>
	</tr>
	<tr>
	    <td>tGravityAccMag-mean()</td>
	    <td>35</td>		
	    <td>numeric</td>
		<td>Mean Euclidean norm magnitude** of x-y-z variables, gravitational acceleration, time domain</td>
	</tr>
	<tr>
	    <td>tGravityAccMag-std()</td>
	    <td>36</td>		
	    <td>numeric</td>
		<td>St.Dev of Euclidean norm magnitude** of x-y-z variables, gravitational acceleration, time domain</td>
	</tr>
	<tr>
	    <td>tBodyAccJerkMag-mean()</td>
	    <td>37</td>		
	    <td>numeric</td>
		<td>Mean Euclidean norm magnitude** of x-y-z variables, body motion acceleration jerk signal*, time domain</td>
	</tr>
	<tr>
	    <td>tBodyAccJerkMag-std()</td>
	    <td>38</td>		
	    <td>numeric</td>
		<td>St.Dev of Euclidean norm magnitude** of x-y-z variables, body motion acceleration jerk signal*, time domain</td>
	</tr>
	<tr>
	    <td>tBodyGyroMag-mean()</td>
	    <td>39</td>		
	    <td>numeric</td>
		<td>Mean Euclidean norm magnitude** of x-y-z variables, gyroscope reading, time domain</td>
	</tr>
	<tr>
	    <td>tBodyGyroMag-std()</td>
	    <td>40</td>		
	    <td>numeric</td>
		<td>St.Dev of Euclidean norm magnitude** of x-y-z variables, gyroscope reading, time domain</td>
	</tr>
	<tr>
	    <td>tBodyGyroJerkMag-mean()</td>
	    <td>41</td>		
	    <td>numeric</td>
		<td>Mean Euclidean norm magnitude** of x-y-z variables, gyroscope reading jerk signal*, time domain</td>
	</tr>
	<tr>
	    <td>tBodyGyroJerkMag-std()</td>
	    <td>42</td>		
	    <td>numeric</td>
		<td>St.Dev of Euclidean norm magnitude** of x-y-z variables, gyroscope reading jerk signal*, time domain</td>
	</tr>
	<tr>
	    <td>fBodyAcc-mean()-X</td>
	    <td>43</td>		
	    <td>numeric</td>
		<td>Mean accelerometer reading, body motion acceleration along x-axis, frequency domain</td>
	</tr>
	<tr>
	    <td>fBodyAcc-mean()-Y</td>
	    <td>44</td>		
	    <td>numeric</td>
		<td>Mean accelerometer reading, body motion acceleration along y-axis, frequency domain</td>
	</tr>
	<tr>
	    <td>fBodyAcc-mean()-Z</td>
	    <td>45</td>		
	    <td>numeric</td>
		<td>Mean accelerometer reading, body motion acceleration along z-axis, frequency domain</td>
	</tr>
	<tr>
	    <td>fBodyAcc-std()-X</td>
	    <td>46</td>		
	    <td>numeric</td>
		<td>St.Dev of accelerometer reading, body motion acceleration along x-axis, frequency domain</td>
	</tr>
	<tr>
	    <td>fBodyAcc-std()-Y</td>
	    <td>47</td>		
	    <td>numeric</td>
		<td>St.Dev of accelerometer reading, body motion acceleration along y-axis, frequency domain</td>
	</tr>
	<tr>
	    <td>fBodyAcc-std()-Z</td>
	    <td>48</td>		
	    <td>numeric</td>
		<td>St.Dev of accelerometer reading, body motion acceleration along z-axis, frequency domain</td>
	</tr>
	<tr>
	    <td>fBodyAccJerk-mean()-X</td>
	    <td>49</td>		
	    <td>numeric</td>
		<td>Mean jerk signal* of accelerometer reading, body motion acceleration along x-axis, frequency domain</td>
	</tr>
	<tr>
	    <td>fBodyAccJerk-mean()-Y</td>
	    <td>50</td>		
	    <td>numeric</td>
		<td>Mean jerk signal* of accelerometer reading, body motion acceleration along y-axis, frequency domain</td>
	</tr>
	<tr>
	    <td>fBodyAccJerk-mean()-Z</td>
	    <td>51</td>		
	    <td>numeric</td>
		<td>Mean jerk signal* of accelerometer reading, body motion acceleration along z-axis, frequency domain</td>
	</tr>
	<tr>
	    <td>fBodyAccJerk-std()-X</td>
	    <td>52</td>		
	    <td>numeric</td>
		<td>St.Dev of jerk signal* of accelerometer reading, body motion acceleration along x-axis, frequency domain</td>
	</tr>
	<tr>
	    <td>fBodyAccJerk-std()-Y</td>
	    <td>53</td>		
	    <td>numeric</td>
		<td>St.Dev of jerk signal* of accelerometer reading, body motion acceleration along y-axis, frequency domain</td>
	</tr>
	<tr>
	    <td>fBodyAccJerk-std()-Z</td>
	    <td>54</td>		
	    <td>numeric</td>
		<td>St.Dev of jerk signal* of accelerometer reading, body motion acceleration along z-axis, frequency domain</td>
	</tr>
	<tr>
	    <td>fBodyGyro-mean()-X</td>
	    <td>55</td>		
	    <td>numeric</td>
		<td>Mean gyroscope reading along x-axis, frequency domain</td>
	</tr>
	<tr>
	    <td>fBodyGyro-mean()-Y</td>
	    <td>56</td>		
	    <td>numeric</td>
		<td>Mean gyroscope reading along y-axis, frequency domain</td>
	</tr>
	<tr>
	    <td>fBodyGyro-mean()-Z</td>
	    <td>57</td>		
	    <td>numeric</td>
		<td>Mean gyroscope reading along z-axis, frequency domain</td>
	</tr>
	<tr>
	    <td>fBodyGyro-std()-X</td>
	    <td>58</td>		
	    <td>numeric</td>
		<td>St.Dev of gyroscope reading along x-axis, frequency domain</td>
	</tr>
	<tr>
	    <td>fBodyGyro-std()-Y</td>
	    <td>59</td>		
	    <td>numeric</td>
		<td>St.Dev of gyroscope reading along y-axis, frequency domain</td>
	</tr>
	<tr>
	    <td>fBodyGyro-std()-Z</td>
	    <td>60</td>		
	    <td>numeric</td>
		<td>St.Dev of gyroscope reading along z-axis, frequency domain</td>
	</tr>
	<tr>
	    <td>fBodyAccMag-mean()</td>
	    <td>61</td>		
	    <td>numeric</td>
		<td>Mean Euclidean norm magnitude** of x-y-z variables, body motion acceleration, frequency domain</td>
	</tr>
	<tr>
	    <td>fBodyAccMag-std()</td>
	    <td>62</td>		
	    <td>numeric</td>
		<td>St.Dev of Euclidean norm magnitude** of x-y-z variables, body motion acceleration, frequency domain</td>
	</tr>
	<tr>
	    <td>fBodyAccJerkMag-mean()</td>
	    <td>63</td>		
	    <td>numeric</td>
		<td>Mean Euclidean norm magnitude** of x-y-z variables, body motion acceleration jerk signal*, frequency domain</td>
	</tr>
	<tr>
	    <td>fBodyAccJerkMag-std()</td>
	    <td>64</td>		
	    <td>numeric</td>
		<td>St.Dev of Euclidean norm magnitude** of x-y-z variables, body motion acceleration jerk signal*, frequency domain</td>
	</tr>
	<tr>
	    <td>fBodyBodyGyroMag-mean()</td>
	    <td>65</td>		
	    <td>numeric</td>
		<td>Mean Euclidean norm magnitude** of x-y-z variables, gyroscope reading, frequency domain</td>
	</tr>
	<tr>
	    <td>fBodyBodyGyroMag-std()</td>
	    <td>66</td>		
	    <td>numeric</td>
		<td>St.Dev of Euclidean norm magnitude** of x-y-z variables, gyroscope reading, frequency domain</td>
	</tr>
	<tr>
	    <td>fBodyBodyGyroJerkMag-mean()</td>
	    <td>67</td>		
	    <td>numeric</td>
		<td>Mean Euclidean norm magnitude** of x-y-z variables, gyroscope reading jerk signal*, frequency domain</td>
	</tr>
	<tr>
	    <td>fBodyBodyGyroJerkMag-std()</td>
	    <td>68</td>		
	    <td>numeric</td>
		<td>St.Dev of Euclidean norm magnitude** of x-y-z variables, gyroscope reading jerk signal*, frequency domain</td>
	</tr>
</table>

</body>
</html>

The following descriptions are taken directly from the 'features_info.txt' file supplied for the project

Time vs frequency domain explained: "These time domain signals (prefix 't' to denote time) were captured at a constant rate of 50 Hz. Then they were filtered using a median filter and a 3rd order low pass Butterworth filter with a corner frequency of 20 Hz to remove noise."

*"the body linear acceleration and angular velocity were derived in time to obtain Jerk signals"

**"Also the magnitude of these three-dimensional signals were calculated using the Euclidean norm"



