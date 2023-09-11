# Google-Data-Analytics-Capstone
Capstone Project for the Google Data Analytics Certificate on Coursera


Introduction :

The case study will follow the data analysis process of

Ask
Prepare
Process
Analyze
Share
Act
A Case Study Roadmap has also been provided which includes key questions, deliverables and task which I will share as we go along.

Scenario

The case study is based on a fictional company Cyclistic, a bike sharing company in Chicago. I am a junior data analyst working for Cyclistic. The director of marketing (Lily Moreno) believes the company’s future success depends on maximizing the number of annual memberships. Therefore, your team wants to understand how casual riders and annual members use Cyclistic bikes differently.

From these insights, your team will design a new marketing strategy to convert casual riders into annual members. But first, Cyclistic executives must approve your recommendations, so they must be backed up with compelling data insights and professional data visualizations

About Cyclistic

Until now, Cyclistic’s marketing strategy relied on building general awareness and appealing to broad consumer segments. One approach that helped make these things possible was the flexibility of its pricing plans: single-ride passes, full-day passes, and annual memberships. Customers who purchase single-ride or full-day passes are referred to as casual riders. Customers who purchase annual memberships are Cyclistic members.

Cyclistic’s finance analysts have concluded that annual members are much more profitable than casual riders. Although the pricing flexibility helps Cyclistic attract more customers, Moreno believes that maximizing the number of annual members will be key to future growth. Rather than creating a marketing campaign that targets all-new customers, Moreno believes there is a very good chance to convert casual riders into members. She notes that casual riders are already aware of the Cyclistic program and have chosen Cyclistic for their mobility needs.

Moreno has set a clear goal: Design marketing strategies aimed at converting casual riders into annual members. In order to do that, however, the marketing analyst team needs to better understand how annual members and casual riders differ, why casual riders would buy a membership, and how digital media could affect their marketing tactics. Moreno and her team are interested in analyzing the Cyclistic historical bike trip data to identify trends.

Phase 1 : Ask

Three questions will guide the future marketing program:

How do annual members and casual riders use Cyclistic bikes differently?
Why would casual riders buy Cyclistic annual memberships?
How can Cyclistic use digital media to influence casual riders to become members?
We have been assigned to answer question 1 and produce a report with the following deliverables:

A clear statement of the business task
A description of all data sources used
Documentation of any cleaning or manipulation of data
A summary of your analysis
Supporting visualizations and key findings
Your top three recommendations based on your analysis
The following Case Study Roadmap guiding questions, tasks and deliverables are due at this stage

Identify the business task — To discover and understand how members and casual riders utilize the bikes differently and to propose recommendations on how to convert casual riders to become members.
Identify Key Stakeholders — Lily Moreno (Manager and Director of Marketing), Cyclistic Execute Team, Cyclistic marketing analytics team
Phase 2 : Prepare

2.1 Data collection

This dataset is downloaded from Cyclistic’s historical trip data and has been made available by Motivate International Inc. under a data license agreement. The dataset consists of 12 unique CSV files according to 12 months from May 2022 to April 2023.

The following Case Study Roadmap guiding questions, tasks and deliverables are due at this stage

Where is the data located — The data is stored on my personal computer and is stored in a folder called Google Case Study 1 -> Trip Data -> CSV to provide context as to what the data is for and what format its in. I have also renamed the files by yymm for clarity.
How is the data organized — The data is located on 12 spreadsheets for each month from May 2022 to Apr 2023.
Are there issues with bias or credibility in this data? Does your data ROCCC? — There are no issues with bias or credibility as it was provided by the Cyclistic’s own data analyst team so it is reliable.
The ROCCC process

Reliable : The data is provided by the Cyclistic’s own data analyst team so it is reliable. The huge data set, around 5.85 million entries.

Original: The data is provided by the Cyclistic’s own data analyst team so it is first hand and original

Comprehensive: The dataset has quite a few columns but after examining the data. I think it could have been more detailed with information like added to it.

Current: The data set is current as I am using April 2023 data in June 2023

Cited: It is an internal data set.

