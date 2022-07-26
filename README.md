**Cyclistic Bike-Share: Case Study**

*This R Markdown document is created as a capstone project for the Google Data Analytics Professional Certificate* *on Coursera .*

**Introduction and Scenario**

I am a junior data analyst working in the marketing analyst team at Cyclistic, a bike-share company in Chicago. The director of marketing believes the company's future success depends on maximizing the number of annual memberships. Therefore, my team wants to understand how casual riders and annual members use Cyclistic bikes differently. From these insights, my team will design a new marketing strategy to convert casual riders into annual members. But first, Cyclistic executives must approve my recommendations, so they must be backed up with compelling data insights and professional data visualizations.

In this project I will be using many of the tools introduced to me in the Google Data Analytics Course including Excel, SQL, R Studio and Tableau.

**Background**

Cyclistic launched in 2016 as a bike-share service. Since then, the program has grown to a fleet of 5,824 bicycles that are geotracked and locked into a network of 692 stations across Chicago. The bikes can be unlocked from one station and returned to any other station in the system anytime.

There are Members and Casual Riders. Cyclistic's finance analysts have concluded that annual members are much more profitable than casual riders. Cyclistic's believes that maximizing the number of annual members will be key to future growth.

This project uses the data analysis process: **ask, prepare, process, analyze, share, and act**.

**Ask**

There are Three questions that will guide the future marketing program:

1.  How do annual members and casual riders use Cyclistic bikes differently?

2.  Why would casual riders buy Cyclistic annual memberships?

3.  How can Cyclistic use digital media to influence casual riders to become members?

The director of marketing, Lily Moreno, has assigned me the first question to answer: **How do annual members and casual riders use Cyclistic bikes differently?**

*The Business Task*

The business task is to identify the key differences in usage between members and casual riders in order turn our Casual riders into Member riders.

**Stakeholders**

The director of marketing

Cyclistic Executive team

Data marketing Analytics team

Cyclistic

**Prepare**

