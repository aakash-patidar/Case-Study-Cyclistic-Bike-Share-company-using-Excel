# Case Study: Cyclistic Bike-Share

<p align="center">
  <img width="460" height="300" src="https://goodordering.com/cdn/shop/articles/Freddie-Grubb-Cycle-to-Work-Scheme-London.jpg?v=1614180230">
</p>

## Introduction
I am a junior data analyst working on the marketing analyst team at Cyclistic, a bike-share company in Chicago. As a data analyst, our primary objective is to understand the behaviour of casual riders and annual members to develop a strategic marketing approach aimed at converting casual riders into annual members. The director of marketing believes Cyclistic's future depends on getting as many people as possible to sign up for annual memberships. To achieve this goal, we need to use data to understand how casual riders and annual members use our bikes differently.

The key steps followed in the analysis:
- Ask
- Prepare
- Process
- Analyze
- Share
- Act

### About the company
In 2016, Cyclistic launched a successful bike-share offering. Since then, the program has grown to a fleet of 5,824 bicycles that are geotracked and locked into a network of 692 stations across Chicago. The bikes can be unlocked from one station and returned to any other station in the system anytime. Until now, Cyclistic’s marketing strategy relied on building general awareness and appealing to broad consumer segments. One approach that helped make these things possible was the flexibility of its pricing plans: single-ride passes, full-day passes, and annual memberships. Customers who purchase single-ride or full-day passes are referred to as casual riders. Customers who purchase annual memberships are Cyclistic members. Cyclistic’s finance analysts have concluded that annual members are much more profitable than casual riders. Moreno(the director) believes that maximizing the number of annual members will be key to future growth. Rather than creating a marketing campaign that targets all-new customers, Moreno believes there is a solid opportunity to convert casual riders into members. She notes that casual riders are already aware of the Cyclistic program and have chosen Cyclistic for their mobility needs. 

