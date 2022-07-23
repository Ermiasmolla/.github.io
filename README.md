**Cyclistic Bike-Share: Case Study**

*This R Markdown document is created as a capstone project for the Google Data Analytics Professional Certificate* *on Coursera .*

**Introduction and Scenario**

I am a junior data analyst working in the marketing analyst team at Cyclistic, a bike-share company in Chicago. The director of marketing believes the company's future success depends on maximizing the number of annual memberships. Therefore, my team wants to understand how casual riders and annual members use Cyclistic bikes differently. From these insights, my team will design a new marketing strategy to convert casual riders into annual members. But first, Cyclistic executives must approve your recommendations, so they must be backed up with compelling data insights and professional data visualizations.

In this project I will be using Many of the tools introduced to me in the Google Data Analytics Course including Excel, SQL, R Studio and Tableau.

**Background**

Cyclistic launched in 2016 as a bike-share service. Since then, the program has grown to a fleet of 5,824 bicycles that are geotracked and locked into a network of 692 stations across Chicago. The bikes can be unlocked from one station and returned to any other station in the system anytime.

There are Members and Casual Riders. Cyclistic's finance analysts have concluded that annual members are much more profitable than casual riders. Cyclistic's believes that maximizing the number of annual members will be key to future growth.

This project uses the data analysis process: **ask, prepare, process, analyze, share, and act**.

**Ask**

There are Three questions that will guide the future marketing program:

1\. How do annual members and casual riders use Cyclistic bikes differently?

2\. Why would casual riders buy Cyclistic annual memberships?

3\. How can Cyclistic use digital media to influence casual riders to become members?

The director of marketing, Lily Moreno, has assigned me the first question to answer: **How do annual members and casual riders use Cyclistic bikes differently?**

**The Business Task**

The business task is to identify the key differences in usage between members and casual riders in order turn our Casual riders into Member riders.

**Stakeholders:**

The director of marketing

Cyclistic Executive team

Data marketing Analytics team

Cyclistic

**Prepare**

The data used is Cyclistic internal data from June 2021- May 2022. The data is available at this [link](https://divvy-tripdata.s3.amazonaws.com/index.html) under this [license](https://www.divvybikes.com/data-license-agreement).

The data used was 12 CSV files on for each month within the last year, with 13 columns and more than 5,800,000 rows.

Our data integrity will be assessed by using ROCCC method. The data needs to be **R**eliable it was be cleaned in Microsoft Excel. The data is **O**riginal because it comes from Motivate International Inc which operates Chicago's Bike sharing service. It is also **C**omprehensive containing many datapoints from start time to start station and other datapoints that are integral to the analysis. The data used is from the most **C**urrent 12-month period and it is **C**ited under a Data license agreement.

**Process**

I processed the data by downloading all 12 of the previous Months CSV Files.

{r setup, include=FALSE} \# Load packages in R library(readr) library(tidyverse) library(dplyr) library(skimr) Changelog \<- read_csv("Cyclistic Ride/Change log.csv")

![Change_log](https://github.com/Ermiasmolla/.github.io/blob/main/Visualizations/Change%20Log.png)
![new](https://github.com/Ermiasmolla/.github.io/blob/main/Change%20log.csv)

 

Within the change log I detail the steps I took in order to clean and mutate the data, including:

·       Adding a ride length column

·       Changing the formatting of that column to calculate duration

·       Adding a numerical column to pull the day of the week from the start date column.

·       Adding another column to change that numerical value into a day (i.e. 2=Monday) for clearer analysis

·       Removing rows where start and end points were not included.

·       Removing rows where ride time was less than a minute or more than 24 hours.

·       Removing data where the ride_column_id was a duplicated numerical value.

·        

Once this was complete or data went from about 5.8 million rows to 4.6 million rows. The cleaned data now represents 78.53% percent of the original data.

**Analyze**

To analyze this data, I mostly used Tableau to visualize the data in a comprehensible. I also used SQL and R to aggregate and summarize my findings with correlated data.

 

![](file:///C:/Users/molla/AppData/Local/Temp/msohtmlclip1/01/clip_image004.jpg)

R Mean and Median

Casual riders are riding for longer periods of time, on average more than double the time of Members.

![](file:///C:/Users/molla/AppData/Local/Temp/msohtmlclip1/01/clip_image006.jpg)

Both Casual and Member riders have significant lows in the Winter Season.\

Casual Riders have a wider range from Highest use to lowest use.**![](file:///C:/Users/molla/AppData/Local/Temp/msohtmlclip1/01/clip_image008.jpg)**Member Riders have peaks at 8 A.M. and 5 P.M. correlating with work shifts. Casual Riders have A gradual increase until Peak rides at 5 P.M.**![](file:///C:/Users/molla/AppData/Local/Temp/msohtmlclip1/01/clip_image010.jpg)**Casual riders have a wide range of riders per day which peak on Weekends Members are steady throughout the Week with slight dips on Weekends**![](file:///C:/Users/molla/AppData/Local/Temp/msohtmlclip1/01/clip_image012.jpg)**

Both Casual and Member riders prefer the Classic bike over the Electric bike. Docked bike were another option but were only used for about 270,000 rides., while second the second-best performing bike was the electric bike at a total of about 1,150,000 rides in the same period. Classic Bikes were used for over 3,000,000 rides

![](file:///C:/Users/molla/AppData/Local/Temp/msohtmlclip1/01/clip_image014.png)

Sql top 5 stations

Casual: More likely to use bikes near lake Michigan and other tourist hotspots with more rides on weekends indicating people are using the bike for leisure. Members: More likely to use in the downtown area and on weekdays, indicating these users are commuters to the city for work.

**Share**

Microsoft PowerPoint is used for data visualization and presenting key insights. - Click [here](https://github.com/skramazan/GDA_Capstone_Project_Cyclistic_Bike-share/tree/main/03.%20Presentation) to download the presentation.

**Act**

After analizing, we reached to the following conclusion: - Casual riders take less number of rides but for longer durations. - Casual Riders are most active on weekends, and the months of June and July. - Casual riders mostly use bikes for recreational purposes.

Here are my top 3 recommendations based on above key findings: 1. Design riding packages by 0keeping recreational activities, weekend contests, and summer events in mind and offer special discounts and coupons on such events to encourage casual riders get annual membership.

2.  

3.  Design seasonal packages, It allows flexibility and encourages casual riders to get membership for specific periods if they are not willing to pay for annual subscription.

4.  

5.  Effective and efficient promotions by targeting casual riders at the busiest times and stations:

    -   

    -   Days: Weekends

    -   

    -   Months: February, June, and July

    -   

    -   Stations: Streeter Dr & Grand Ave, Lake Shore Dr & Monroe St, Millennium Park

    -   

6.  

***Thanks for reading and Happy Analyzing!*** :smiley: :bar_chart:
