### Required packages

    library("ggplot2")
    library("dplyr")
    library("lattice")
    library("plyr")

### Loading and pre-processing the data

###### *Data examination can be made with summary(), str(), dim(), columns(), head(), tail(), dput() and View().*

    setwd("C:/Users/victo/Desktop/COURSERA/2020 Data Science Specialization/05. Reproducible Research/Course Project 1")
    unzip("activity.zip")
    # Loading data
    originalDF <- read.csv("activity.csv", sep = ",", header=TRUE)
    str(originalDF)

    ## 'data.frame':    17568 obs. of  3 variables:
    ##  $ steps   : int  NA NA NA NA NA NA NA NA NA NA ...
    ##  $ date    : Factor w/ 61 levels "2012-10-01","2012-10-02",..: 1 1 1 1 1 1 1 1 1 1 ...
    ##  $ interval: int  0 5 10 15 20 25 30 35 40 45 ...

    # Add hour and minute
    originalDF <- mutate(originalDF, hour = interval %/% 100, minute = interval %% 100)
    # Data set ignoring the missing values (NA)
    tidy_originalDF <- na.omit(originalDF) 
    head(tidy_originalDF) 

    ##     steps       date interval hour minute
    ## 289     0 2012-10-02        0    0      0
    ## 290     0 2012-10-02        5    0      5
    ## 291     0 2012-10-02       10    0     10
    ## 292     0 2012-10-02       15    0     15
    ## 293     0 2012-10-02       20    0     20
    ## 294     0 2012-10-02       25    0     25

### **1. What is mean total number of steps taken per day?**

#### **1.** Calculate total number of steps taken per day.

    # Group the number of steps by day
    agg_ByDate <- aggregate(steps~date, tidy_originalDF, sum, na.rm=TRUE)
    # Change variable names
    names(agg_ByDate) <- c("date","total_steps")
    # check if changes where made
    head(agg_ByDate)

    ##         date total_steps
    ## 1 2012-10-02         126
    ## 2 2012-10-03       11352
    ## 3 2012-10-04       12116
    ## 4 2012-10-05       13294
    ## 5 2012-10-06       15420
    ## 6 2012-10-07       11015

#### **2.** Plot a histogram of the total number of steps taken each day.

    ggplot(agg_ByDate, aes(total_steps, fill=..count.., col=..count..)) +
            geom_histogram(bins = 8, alpha = 0.6, position = "identity", 
                           binwidth = 5000, boundary= 0) + # histogram with boundary (starting with 0) 
            guides(fill=FALSE, col=FALSE) + # Remove legends of ..count..
            ggtitle("Total Number of Steps taken each Day (October - November 2012)") +
            theme(plot.title = element_text(face = "bold", size = 11, hjust = 0.5)) +
            xlab("Total Steps taken each Day") + ylab("Frequency") + 
            scale_x_continuous(breaks=seq(from=0, to=25000, by=5000)) + # Adjusting the scale of the histogram
            scale_y_continuous(breaks=seq(from=0, to=28, by=4)) 

![](RepData_PeerAssignment1_files/figure-markdown_strict/plot%20total%20steps%20per%20day-1.png)

#### **3.** Calculate and report the mean and median of the total number of steps taken per day:

    summary(agg_ByDate$total_steps)

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ##      41    8841   10765   10766   13294   21194

###### *As we can see, the mean of steps taken per day is 10766, while the median is 10765.*

### **2. Which is the average daily activity pattern?**

#### **1.** Time series plot (i.e. type="l") of the 5-minute interval (x-axis) and the average number of steps taken, averaged across all day (y-axis).

    # Create a table with steps per time (from the data frame without NAs)
    agg_ByTime <- aggregate(steps~interval, tidy_originalDF, mean, na.rm=TRUE) 
    # Change variable names
    names(agg_ByTime) <- c("interval","mean_steps")
    head(agg_ByTime)

    ##   interval mean_steps
    ## 1        0  1.7169811
    ## 2        5  0.3396226
    ## 3       10  0.1320755
    ## 4       15  0.1509434
    ## 5       20  0.0754717
    ## 6       25  2.0943396

    # Plot the time series
    ggplot(agg_ByTime, aes(interval, mean_steps)) + 
            geom_line(col="darkblue") +
            ggtitle("Average Number of Steps taken per a 5-minute Interval, averaged across all days") + 
            xlab("Intervals") + ylab("Average Number of Steps") + 
            theme(plot.title = element_text(face="bold", size = 11, hjust = 0.5)) +
            scale_x_continuous(breaks=seq(from=0, to=2400, by=500)) + # Adjusting the scale
            scale_y_continuous(breaks=seq(from=0, to=250, by=50)) 

