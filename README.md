# **Geospatial Analysis, crimes in San Francisco**

# Use Case

- Use Case Summary:
- Objective Statement:
  * Get insights into which crimes are committed the most and what the patterns are in them.
  * Get insights into which crimes are most committed by time of day and have another level of granularity for new discoveries.
  * Understand if the data possesses bias in the crime records, and consequently highlight these errors.

- Challenges:
  * Large size of data, with many columns and crime categories.
  * Data has some strange patterns in the records and it is important to filter them.

- Methodology / Analytic Technique:
  * Descriptive analysis
  * Graph analysis
  * Spatial analysis
 
- Expected Outcome:
  * Show authorities which crimes are most committed and where they occur, with an additional readout of day and time patterns on such occurrences.
  * Demonstrate that the police data has certain errors and even biases about how crimes are registered in the city
  * Interactive map to understand the city's crime patterns

# Data Undersanding
- Source Data: San Francisco Open Data - Incident Report (2003 to 2018). https://data.sfgov.org/Public-Safety/Police-Department-Incident-Reports-2018-to-Present/wg3w-h783
- The dataset has 26 columns with 2,129,525 rows, with a daily update.
- Data Dictionary (columns used):
- Incident Datetime: The date and time when the incident occurred
- Incident Category: A category mapped on to the Incident Code used in statistics and reporting. Mappings provided by the Crime Analysis Unit of the Police Department.
- Incident Subcategory: A subcategory mapped to the Incident Code that is used for statistics and reporting. Mappings are provided by the Crime Analysis Unit of the Police Department.
- Resolution: The resolution of the incident at the time of the report. 
- Latitude: The latitude coordinate in WGS84, spatial reference is EPSG:4326.
- Longitude: The longitude coordinate in WGS84, spatial reference is EPSG:4326.

# Data Preparation

- Code Used:
- Python Version: 3.9.7
- Packages: Pandas, Numpy, Matplolib, Folium

# Data Cleansing

- Due to the massive amount of data, I have filtered for the most committed crimes in the city to make the data narrative simpler and more effective for understanding the patterns shown
- There are many records marked every 30 minutes, an indication that the data may not be that accurate, since it is a manual input from a police officer.
- Over the years the categorization of the data has changed, a common indication of changing internal rules in incident records and at the same time a sign of error in the data because it has not been translated to the most current standard of the department rule.

# Exploratory Data Analysis
- What are the most committed crimes in San Francisco and what are their patterns? 
![crime_week](https://i.imgur.com/tdjS4vc.png)

We can see that the data make sense for some crimes (e.g. Drunkness increasing too much around the weekend) and some curious insights such as prostitution being high during the middle of the week.

- What time of the day are crimes most committed?
![crime_hour](https://i.imgur.com/TAVf6In.png)

Going into a higher level of granularity of the occurrences, we can see that for example for prostitution the most common hours are near evening with a slight peak during the middle of the day. Furthermore it seems that most crimes occur at night, except for trespassing where there is a very high incident during the day.

- What is the crime rate per region in the city of San Francisco?
![crime_hour](https://i.imgur.com/3pDtV8e.png)

To accomplish this visualization, I put together a formula to understand what the crime ratio is within the regions using crime types as a category, so that it is possible to understand what are the most committed offenses per crime in the city of San Francisco. For example, in the Richmond district vehicle theft is extremely high compared to the city average. 
Formula for the calculation: $\frac{P(crime|district)}{P(crime)}$

- Where are the main crime areas?
![crime_hour](https://i.imgur.com/1T7AMVM.png)

Here we can see a very interesting insight, there are two clear clusters of crime in the city, one near the city hall (highlighted in an orange icon) and one district near the outskirts, inside the python file you can see these regions changing over the years, showing that crime evolves according to the public policy established.

- Are there errors in the data?
![crime_error](https://i.imgur.com/roGcsUk.png)

Here we can clearly see that the records of crimes committed have a strange pattern, apparently the vast majority of crimes occur at set times (every 30 minutes), I believe this is a mistake because the police officers do not pay enough attention to understand at what time the crime occurred, thus creating noise in the database.


# Recommendation
- The San Francisco police must understand that the accuracy of the data must be taken seriously, we understand that it is difficult to categorize such crimes but with a robust and reliable system it is possible to extract even more insights to improve the quality of life of the city's citizens.


- Furthermore, we can see great insights into types of crimes and locations in the city, which is important to show the authorities where they should act.








