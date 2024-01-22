# Google-Data-Analytics-Capstone-Case-Study-Cyclistic
In this case study, I perfomed many real-world tasks of a junior data analyst at a fictional company, Cyclistic. In order to answer the key business questions, I will follow the steps of the data analysis process: Ask, Prepare, Process, Analyze, Share, and Act.
I have performed Data Combining, Data Cleaning and Data Exploration using Python. I haved used Power BI for Data Analysis and Vizualization.
# Background
Cyclistic
A bike-share program that features more than 5,800 bicycles and 600 docking stations. Cyclistic sets itself apart by also offering reclining bikes, hand tricycles, and cargo bikes, making bike-share more inclusive to people with disabilities and riders who can’t use a standard two-wheeled bike. The majority of riders opt for traditional bikes; about 8% of riders use the assistive options. Cyclistic users are more likely to ride for leisure, but about 30% use them to commute to work each day.

Until now, Cyclistic’s marketing strategy relied on building general awareness and appealing to broad consumer segments. One approach that helped make these things possible was the flexibility of its pricing plans: single-ride passes, full-day passes, and annual memberships. Customers who purchase single-ride or full-day passes are referred to as casual riders. Customers who purchase annual memberships are Cyclistic members.

Cyclistic’s finance analysts have concluded that annual members are much more profitable than casual riders. Although the pricing flexibility helps Cyclistic attract more customers, Moreno (the director of marketing and my manager) believes that maximizing the number of annual members will be key to future growth. Rather than creating a marketing campaign that targets all-new customers, Moreno believes there is a very good chance to convert casual riders into members. She notes that casual riders are already aware of the Cyclistic program and have chosen Cyclistic for their mobility needs.

Moreno has set a clear goal: Design marketing strategies aimed at converting casual riders into annual members. In order to do that, however, the marketing analyst team needs to better understand how annual members and casual riders differ, why casual riders would buy a membership, and how digital media could affect their marketing tactics. Moreno and her team are interested in analyzing the Cyclistic historical bike trip data to identify trends.

# Scenario
I assumed to be a junior data analyst working in the marketing analyst team at Cyclistic, a bike-share company in Chicago. The director of marketing believes the company’s future success depends on maximizing the number of annual memberships. Therefore, my team wants to understand how casual riders and annual members use Cyclistic bikes differently. From these insights, my team will design a new marketing strategy to convert casual riders into annual members. But first, Cyclistic executives must approve our recommendations, so they must be backed up with compelling data insights and professional data visualizations.

Ask
Business Task
Devise marketing strategies to convert casual riders to members.

Analysis Questions
Three questions will guide the future marketing program:

How do annual members and casual riders use Cyclistic bikes differently?
Why would casual riders buy Cyclistic annual memberships?
How can Cyclistic use digital media to influence casual riders to become members?
Moreno has assigned me the first question to answer: How do annual members and casual riders use Cyclistic bikes differently?