![](RepData_PeerAssignment1_files/figure-markdown_strict/average%20daily%20activity-1.png)

#### **2.** Which 5-minute interval, on average across all the days in the dataset, contains the maximum number of steps?

    # Interval that contains the maximum average number of steps
    agg_ByTime[which.max(agg_ByTime$mean_steps), ]$interval 

    ## [1] 835

    agg_ByTime[which.max(agg_ByTime$mean_steps), ]$mean_steps # additional information

    ## [1] 206.1698

    summary(agg_ByTime$mean_steps) # additional information

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ##   0.000   2.486  34.113  37.383  52.835 206.170

###### *The plot shows that the interval 835 is the larger interval of the day with 206 steps. That means that the maximum number of steps occurs at 8:35 AM*

###### *If we compare it with the mean of 37 steps, it is about 22.5 times larger*

### **3. Imputing missing values**

#### **1.** Calculate and report the total number of missing values in the dataset

###### *To calculate the total number of NAs, the "originalDF" data frame has been used.*

    colSums(is.na(originalDF)) # Number of NAs in original data set

    ##    steps     date interval     hour   minute 
    ##     2304        0        0        0        0

    mean(is.na(originalDF$steps)) # Proportion of the number of NAs

    ## [1] 0.1311475

###### *There is a total of 2304 of missing values (NAs) in the variable "steps" representing a 13% of the total data frame which is statistically acceptable.*

#### **2.** Devising a strategy for filling in all of the missing values in the dataset, and create

###### *The strategy used to filling in all missing values in the new data set is the mean instead of the missing values*

#### **3.** Creating a new dataset that is equal to the original dataset but with the missing data filled in.

    # Create a new dataset equal to the "originalDF"
    newDF <- originalDF 
    # Create a new column "imputed_steps" equal to the "steps" column
    newDF$imputed_steps <- newDF$steps
    # Fill the NAs values by using the mean
    newDF$imputed_steps[is.na(newDF$steps)] <- mean(newDF$imputed_steps, na.rm = T)
    # check if there are any missing values in the "imputed_steps"
    colSums(is.na(newDF))

    ##         steps          date      interval          hour        minute 
    ##          2304             0             0             0             0 
    ## imputed_steps 
    ##             0

    # check the newDF
    str(newDF)

    ## 'data.frame':    17568 obs. of  6 variables:
    ##  $ steps        : int  NA NA NA NA NA NA NA NA NA NA ...
    ##  $ date         : Factor w/ 61 levels "2012-10-01","2012-10-02",..: 1 1 1 1 1 1 1 1 1 1 ...
    ##  $ interval     : int  0 5 10 15 20 25 30 35 40 45 ...
    ##  $ hour         : num  0 0 0 0 0 0 0 0 0 0 ...
    ##  $ minute       : num  0 5 10 15 20 25 30 35 40 45 ...
    ##  $ imputed_steps: num  37.4 37.4 37.4 37.4 37.4 ...

    head(newDF) 

    ##   steps       date interval hour minute imputed_steps
    ## 1    NA 2012-10-01        0    0      0       37.3826
    ## 2    NA 2012-10-01        5    0      5       37.3826
    ## 3    NA 2012-10-01       10    0     10       37.3826
    ## 4    NA 2012-10-01       15    0     15       37.3826
    ## 5    NA 2012-10-01       20    0     20       37.3826
    ## 6    NA 2012-10-01       25    0     25       37.3826