4. How are you addressing licensing, privacy, security, and accessibility? — The data is open source and is provided under the license here

5. How did you verify the data’s integrity? — The spreadsheets data was verified and consistent throughout the spreadsheets. The columns also matched up.

6. How does it help you answer your question? — There is enough data there to analyze several metrics of difference between members and casual riders.

7. Are there any problems with the data? — There is missing data in the start_station_name and start_station_id columns. I think it could have been more detailed with information like indivdual user ids added to it to target casual customers who regularly use the service.

8. Deliverable: A description of all data sources used — The data sources are 12 csv files prepared by the data analytics team at Cyclistic based on 12 months of trip data from May 22 to Apr 23.

Phase 3: Process

The following Case Study Roadmap guiding questions, tasks and deliverables are due at this stage

What tools have you chosen and why — I have chosen R Studio (Desktop Version) due to the size of the datasets and ease of processing.
Have you ensured your data integrity — Yes, I have performed checks and cleaned which are detailed below
Have you documented your cleaning process — Yes documented below as well.
Deliverables — Documented cleaning process
I first added 3 new columns to the individual csv

Ride Length — Calculate the total ride length by subtracting the ended at column from the start at column
Weekday — Specified which day the trips took place. Numbered from 1 to 7 where 1 is Sunday and 7 is Saturday
Hour — Extracted the hour from the start at column to do an analysis on the number of rides per hour. This was not part of the Roadmap but I wanted to be able to access this data.
As I did these steps, I also shorted the names of the csv files to reflect the year and name only i.e. 2304,2212 etc.

3.1 Data Cleaning

For the Data Cleaning process, I will be using R Studio to combine the 12 csv files into 1 data set. I chose to use R Studio due to the file sizes of the csv files. I used the desktop version to complete my cleaning as the online version would crash frequently due to memory limitations.

First we would need to load the appropriate packages into Rstudio.

Do note that I will be using # to provide comments to the code

#Installing the packages
install.packages('tidyverse')
install.packages('lubridate')
install.packages('ggplot2')
install.packages('dplyr')

#Loading the packages
library(tidyverse)
library(lubridate)
library(ggplot2)
We now need to load the csv files into R studio

#Change the working directory
setwd("file location on PC")

#Loading datasets and filling in with "NA" to account for any missing data 
May22 <- read_csv("2205.csv", na= "")
Jun22 <- read_csv("2206.csv", na= "")
Jul22 <- read_csv("2207.csv", na= "")
Aug22 <- read_csv("2208.csv", na= "")
Sep22 <- read_csv("2209.csv", na= "")
Oct22 <- read_csv("2210.csv", na= "")
Nov22 <- read_csv("2211.csv", na= "")
Dec22 <- read_csv("2212.csv", na= "")
Jan23 <- read_csv("2301.csv", na= "")
Feb23 <- read_csv("2302.csv", na= "")
Mar23 <- read_csv("2303.csv", na= "")
Apr23 <- read_csv("2304.csv", na= "")

#Merging into 1 data set

all_trips <- bind_rows(May22,Jun22,Jul22,Aug22,Sep22,Oct22,Nov22,Dec22,Jan23,Feb23,Mar23,Apr23)

#Checking number of rows 

> rowtotal <- sum(nrow(May22),nrow(Jun22),nrow(Jul22),nrow(Aug22),nrow(Sep22),nrow(Oct22),nrow(Nov22),nrow(Dec22),nrow(Jan23),nrow(Feb23),nrow(Mar23),nrow(Apr23))
> print(rowtotal)
[1] 5859061

>  str(all_trips)
spc_tbl_ [5,859,061 × 16] (S3: spec_tbl_df/tbl_df/tbl/data.frame)
The numbers of rows match so we are sure that there is no data loss from merging the data.

We can now look at the data set as a whole to begin data cleaning, in particular all the rows with missing data

#Cleaning data I did the following to check how many NA values & incomplete records in the combined df