## Data Source
[trip_data](https://divvy-tripdata.s3.amazonaws.com/index.html)

## Tools
- Power Query: Merging Data
- Microsoft Excel: Cleaning Data
- Pivot Table: Data Analysis
- Microsoft Excel: Data Visualization

## Data Analysis Process
### Ask:  
The "ask" phase of the data analysis process involves recognizing the current problem, understanding stakeholder expectations, defining the business task, and identifying how insights will benefit stakeholders.

**Business Task:**  
Analyze the behavior of casual riders and annual members in order to develop a strategic marketing approach aimed at converting casual riders into annual members.

**Key Stakeholders**  
The key stakeholders for this project include:  
Lily Moreno: The Director of marketing and my Manager. Moreno is responsible for the development of campaigns and initiatives to promote the bike-share program.  
Cyclistic executive team: The notoriously detail-oriented executive team will decide whether to approve the recommended marketing program.  
Cyclistic marketing analytics team: A team of data analysts who are responsible for collecting, analyzing, and reporting data that helps guide Cyclistic marketing strategy.  

### Prepare:  
The "prepare" phase of the data analysis process involves collecting and preparing the necessary data for analysis. Key steps include identifying data sources such as databases, spreadsheets, or external sources, and then extracting the relevant information.  
- The dataset used for this project is public data provided by Motivate International Inc. It can be used to explore how different customer types are using Cyclistic bikes. The dataset consists of monthly files from January 2022 to December 2022.
- In each file of the dataset, there are 13 columns that describe different aspects of the bike rides. The columns consist of the ride ID, bike type, starting and ending station IDs, names of the starting and ending stations, geographic coordinates, and membership type for each ride.

### Process:
The "process" step in data analysis involves cleaning, transforming, and integrating data to make sure it is accurate, consistent, and ready for analysis. This includes tasks like handling missing values, correcting errors, standardizing formats, and merging data from different sources. These steps are essential to ensure the quality and reliability of the data for meaningful analysis.  

The tool we used for the process step is Microsoft Excel. The following actions we performed to clean the data:
- **Converting .csv files to .xlsx format:** First, the 12 months of bike-sharing data collected in the prepare step were in .csv format. We converted this data into .xlsx format using the Save As option. Converting a CSV file to an XLSX file allows for enhanced data formatting, improved readability, and access to advanced features such as formulas, charts, and data validation available in Excel.
- **Removing Duplicates:** Utilized Excel's built-in "Remove Duplicates" feature to identify and remove duplicate entries from the dataset.
- **Removing Blanks:** When transforming data, removing blanks(or missing values) is a crucial step to ensure data quality and integrity. To ensure integrity of the data, blank values were removed from the start_station_name, start_station_id, end_station_name, and end_station_id columns to ensure data completeness.
- **Handling Missing Data:** Used Excel's tool like Conditional formatting to identify and handle any missing data.
- **Validating Data:** Validate the data to ensure its accuracy and consistency. Ensure that the values in particular columns like "rideable_type" and "member_casual" are consistent and accurate. No values other than "classic_bike," "docked_bike," or "electric_bike" for the "rideable_type" column, and "casual" or "member" for the "member_casual" column should be present.
- **Removing unwanted data:** All geographical location data, such as start_lat, start_lng, end_lat, and end_lng, were removed as they were irrelevant to the problem we are addressing.

#### Data Transformation 
Now that all the data is cleaned up, it's time to transform it into a useful format and organize it to prepare it for analysis.
Power Query is a powerful data transformation tool in Excel that allows users to import, transform, and combine data from various sources. It enables users to clean, reshape, and transform data with ease, making it suitable for analysis and reporting purposes.  
**Data Merging using Power Query**  
A new table named Annual_cyclistic_data_2022 was created. Then, imported the complete folder of cleaned 12 months data to merge.  

  <img width="460" height="300" src="https://github.com/aakash-patidar/Case-Study-Cyclistic-Bike-Share-company-using-Excel/assets/171103471/95d4503c-f99c-48f2-bc18-9baf239f9f67">

Now, all the 12 months bike sharing data was combined using the Power Query to transform into a meaningful format.  

  <img width="460" height="300" src="https://github.com/aakash-patidar/Case-Study-Cyclistic-Bike-Share-company-using-Excel/assets/171103471/3b51153f-f65d-4f42-b2c9-4493d9869a22">

Here is the comprehensive dataset for the Cyclistic bike-sharing company covering the entire year of 2023:  

  <img width="460" height="300" src="https://github.com/aakash-patidar/Case-Study-Cyclistic-Bike-Share-company-using-Excel/assets/171103471/906f2fb6-8e9c-47c7-8bad-f8eccb2c6022">

Once the data has been merged, load the data into the Excel to do some further transformation and organization of data to ensure data integrity.  

  <img width="460" height="300" src="https://github.com/aakash-patidar/Case-Study-Cyclistic-Bike-Share-company-using-Excel/assets/171103471/adc2f0da-7c42-4039-8321-b79cf24ff686">

Now, three more columns were added named ride_length, day_of_week and day_of_week_name.  
- **ride_length:** A ride_length column was added to calculate the duration of each ride by subtracting the started_at column from the ended_at column, and formatting the result into HH:MM
format.
- **day_of_week:** A day_of_week column was added to calculate the day of the week that each ride started using the WEEKDAY function, with the formula =WEEKDAY(C2,1) in each file. In this function, 1 represents Sunday and 7 represents Saturday.
- **day_of_week_name:** A new column, day_of_week_name, was added to display the names of the days. This was done by copying all the values from the day_of_week column, pasting them as values using the Paste Special tool in Excel, and then replacing the numerical values with the day names (Sunday through Saturday) using the Find & Replace tool.

The complete cleaned dataset was finally collected and used to analyze important insights.  

  <img width="460" height="300" src="https://github.com/aakash-patidar/Case-Study-Cyclistic-Bike-Share-company-using-Excel/assets/171103471/1abf29a7-cd76-4fd5-adbf-a1d9baa0998c">  

### Analyze:  
The "Analyze" phase in the data analysis process involves examining the cleaned and prepared data to uncover meaningful insights and trends. In this phase, we explored the data to uncover insights and address key findings about how annual members and casual riders use Cyclistic bikes differently. Our goal was to understand their behaviors and patterns to inform marketing strategies that could convert casual riders into annual members. 
**Tool used to analyze cyclistic data:** Pivot Tables

1. **Average ride length for members and casual riders**  
   A pivot table was created to identify the trends in ride length for different riders, including members and casual riders. By placing member_casual in the Rows area and the Average of ride_length in the Values area, we were able to clearly differentiate how each member type uses the bikes, providing valuable insights into their riding patterns.  
   
     <img src="https://github.com/aakash-patidar/Case-Study-Cyclistic-Bike-Share-company-using-Excel/assets/171103471/ba0b17be-a15b-4888-8ef5-c0c04790eab8">  

2. **Average ride length for users by weekdays**
   A pivot table was designed to uncover the patterns in ride length for different users across the week days. This pivot table was organized by placing member_casual in the Rows area, day_of_week_name in the Columns area, and the Average of ride_length in the Values area. This configuration enabled us to analyze utilization patterns and gain insights into how different rider types use bikes on different days of the week.  

    <img src="https://github.com/aakash-patidar/Case-Study-Cyclistic-Bike-Share-company-using-Excel/assets/171103471/9a5943a6-6a93-47b0-8beb-c8ab0a04db6a">  

3. **Number of rides for users by weekdays**
   A pivot table was crafted to unveil the patterns in the number of rides for different users throughout the weekdays. This pivot table was structured by arranging day_of_week_name in the Rows area, member_casual in the Columns area, and the Count of ride_id in the Values area. This setup empowered us to scrutinize utilization patterns and glean insights into how the number of rides varies across weekdays for different user groups.  

    <img src="https://github.com/aakash-patidar/Case-Study-Cyclistic-Bike-Share-company-using-Excel/assets/171103471/c1478d1a-5840-45b0-9cbf-a2850cf362b6">  

4. **Number of rides for users by bike type**
     A pivot table was created to examine how annual riders and casual riders utilize various types of bikes. This pivot table was organized by putting "rideable_type" in rows and "member_casual" in columns and Count of ride_id in Values to count the number of rides for each combination to see how annual riders and casual riders use different types of bikes.  

    <img src="https://github.com/aakash-patidar/Case-Study-Cyclistic-Bike-Share-company-using-Excel/assets/171103471/57906816-3727-42ce-a6cf-f718d64c5634">  

### Share:
The "Share" phase of the data analysis process involves communicating the results and insights derived from the analysis to stakeholders. This includes summarizing key findings, creating visualizations to present data trends, and providing actionable recommendations for decision-making. Effective communication ensures that stakeholders understand the implications of the data analysis and can use it to inform strategic decisions.  

1. **Average ride length for members and casual riders**  

    <img src="https://github.com/aakash-patidar/Case-Study-Cyclistic-Bike-Share-company-using-Excel/assets/171103471/f1da23c1-d111-48d3-a779-ce790143012b">  
The chart shows that casual riders have a significantly longer average ride length, approximately 28 minutes and 48 seconds, compared to members, whose average ride length is about 14 minutes and 24 seconds.
    
2. **Average ride length for users by weekdays**

     <img src="https://github.com/aakash-patidar/Case-Study-Cyclistic-Bike-Share-company-using-Excel/assets/171103471/fd86c0a4-43fa-44a3-86f9-9d13d7a05fb2">  
The bar graph shows how Cyclistic’s bike share program is used differently by annual members and casual riders. It shows that annual members of Cyclistic’s bike share program have consistent ride lengths throughout the week, using the service mainly for daily       activities like commuting. In contrast, casual riders have much longer rides on Saturdays and Sundays, suggesting they use the bikes more for weekend leisure and recreation. This highlights the different riding patterns: regular use by annual members and         recreational use by casual riders.lves communicating the findings, insights, and results of the analysis to stakeholders, colleagues, or a broader audience. This phase is crucial as it translates complex data into actionable information that can drive decision-making. The best way to share your findings is through data visualization. Data visualization, the graphical representation of data, helps you convey meaningful insights and tell your data story more effectively.

3. **Number of rides for users by weekdays**

     <img src="https://github.com/aakash-patidar/Case-Study-Cyclistic-Bike-Share-company-using-Excel/assets/171103471/4bdcb3bc-791e-4e1a-ac9a-51965781cdba">  
The chart displays the number of rides for casual and member users across weekdays. Member users consistently have higher numbers of rides than casual users throughout the week. The peak usage for members is observed on Tuesday and Wednesday, with over 120,000 rides while the lowest usage is on Sunday, with around 80,000 rides. Casual users show relatively stable ride numbers from Monday to Friday, with an increase during the weekend, especially on Saturday, reaching around 60,000 rides. Overall, members dominate ride numbers on weekdays, while casual users show increased activity on weekends. 
     
4. **Number of rides for users by bike type**

     <img src="https://github.com/aakash-patidar/Case-Study-Cyclistic-Bike-Share-company-using-Excel/assets/171103471/92ba061c-fa9d-4a2f-8c48-999d14a34759">  
The bar chart displays the number of rides for different bike types (electric, docked, and classic) categorized by user type (member and casual) on weekdays. Members dominate with approximately 400,000 electric bike rides compared to around 175,000 by casual users. For classic bikes, members take about 425,000 rides, while casual users take around 125,000 rides. Docked bikes are used the least, with members accounting for nearly 30,000 rides and casual users for around 10,000 rides. Members consistently have higher ride numbers across all bike types.  

### Act:

**Key takeaways:**  
- Ride Duration: Casual riders have significantly longer average ride lengths compared to annual members.
- Usage Patterns: Annual Member use the bike share service consistently throughout the week, primarily for daily activities such as commuting while casual riders tend to have much longer rides on weekends (Saturdays and Sundays), indicating a preference for using the bikes for leisure and recreational activities.
- Ride Frequency: Members have a higher number of rides consistently across all weekdays, peaking on Tuesday and Wednesday with over 120,000 rides. The lowest usage is on Sunday with around 80,000 rides whereas casual riders maintain stable ride numbers from Monday to Friday, with a notable increase during weekends, especially on Saturday, reaching around 60,000 rides.
- Bike Type Preference: Annual members show a higher preference for classic and electric bikes, while casual riders have a higher inclination towards docked bikes.
- Weekday vs. Weekend Usage: Annual members tend to ride more on weekdays, while casual riders have higher usage on weekends.

#### Recommendations to convert more Casual Riders into Annual Members    
- **Introduce Weekend Membership Plans:** Offer a special weekend membership plan that provides unlimited rides at a discounted rate for weekends. This could attract casual riders who predominantly use the service on Saturdays and Sundays to commit to a membership, providing them with cost savings and benefits.
- **Enhanced Incentives and Rewards:** Create a loyalty program that rewards frequent casual riders with incentives such as discounted annual memberships, free ride credits, or exclusive access to events and partner discounts. Highlight the long-term savings and perks that come with an annual membership to encourage casual riders to upgrade.
- **Targeted Marketing and Promotions:** Develop targeted marketing campaigns that focus on the benefits of an annual membership. Use data-driven insights to send personalized promotions to casual riders who frequently use the service on weekends. Highlight features such as the convenience of consistent usage, cost savings, and additional benefits (e.g., priority access to bikes, special offers). Engage these riders through email campaigns, social media ads, and in-app notifications to convert them into annual members.


   
  



  
































