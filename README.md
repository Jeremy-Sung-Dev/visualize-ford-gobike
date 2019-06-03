# Exploratory Visualization on Ford GoBike Data
## by Jeremy Sung
## Objective
> Perform exploratory analysis and Geo Analytics on Ford GoBike archives stored on AWS S3 and create slides to communicate the data story

## Dataset

> Ford GoBike System Data Set includes information about individual bike rides via this bike-sharing system in greater SF Bay area. It consists of 16 different variables such as age, gender, weekday, time and others and 3.31 billion rides. Ages between 18 and 56 cover 95% of the users in dataset. Riders over 100 years old can also be found. I remove users more than 60 years old. In order to make grouping and analyze the date by using groups i generated new fields such as age group.

## Summary of Findings

After data type conversion and cleaning missing values, I looked into all features in three aspects to explore data stories and summarized my findings as follows.

### Customer related:
#### Genders:
- **Male customers are the majority, 74.13%, compared with the Female, 24.23%.**
- **Dropping 6.69% missing values in member_gender does not make much difference on distribution.**
- **There is a connection on missing values between member_gender and member_birth_year.**
  - Clean missing values in member_birth_year removed all missing values in member_gender.
  - If we clean missing values in member_gender first, member_birth_year has only 433 missing values left.

#### Rider Ages:
##### Statistics:
- No Customer is younger than 18 years old. Most customers (> 99%) are younger than 66 years old.
- The oldest customer(s) in this dataset is 141 years old.
- In Statistics, outliers in member_age, the lower bound is 8.5 years old and the higher bound, 60.5 years old. Customers older than 60.5 years old can be considered as outliers and excluded..
- Customers older than 66 years old were excluded from this analysis.
- While average rider age is 35.86 years old, customers at age 31 is most common among riders and the majority of customers are in their 30s.

##### Demands in Age Groups:
- Ages between 24 and 40 are the dominant rider age groups, followed by ages between 41 and 56.
- The number of bike renters in their 20-30 exceeded those in age group 30-40 after Jun, 2018 and became dominant.

##### Blend in the `Month` feature:
- When blend in the Month derived feature, we noticed that  
 - Customers in 20-30 age group climbed up fast and surpassed the customers in age group 30-40 in Nov, 2018;
 - Demands on bike rental serivce in age group 40 to 60 rose up and fell down with four seasons.
 - Demands from customers in their 60+ were fairly stable. No apparent change on the bike rental counts.
 - The demand on bike rentals on Subscribers varied with season. Non-subscribers, i.e. other customers (green line) did not show much change on demand.

### Rides and Rental related:
#### Average trip duration & distance between subscribers and non-subscribers:
- Average trip duration for Customers is twice as long as that for Subscribers.
- Travel distances by customers is roughly the same as those done by subscribers, 1.21 vs. 1.04 miles.
- The majority of bike rides last between 6 mins(345 secs, Q1) and 12 mins (837 secs, Q3). Average Bike Rental Duration is 13 mins (778 secs, mean()). Most bike rides (95%) fell within 27.5 mins (1650 secs, 95%). And, rarely any ride went beyond an hour (64.5 mins, 3,871 secs, >99%).

### Timing and Demands:
##### Highest and Lowest:
- The highest daily demand of all time appeared in April, 2018.
- The lowest daily demands since the bike sharing service go-live appeared in Nov - Dec, 2017 and in Nov - Dec in 2018;

##### Peak Service Hours
- Peak demands on bike sharing services not only came during weekdays, especially on Tue, Wed and Thu, but are also in aligbment with commute hours, i.e. 7:00 to 9:00 AM and 4:00 to 7:00 PM.
- Strongly suggests that the bike sharing service has to do with daily commute to work or to school.

##### Blend in `customer types: Subscribers and Non-Subscribers` and `customer age groups`:
- Subscribers in age group 30-40 were the the main bike renters followed by those in age group 20-30.
- Subscribers in age group 20-30 surpassed the age group 30-40 subscribers after Oct, 2019 and became the primary bike renters. Bike rentals with riders in other age groups fluctuated with seasons with or without subscription.
- Subscriber rentals often occurred in 7 to 9am and 4 to 6pm, the so-called Commute Hours.
- On the other hand, rentals from non subscribers often took place between 5pm and 6pm in weekday and from 12pm to 4pm in the weekend. **Thought: Non-subscribers tend to rent bikes after business hours in weekday and weekend for casual and recreational purpose.**

##### Blend in riders in the `"Bike Share for All"` program:
- Peak rental demands from riders in this program occurs at around 5:00PM. No apparent alignment is found with the morning commute hours (7-9). **Thought: This may have to do with the fares.**

### Geographical Analyses (GeoAnalytics):
#### SF Bay Area:
Some insights derived from coordinates, latitudes & longitudes, are summarized as follows.
- In general, Ford GoBike service offers millions of bike sharing stations in SF Bay areas and are gathered in three regions:
 - San Francisco downtown - only in certain districts centered around Embarcadero and Mission District.
 - Oakland Downtown / Berkeley, and
 - San Jose downtwon.
 - Little to no bike station is found in other counties or regions, such as cities in
   - Penisula including Mountain Views, Palo Alto, Redwood City, and San Mateo, etc. or
   - East Bay such as Fremont, Newark, Union City, and Hayward, etc.
- The Top-100 most popular start stations are found in San Francisco and in Oakland.

#### Zoom in San Francisco and Oakland:
- After we zoom in to street map of each region, overall Top-100 most popular start stations are, indeed, located in San Francisco downtown followed by Oakland downtown.

#### Zoom in Berkeley and San Jose, blending with `Bike Share for All` feature:
- Popular start stations in Berkeley and San Jose were mostly rented by riders who leveraged the `Bike Share for All` program. The number of regular customers, i.e. those who paid full price for the bike sharing service, are relatively small compared with those in San Francisco and Oakland.   

## Key Insights for Presentation
> Ford GoBike bike sharing service is popular in San Francisco, Oakland, Berkeley and San Jose. Customers are between 18 and 66 years old with the majority between 28 and 41. The average customer age is at 35.86 years old.
> Average ride distance for subscribers is 1.04 miles and 1.21 miles for non-Subscribers.
> Average ride duration for subscribers is 11.19 mins and 26.64 mins for non-Subscribers.
> Based on the timing and patterns subscribers most likely use bikes for daily commute either to school or to work. Non-subscribers show peak rental counts after hours or in weekends.
> Riders who took advantage of the "Bike Share for All" program preferred to rent bikes in Berkeley or in in San Jose, followed by Oakland Downtown. San Francisco also has quite a few popular bike stations for "Bike Share for All" riders but the majority of the Top 100 most popular bike stations in the city are regular stations.         