sum(is.na(all_trips)) - 3455662 #number of NA values
df_complete <- sum(complete.cases(all_trips)) - 4533929 #number of complete rows
df_incomplete <- sum(!complete.cases(all_trips)) - 1325132 #sum of incomplete records (rows)

#removing all NA / incomplete data
all_trips_clean <- na.omit(all_trips) 
sum(is.na(all_trips_clean))[1] 0 #check for na values
df_incomplete <- sum(!complete.cases(all_trips_clean))[1] 0 #check for incomplete rows.

glimpse(all_trips_clean)
Rows: 4,533,929
Columns: 16
Our original data set all_trips had 5,859,061 rows while our cleaned data set all_trips_clean has 4,533,929. We removed 1,325,132 rows with incomplete data which is 22.6% of our original data set. I debated whether to keep the incomplete data in as it is a significant chunk of our dataset but using a sample size calculator with Confidence level set to 99.99% and a margin of error at 1% the min sample size was 37,588 so I decided to remove them.

As we have previously checked the spreadsheets for duplicated Ride ID values and found none. We do not need to check again.

At this point we were instructed by the case study guide to remove the lat and long. However, I will be keeping these as I would like to do a heat map Visualization in Tableau later on.

We are also tasked with changing some of the data formats and creating new data columns to aggregate data by month , day & year. We also needed to create a ride length column

#Create new date,day, month , year, day of the week columns
all_trips_clean$date <- as.Date(all_trips_clean$started_at)
all_trips_clean$month <- format(as.Date(all_trips_clean$date), "%m")
all_trips_clean$day <- format(as.Date(all_trips_clean$date), "%d")
all_trips_clean$year <- format(as.Date(all_trips_clean$date), "%Y")
all_trips_clean$day_of_week <- format(as.Date(all_trips_clean$date), "%A")

#Creating a ride length calculation

all_trips_clean$ride_length <- difftime(all_trips_clean$ended_at,all_trips_clean$started_at)

#Converting to numeric 
all_trips$ride_length <- as.numeric(as.character(all_trips$ride_length))

#Removing rows that had negative ride lengths
all_trips_clean_v2 <- filter(all_trips_clean$ride_length<0))
Phase 4: Analyze

Now that the data has been cleaned we can do some descriptive analysis on the cleaned data. These were provided by the Case Study

#Ride Length analysis
Min.   1st Qu.    Median      Mean   3rd Qu.      Max. 
        0         0         0    148675         0 725760000

# By member type

#Mean

all_trips_clean_v4$member_casual all_trips_clean_v4$ride_length
1                           casual                      250475.94
2                           member                       82208.89

#Median

all_trips_clean_v4$member_casual all_trips_clean_v4$ride_length
1                           casual                              0
2                           member                              0

#Min

 all_trips_clean_v4$member_casual all_trips_clean_v4$ride_length
1                           casual                              0
2                           member                              0

#Max
  all_trips_clean_v4$member_casual all_trips_clean_v4$ride_length
1                           casual                      725760000
2                           member                       31622400

#Mean seperate by day of the week
all_trips_clean_v4$member_casual all_trips_clean_v4$day_of_week all_trips_clean_v4$ride_length
1                            casual                         Sunday                      268204.93
2                            member                         Sunday                       90085.83
3                            casual                         Monday                      263536.54
4                            member                         Monday                       86515.58
5                            casual                        Tuesday                      251512.56
6                            member                        Tuesday                       83402.02
7                            casual                      Wednesday                      207870.16
8                            member                      Wednesday                       72686.36
9                            casual                       Thursday                      244574.38
10                           member                       Thursday                       77857.94
11                           casual                         Friday                      256312.85
12                           member                         Friday                       80954.86
13                           casual                       Saturday                      257490.12
14                           member                       Saturday                       84036.12
At this point I stopped and exported the data for further visualization in Tableau.

#Export to CSV File
write.csv(all_trips_clean_v4, "all_trips_clean_v4.csv", row.names=FALSE)
The following Case Study Roadmap guiding questions, tasks and deliverables are due at this stage