#### **4.** Make a histogram of the total number of steps taken each day. Calculate and report the mean and median total number of steps taken per day. Do these values differ from the estimates from the first part of the assignment? What is the impact of imputing missing data on the estimates of the total daily number of steps?

    # Group the number of imputed_steps by day
    agg_ByDate_imputed <- aggregate(imputed_steps~date, newDF, sum)
    # Change variable names
    names(agg_ByDate_imputed) <- c("date","total_imputed")
    # check if changes where made
    head(agg_ByDate_imputed)

    ##         date total_imputed
    ## 1 2012-10-01      10766.19
    ## 2 2012-10-02        126.00
    ## 3 2012-10-03      11352.00
    ## 4 2012-10-04      12116.00
    ## 5 2012-10-05      13294.00
    ## 6 2012-10-06      15420.00

    # Plot the histogram
    ggplot(agg_ByDate_imputed, aes(total_imputed, fill=..count.., col=..count..)) +
            geom_histogram(bins = 8, alpha = 0.6, position = "identity", 
                           binwidth = 5000, boundary= 0) + # histogram with boundary (starting with 0) 
            guides(fill=FALSE, col=FALSE) + # Remove legends of ..count..
            ggtitle("Total Steps taken each Day - with imputed NA Values (October - November 2012)") +
            theme(plot.title = element_text(face = "bold", size = 11, hjust = 0.5)) +
            xlab("Total Steps taken each Day") + ylab("Frequency") + 
            scale_x_continuous(breaks=seq(from=0, to=25000, by=5000)) + # Adjusting the scale of the histogram
            scale_y_continuous(breaks=seq(from=0, to=40, by=6)) 

![](RepData_PeerAssignment1_files/figure-markdown_strict/plot%20total%20imputed_steps-1.png)

    summary(agg_ByDate_imputed$total_imputed)

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ##      41    9819   10766   10766   12811   21194

###### *By imputing the NA value\#s by the mean has caused the mean and median to be different in both histograms.*

###### *As it can be seen, imputing missing data on the estimates of the total daily number of steps changes the median and the distribution*

###### *Based on the method used for filling in missing values, we can get different mean and median values. The histogram can also be different based on the strategy we used to fill in the missing values.*

###### *In that case, by imputing missing data by using the mean, we can see that the mean and the median are equal (10766.19 daily steps) which inform us that the histogram has a symmetric distribution. On the other hand, on the first estimate the mean and the median were slighty different (10766.19 and 10765 respectively).*

### **4. Are there differences in activity patterns between weekdays and weekends?**

#### **1.** Create a new factor variable in the dataset with two levels - "weekday" and "weekend" indicating whether a given date is a weekday or weekend day.

    # Create a new column with the name of the day
    newDF$week_day <- weekdays(as.Date(newDF$date))
    head(newDF)

    ##   steps       date interval hour minute imputed_steps week_day
    ## 1    NA 2012-10-01        0    0      0       37.3826  dilluns
    ## 2    NA 2012-10-01        5    0      5       37.3826  dilluns
    ## 3    NA 2012-10-01       10    0     10       37.3826  dilluns
    ## 4    NA 2012-10-01       15    0     15       37.3826  dilluns
    ## 5    NA 2012-10-01       20    0     20       37.3826  dilluns
    ## 6    NA 2012-10-01       25    0     25       37.3826  dilluns

    # Create a new column with the category name 
    newDF$day_category <- ifelse(newDF$week_day %in% c("dissabte", "diumenge"), "Weekend", "Weekday")
    # convert column to factor
    newDF$day_category <- factor(newDF$day_category)
    head(newDF)

    ##   steps       date interval hour minute imputed_steps week_day day_category
    ## 1    NA 2012-10-01        0    0      0       37.3826  dilluns      Weekday
    ## 2    NA 2012-10-01        5    0      5       37.3826  dilluns      Weekday
    ## 3    NA 2012-10-01       10    0     10       37.3826  dilluns      Weekday
    ## 4    NA 2012-10-01       15    0     15       37.3826  dilluns      Weekday
    ## 5    NA 2012-10-01       20    0     20       37.3826  dilluns      Weekday
    ## 6    NA 2012-10-01       25    0     25       37.3826  dilluns      Weekday

    # Summarize data by "interval" and type of the "day_category"
    agg_ByInterval <- ddply(newDF, ~interval+day_category, summarise, mean=mean(imputed_steps))
    head(agg_ByInterval)

    ##   interval day_category     mean
    ## 1        0      Weekday 7.006569
    ## 2        0      Weekend 4.672825
    ## 3        5      Weekday 5.384347
    ## 4        5      Weekend 4.672825
    ## 5       10      Weekday 5.139902
    ## 6       10      Weekend 4.672825

    # Plot data in a panel plot
    xyplot(mean~interval|day_category, data = agg_ByInterval, type = "l", layout=c(1,2), 
           main="Average Steps per Interval Based on Type of Day category", 
           ylab="Average Number of Steps", xlab="Interval")

![](RepData_PeerAssignment1_files/figure-markdown_strict/weekday%20and%20weekend-1.png)
