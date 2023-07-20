# COVID-19 Data Analysis Using SQL

## Description:

This SQL portfolio project focuses on analyzing COVID-19 data to gain valuable insights and trends related to the pandemic. 
The project showcases my proficiency in SQL queries, data manipulation, and analysis techniques.


## Data Sources:
The dataset used in this project is sourced from reliable and authoritative repositories, such as government health agencies, global health organizations, 
and reputable research institutions. It includes information on COVID-19 cases, deaths, recoveries, testing, and demographic data.


## Project Objectives:

  Data Exploration: Perform exploratory data analysis to gain a comprehensive understanding of the dataset's structure and content.

  Data Cleaning: Preprocess and clean the data to ensure accuracy and consistency in the analysis.

  Data Aggregation: Utilize SQL queries to aggregate and summarize COVID-19 data at various levels, including country, region, and time.

  Time Series Analysis: Apply SQL queries to study the progression of COVID-19 cases, deaths, and recoveries over time.

  Geospatial Analysis: Perform geospatial analysis to visualize the distribution of COVID-19 cases on maps.

  Comparative Analysis: Conduct comparative analysis across countries or regions to identify patterns and differences in COVID-19 metrics.


## Key SQL Skills Demonstrated:

  Data querying and filtering using SELECT, WHERE, GROUP BY, and HAVING clauses.
  Joining multiple tables to combine relevant data for analysis.
  Aggregating data with functions like COUNT, SUM, AVG, and MAX.
  Analyzing time-based data using date functions and window functions.
  Creating views and temporary tables for complex queries and analysis.
  
## Outcome:
  The COVID-19 Data Analysis project on my Github repository showcases my proficiency in SQL and ability to work with real-world datasets to derive valuable insights. 
  Through this project, I demonstrate my analytical and problem-solving skills in the context of a global health crisis, highlighting my commitment to continuous learning and contributing to data-driven decision-making processes.




SELECT * 
FROM PortfolioProject..[Covid-deaths]
WHERE continent IS NOT NULL
AND location IS NOT NULL
ORDER BY location, date