How should you organize your data to perform analysis on it? — The data has been organized using the column headers in the CSVs
How should you organize your data to perform analysis on it? — Yes, we have checked the column data and converted to proper formatting
Deliverable — Data Analysis Summary
Phase 5: Share

Visualizations and Findings from Tableau

First attribute I looked at a basic breakdown of members and casual riders to see what % of overall riders are we trying to convert to members. 60.5% (2,742,667) of the 4,533,335 riders are members.

2. I then looked at bike preferences to see if there were any clear preferences we could use. It seems that casual members are the only ones that used docked bike but classic bikes are far and away the favourite choice for both members and casual. We could further examine why only casuals use docked bikes and why classic bikes are so heavily used.


3. Ride Statistics by Day — I combined a few observations into 1 data viz.

3.1 The daily amount of rides doesnt vary much during the week and members account for more rides than casual do.

3.2 The amount of rides peaks around 7/8 am in the morning and then at 4/5/6 pm during the evening. This would suggest that members are regularly using the bikes to get to and from work as part of their daily commute

3.3 Casual riders have way longer ride lengths then member riders. Almost 3x as long. This could mean that casual riders are using the bikes for more leisurely activities like sightseeing.


4. Ride statistics by month — I wanted to find out which months was the service used the most and did average ride time fluctuate as well.

4.1 We can see that from April to August there is a significant upward trend in usage. This would be during the spring and summer seasons, which would eb the most popular time to ride bikes. The downward trend from September is also due to the Autumn and winter seasons approaching.

An interesting observation is that casual riders have greater lows and highs compared to the members. One possible reason for the greatest increase from Apr to June is that it is peak season for Tourists to come to Chicago. However, correlation is not causation and more detailed investigation needs to be done.


5. Top 5 starting and ending stations — The top 5 starting and ending locations are all located in the Central Business District of Chicago and located around Navy Pier and Millennium park which are both major tourist destinations. There are also many tourist destinations in and around that area.


Phase 6 : Act

After having gone through the analysis and the findings from the visualizations, I would like to share my hypothesis and my top recommendations.

Hypothesis

Members are locals who use the bike share service to get to and from work on a daily basis based on high usage times, steady ridership on weekly and a base of 100k+ rides a month throughout the year.
Casuals are likely tourists who come to use the bikes during their holiday and will rent the bikes for longer periods of time.
It also seems like the single-ride passes do have some loopholes to exploit as the average ride length for casual users is 200k seconds which is around 2 days.
Recommendations

To recap the 3 business questions asked at the beginning of the case study

How do annual members and casual riders use Cyclistic bikes differently?
Why would casual riders buy Cyclistic annual memberships?
How can Cyclistic use digital media to influence casual riders to become members?
To answer 1.

Members use the bikes consistently with peak periods at 8/9am and 4/5/6 pm during the day. This does coincide with peak traffic to and from work.
Members use bikes on a much shorter average ride length than casual riders.
Members only use classic and electric bikes while casual riders also use docked bikes.
We were also tasked with the overall objective of designing marketing strategies aimed at converting casual riders into annual members.

These are some suggestions for the marketing strategies

Concentrate/Start marketing during the peak months of the year, this would be the period between April to August. This period has the highest increase in casual users.
With the top 5 stations all located around the CBD/Tourist areas, we could localize a unique discount to those stations/locations.
Provide discounts to upgrade to an annual membership for existing casual users
Other suggestions

Limit ride legnth on single trips as the average trip is 2 days long or introduce late return penalties beyond a certain time frame
Have strategic pricing on single trips, we have no information on prices so this is harder to propose.
Priority usage for bikes during peak hours for annual members.
Consider introducing a monthly pass for tourists during the peak months
Tie up with tourist attractions for annual members.
Personal Learning Points

Should relook at the ride length column. The data doesnt make sense as the Max Ride Length was 725,760,000 seconds which is 23 years!
Having to redo the Process and Analyze portions incurred alot of time but the insights from keeping some of the data we were told to remove was invaluable.
More indepth study and use of R and Tableau is needed.
Google Data Analytics
R
Tableau
Data Analysis