The data used is Cyclistic internal data from June 2021- May 2022. The data is available at this [link](https://divvy-tripdata.s3.amazonaws.com/index.html) under this [license](https://www.divvybikes.com/data-license-agreement).

I downloaded 12 CSV files, one for each month within the last year, with 13 columns and more than 5,800,000 rows.

Our data integrity will be assessed by using the ROCCC method. The data needs to be **R**eliable, it was be cleaned and manipulated using Microsoft Excel. The data is **O**riginal because it comes from Motivate International Inc which operates Chicago's Bike sharing service. It is also **C**omprehensive containing many data-points from start time to start station and other data-points that are integral to the analysis. The data used is from the most **C**urrent 12-month period and it is **C**ited under a Data license agreement.

**Process**

I processed the data in Excel by downloading, cleaning, manipulating and combining all 12 of the previous Months CSV Files. Below is a change log of the steps I took in Excel

![Change_log](https://github.com/Ermiasmolla/.github.io/blob/main/Visualizations/Change%20Log.png)

Within the change log I detail the steps I took in order to clean and mutate the data, including:

·       Adding a ride_length column

·       Changing the formatting of that column to calculate duration

·       Adding a numerical column to pull the day of the week from the start date column.

·       Adding another column to change that numerical value into a day (i.e. 2=Monday) for clearer analysis

·       Removing rows where start and end points were not included.

·       Removing rows where ride time was less than a minute or more than 24 hours.

·       Removing data where the ride_column_id was a duplicated numerical value.

Once this was complete our data went from about 5.8 million rows to 4.6 million rows. The cleaned data now represents 78.53% percent of the original data.

**Analyze**

To analyze this data, I mostly used Tableau to visualize the data in a comprehensible. I also used SQL and R to aggregate and summarize my findings with correlated data.

![Ride_Length](https://github.com/Ermiasmolla/.github.io/blob/main/Visualizations/Rides%20by%20Ride%20Length.png)

```{r}
install.packages("tidyverse")

library(readr)

library(tidyverse)

library(dplyr)

library(skimr)

june_2021 <- read_csv("Cyclistic Ride/CSV/202106-divvy-tripdata.csv") july_2021 <- read_csv("Cyclistic Ride/CSV/202107-divvy-tripdata.csv") august_2021 <- read_csv("Cyclistic Ride/CSV/202108-divvy-tripdata.csv") september_2021 <- read_csv("Cyclistic Ride/CSV/202109-divvy-tripdata.csv") october_2021 <- read_csv("Cyclistic Ride/CSV/202110-divvy-tripdata.csv") november_2021 <- read_csv("Cyclistic Ride/CSV/202111-divvy-tripdata.csv") december_2021 <- read_csv("Cyclistic Ride/CSV/202112-divvy-tripdata.csv") january_2022 <- read_csv("Cyclistic Ride/CSV/202201-divvy-tripdata.csv") february_2022 <- read_csv("Cyclistic Ride/CSV/202202-divvy-tripdata.csv") march_2022 <- read_csv("Cyclistic Ride/CSV/202203-divvy-tripdata.csv") april_2022 <- read_csv("Cyclistic Ride/CSV/202204-divvy-tripdata.csv") may_2022 <- read_csv("Cyclistic Ride/CSV/202205-divvy-tripdata.csv") fullset <- rbind(june_2021, july_2021,august_2021,september_2021,october_2021, november_2021,december_2021,january_2022,february_2022, march_2022,april_2022,may_2022)
```

Using R to calculate Mean and Median

```{r}
fullset %>% filter(member_casual=='casual' | member_casual == 'member') %>% group_by(member_casual) %>% summarise(mean=mean(ride_length))
```
![Mean](https://github.com/Ermiasmolla/.github.io/blob/main/Visualizations/Mean.PNG)

```{r}
fullset %>% filter(member_casual=='casual' | member_casual == 'member') %>% group_by(member_casual) %>% summarise(median=median(ride_length))
```
![Median](https://github.com/Ermiasmolla/.github.io/blob/main/Visualizations/Median.png)

Casual riders are riding for longer periods of time, with an average more than double the time of Members.

![Ride_By_Month](https://github.com/Ermiasmolla/.github.io/blob/main/Visualizations/Rides%20by%20Month.png)

Both Casual and Member riders have significant lows in the winter season. Casual Riders have a wider range from highest use to lowest

![Ride_By_Hour](https://github.com/Ermiasmolla/.github.io/blob/main/Visualizations/Rides%20by%20Hour.png)

Member Riders have peaks at 8 A.M. and 5 P.M. correlating with work shifts. Casual Riders have a gradual increase until peak rides at 5 P.M.

![Ride_By_DOW](https://github.com/Ermiasmolla/.github.io/blob/main/Visualizations/Rides%20by%20Day%20of%20Week.png)

Casual riders have a wide range of riders per day which peak on weekends, members are steady throughout the Week with slight dips on weekends

![Ride_By_Bike_type](https://github.com/Ermiasmolla/.github.io/blob/main/Visualizations/Rides%20by%20Bike%20type.png)

Both Casual and Member riders prefer the Classic bike over the Electric bike. Docked bike were another option but were only used for about 270,000 rides., while second the second-best performing bike was the electric bike at a total of about 1,150,000 rides in the same period. Classic Bikes were used for over 3,000,000 rides

![Density](https://github.com/Ermiasmolla/.github.io/blob/main/Visualizations/Density.png)

In this part of the analysis I also used PGAdmin to run SQL queries to find the top 5 stations for Members as well as Casual riders.

First I created the table

```{sql connection=}
CREATE TABLE public.June_2021
(    
    ride_id VARCHAR PRIMARY KEY,   
    rideable_type text,
    started_at TIMESTAMP,
    ended_at TIMESTAMP,
	  ride_length TIME,   
    day_of_week smallint,
    day_of_week_text text,
    start_station_name VARCHAR,
  	start_station_id VARCHAR,   
    end_station_name VARCHAR,
    end_station_id VARCHAR,
    start_lat double precision,
	  start_lng double precision,   
    end_lat double precision,
    end_lng double precision,
    member_casual text
)
```

Then I joined the tables to create a table called "All_data""

```{sql connection=}
SELECT  distinct (start_station_name), count (start_station_name)
FROM
	(SELECT 
        *
    FROM
        june_2021
UNION
    SELECT
        *
    FROM
        july_2021
UNION
    SELECT
        *
    FROM
        august_2021
UNION
	SELECT 
        *
    FROM
        september_2021
UNION
    SELECT
        *
    FROM
        october_2021
UNION
    SELECT
        *
    FROM
        november_2021
UNION
	SELECT 
        *
    FROM
        december_2021
UNION
    SELECT
        *
    FROM
        january_2022
UNION
    SELECT
        *
    FROM
        february_2022
UNION
	SELECT 
        *
    FROM
        march_2022
UNION
    SELECT
        *
    FROM
        april_2022
UNION
    SELECT
        *
    FROM
        may_2022) all_data
		where member_casual = 'member'
		group by distinct (start_station_name)
		order by count (start_station_name) Desc
		Limit 5

```

![Member Stations](https://github.com/Ermiasmolla/.github.io/blob/main/Visualizations/Member%20Stations.PNG)

```{sql connection=}
SELECT  distinct (start_station_name), count (start_station_name)
FROM
	(SELECT 
        *
    FROM
        june_2021
UNION
    SELECT
        *
    FROM
        july_2021
UNION
    SELECT
        *
    FROM
        august_2021
UNION
	SELECT 
        *
    FROM
        september_2021
UNION
    SELECT
        *
    FROM
        october_2021
UNION
    SELECT
        *
    FROM
        november_2021
UNION
	SELECT 
        *
    FROM
        december_2021
UNION
    SELECT
        *
    FROM
        january_2022
UNION
    SELECT
        *
    FROM
        february_2022
UNION
	SELECT 
        *
    FROM
        march_2022
UNION
    SELECT
        *
    FROM
        april_2022
UNION
    SELECT
        *
    FROM
        may_2022) all_data
		where member_casual = 'casual'
		group by distinct (start_station_name)
		order by count (start_station_name) Desc
		Limit 5

```

![Casual Stations](https://github.com/Ermiasmolla/.github.io/blob/main/Visualizations/Casual%20Stations.PNG)

Casual: More likely to use bikes near lake Michigan and other tourist hot spots with more rides on weekends indicating people are using the bikes for leisure.

Members: More likely to use in the downtown area and on weekdays, indicating these users are commuters to the city for work.

**Share**

I used PowerPoint to share the key findings and recommendations click [here](https://github.com/Ermiasmolla/.github.io/blob/main/Cyclistic%20Case%20Study.pptx) to download the presentation.

**Act**

After the analysis there are three recommendations I would make based on the trends we have noted.

1.	Lower incremental rates for longer use.
	We see that Casual riders are on the bikes for longer periods of time. To encourage longer use we should decrease the charge per minute for members. After 15 minutes of use we can decrease the minute rate by a certain percentage. The mean ride time for casual riders is 27 minutes while member mean ride time is 12. If we charge less for member to use after 15 minutes, it will lead to casual riders converting to members to ride the bikes longer.

2.	Reduced fare at specific time of day and day of week.
	The other Major difference is linked with time. We see Casual rider’s ride at different hours of the day and different days of the week. We could have a reduced price for Members to ride after 6 and during the noon hour. This would attract our casual members because their use is not based on work hours. It would also have the benefit of making sure we have enough bikes for current member when they need it most at 5 P.M. These reduced member prices should also be in place on weekends. This is the highest traffic time for casual riders. If we have these price changes in place, we will be offering a lower price for members when casual riders most want to ride.

3.	Location based discounts and activities
	We observe the top 5 locations being near lakeshore drive and near tourist attractions such as the aquarium. We can assume that this is due to their primary use for the service being for leisurely activities. With leisure in mind, a recommendation I would give is to incentivize these activities. We can work with the city to give large discounts to members for public events. We can also give guided tours for tourists on the lake shore. Using these methods, we meet the casual rider’s needs.


Thank you.