Prepare
Data Source
I used Cyclistic’s historical trip data to analyze and identify trends from Jan 2023 to Dec 2023 which can be downloaded from [divvy_tripdata](https://divvy-tripdata.s3.amazonaws.com/index.html).

This is public data that can be used to explore how different customer types are using Cyclistic bikes. But note that data-privacy issues prohibit from using riders’ personally identifiable information. This means that we won’t be able to connect pass purchases to credit card numbers to determine if casual riders live in the Cyclistic service area or if they have purchased multiple single passes.

Data Organization
There are 12 files with naming convention of YYYYMM-divvy-tripdata and each file includes information for one month, such as the ride id, bike type, start time, end time, start station, end station, start location, end location, and whether the rider is a member or not. The corresponding column names are ride_id, rideable_type, started_at, ended_at, start_station_name, start_station_id, end_station_name, end_station_id, start_lat, start_lng, end_lat, end_lng and member_casual.

Process
Python is used to combine the various datasets into one dataset and clean it.
Reason:
A worksheet can only have 1,048,576 rows in Microsoft Excel because of its inability to manage large amounts of data. Because the Cyclistic dataset has more than 5.6 million rows, it is essential to use a platform like Python that supports huge volumes of data.

I used Python for Data Combining, Data Exporation and Data Cleaning. After that i splited Total data into two files. One contains all riding details and other one contains all station details making ride_id primary in both files. 

# Data Combining
file_list = [r'C:\Users\Saikat\Desktop\BA Project\Cyclistic\Jan 2023/202301-divvy-tripdata.csv',
            r'C:\Users\Saikat\Desktop\BA Project\Cyclistic\Feb 2023/202302-divvy-tripdata.csv',
            r'C:\Users\Saikat\Desktop\BA Project\Cyclistic\March 2023/202303-divvy-tripdata.csv',
            r'C:\Users\Saikat\Desktop\BA Project\Cyclistic\April 2023/202304-divvy-tripdata.csv',
            r'C:\Users\Saikat\Desktop\BA Project\Cyclistic\May 2023/202305-divvy-tripdata.csv',
            r'C:\Users\Saikat\Desktop\BA Project\Cyclistic\June 2023/202306-divvy-tripdata.csv',
            r'C:\Users\Saikat\Desktop\BA Project\Cyclistic\July 2023/202307-divvy-tripdata.csv',
            r'C:\Users\Saikat\Desktop\BA Project\Cyclistic\Aug 2023/202308-divvy-tripdata.csv',
            r'C:\Users\Saikat\Desktop\BA Project\Cyclistic\Sep 2023/202309-divvy-tripdata.csv',
            r'C:\Users\Saikat\Desktop\BA Project\Cyclistic\Oct 2023/202310-divvy-tripdata.csv',
            r'C:\Users\Saikat\Desktop\BA Project\Cyclistic\Nov 2023/202311-divvy-tripdata.csv',
            r'C:\Users\Saikat\Desktop\BA Project\Cyclistic\Dec 2023/202312-divvy-tripdata.csv']
files = pd.DataFrame()
for file in file_list:
    current = pd.read_csv(file)
    files = pd.concat([files, current], ignore_index = True)
# Data Eploration
Converting into exact data types:
ride_id                       object
rideable_type                 object
started_at            datetime64[ns]
ended_at              datetime64[ns]
start_station_name            object
start_station_id              object
end_station_name              object
end_station_id                object
start_lat                    float64
start_lng                    float64
end_lat                      float64
end_lng                      float64
member_casual                 object
dtype: object
# Data Cleaning
Checking unique values for eleminating duplicate rows
ride_id               5719877
rideable_type               3
started_at            4823909
ended_at              4835702
start_station_name       1592
start_station_id         1516
end_station_name         1597
end_station_id           1520
start_lat              789702
start_lng              748738
end_lat                 13884
end_lng                 14002
member_casual               2
dtype: int64
Converting into categories for reducing file size
Column              Dtype         
---  ------              -----         
 0   ride_id             object        
 1   rideable_type       category      
 2   started_at          datetime64[ns]
 3   ended_at            datetime64[ns]
 4   start_station_name  category      
 5   start_station_id    category      
 6   end_station_name    category      
 7   end_station_id      category      
 8   start_lat           float64       
 9   start_lng           float64       
 10  end_lat             float64       
 11  end_lng             float64       
 12  member_casual       category      
dtypes: category(6), datetime64[ns](2), float64(4), object(1)
memory usage: 360.3+ MB
Checking null values
ride_id                    0
rideable_type              0
started_at                 0
ended_at                   0
start_station_name    875716
start_station_id      875848
end_station_name      929202
end_station_id        929343
start_lat                  0
start_lng                  0
end_lat                 6990
end_lng                 6990
member_casual              0
dtype: int64
Making separate data with all riding details
![image](https://github.com/saikatdtt1/Google-Data-Analytics-Capstone-Case-Study-Cyclistic/assets/144656040/bf6f778a-122b-4a8b-9aa4-32baae6d14e8)

Making separate data with all stations details
![image](https://github.com/saikatdtt1/Google-Data-Analytics-Capstone-Case-Study-Cyclistic/assets/144656040/9a1b7def-f121-4658-a1a3-064e40e8e0fa)
Separating Day, Hour, Minute and Second
![image](https://github.com/saikatdtt1/Google-Data-Analytics-Capstone-Case-Study-Cyclistic/assets/144656040/d3322316-387d-46a1-8942-038873d17c76)

# Data Analysis
The analysis question is: How do annual members and casual riders use Cyclistic bikes differently?
Yearly Analysis
![Year](https://github.com/saikatdtt1/Google-Data-Analytics-Capstone-Case-Study-Cyclistic/assets/144656040/5fe81f52-19d2-463a-9fa0-ac5c45990532)
Seasional Analysis
![Seasion](https://github.com/saikatdtt1/Google-Data-Analytics-Capstone-Case-Study-Cyclistic/assets/144656040/c844ce72-9fbc-49e5-9474-ab114ff8bd97)
Monthly Analysis
![Month](https://github.com/saikatdtt1/Google-Data-Analytics-Capstone-Case-Study-Cyclistic/assets/144656040/db02ce8d-4fa4-40b3-9c80-71410760bf13)
Weekly Analysis
![Week](https://github.com/saikatdtt1/Google-Data-Analytics-Capstone-Case-Study-Cyclistic/assets/144656040/c94734da-16c0-4877-a3df-57b393a828bb)
Daily Analysis
![Day](https://github.com/saikatdtt1/Google-Data-Analytics-Capstone-Case-Study-Cyclistic/assets/144656040/80a44e29-b2b4-4f6c-b1aa-3447ed42df22)
Months: When it comes to monthly trips, both casual and members exhibit comparable behavior, with more trips in the spring and summer and fewer in the winter. The gap between casuals and members is closest in the month of july in summmer.
Days of Week: When the days of the week are compared, it is discovered that casual riders make more journeys on the weekends while members show a decline over the weekend in contrast to the other days of the week.
Hours of the Day: The members shows 2 peaks throughout the day in terms of number of trips. One is early in the morning at around 6 am to 8 am and other is in the evening at around 4 pm to 8 pm while number of trips for casual riders increase consistently over the day till evening and then decrease afterwards.
These findings lead to the conclusion that casual commuters travel longer (approximately 2x more) but less frequently than members. They make longer journeys on weekends and during the day outside of commuting hours and in spring and summer season, so they might be doing so for recreation purposes.
Summary:
  Casual: 
  Prefer using bikes throughout the day, more frequently over the weekends in summer and spring for leisure activities.
  Travel 2 times longer but less frequently than members.
  Member:
  Prefer riding bikes on week days during commute hours (8 am / 5pm) in summer and spring.
  Travel more frequently but shorter rides (approximately half of casual riders' trip duration).
# Act
After identifying the differences between casual and member riders, marketing strategies to target casual riders can be developed to persuade them to become members.
Recommendations:
Annual membership could be included with hourly benefits.
Casual members could be attracted by making Annual benefit only for weekends.
Some special benefits could be included in Summer seasions for attacting more Annual members.


