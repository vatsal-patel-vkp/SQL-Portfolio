# COVID-19 Data Analysis Using SQL

## Description:

This SQL portfolio project focuses on analyzing COVID-19 data to gain valuable insights and trends related to the pandemic. 
The project showcases my proficiency in SQL queries, data manipulation, and analysis techniques.


## Data Sources:
The dataset used in this project is sourced from reliable and authoritative repositories, such as government health agencies, global health organizations, 
and reputable research institutions. It includes information on COVID-19 cases, deaths, recoveries, testing, demographic, and vaccination data.


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


-------------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------------


## SQL Code

SELECT * 
FROM PortfolioProject..[Covid-deaths]
WHERE continent IS NOT NULL
AND location IS NOT NULL
ORDER BY location, date

![image](https://github.com/vatsal-patel-vkp/SQL-Portfolio/assets/107895872/7394a8a2-11e2-4bce-9f6b-ceaf01a73646)


SELECT * 
FROM PortfolioProject..[Covid-Vaccination]
ORDER BY 3,4


SELECT location, date, population, total_cases, new_cases, total_deaths
FROM PortfolioProject..[Covid-deaths]
ORDER BY 1,2

![image](https://github.com/vatsal-patel-vkp/SQL-Portfolio/assets/107895872/e332895c-1c6a-404b-a5f6-6ebe54cdf59d)


ALTER TABLE [Covid-deaths]
ALTER COLUMN total_cases FLOAT

ALTER TABLE [Covid-deaths]
ALTER COLUMN total_deaths FLOAT


SELECT location, date, population, total_cases, total_deaths, (total_deaths/total_cases)*100 AS Death_Percentage
FROM PortfolioProject..[Covid-deaths]
ORDER BY 1,2


![image](https://github.com/vatsal-patel-vkp/SQL-Portfolio/assets/107895872/7f73c9c2-96ab-4952-b757-b71bbebffb8c)



SELECT location, date, population, total_cases, total_deaths, (total_deaths/total_cases)*100 AS Death_Percentage
FROM PortfolioProject..[Covid-deaths]
WHERE location IN ('canada', 'india', 'United States')
ORDER BY 1,2

![image](https://github.com/vatsal-patel-vkp/SQL-Portfolio/assets/107895872/2d0cf8fe-2980-47b4-a0d1-192ca69d3a01)


SELECT location, date,population, total_cases, (total_cases/population)*100 AS Percentage_getting_Covid
FROM PortfolioProject..[Covid-deaths]
WHERE location like '%Canada%'
ORDER BY location, date

![image](https://github.com/vatsal-patel-vkp/SQL-Portfolio/assets/107895872/c3e69230-4f23-4aeb-b4a4-72b922f876c3)


SELECT location, population, MAX(total_cases) AS TotalCases, MAX(total_cases/population)*100 AS Percent_of_population_getting_affected
FROM PortfolioProject..[Covid-deaths]
GROUP BY location, population
ORDER BY Percent_of_population_getting_affected DESC

![image](https://github.com/vatsal-patel-vkp/SQL-Portfolio/assets/107895872/ef4faf18-527c-4d95-ade5-f13fe3508e2f)


SELECT location, MAX(CAST(total_deaths AS INT)) AS Total_Deaths
FROM PortfolioProject..[Covid-deaths]
--WHERE continent IS NOT NULL
GROUP BY location
ORDER BY Total_Deaths DESC

![image](https://github.com/vatsal-patel-vkp/SQL-Portfolio/assets/107895872/1e520ce6-0621-46e8-9edb-148b668e528a)


SELECT location, population, MAX(CAST(total_deaths AS INT)) AS TotalDeaths, MAX(total_deaths/population)*100 AS DeathPercentage
FROM PortfolioProject..[Covid-deaths]
WHERE continent IS NOT NULL 
GROUP BY location, population
ORDER BY TotalDeaths DESC

![image](https://github.com/vatsal-patel-vkp/SQL-Portfolio/assets/107895872/793ce474-0070-4322-afee-c00538512668)



SELECT continent, MAX(CAST(total_deaths AS INT)) AS Total_Deaths
FROM PortfolioProject..[Covid-deaths]
GROUP BY continent
ORDER BY Total_Deaths DESC

![image](https://github.com/vatsal-patel-vkp/SQL-Portfolio/assets/107895872/b733ec95-dd44-4683-a8a0-952fb0ad1617)


SELECT continent, MAX(CAST(total_deaths AS INT)) AS Total_Deaths
FROM PortfolioProject..[Covid-deaths]
WHERE continent IS NOT NULL
GROUP BY continent
ORDER BY Total_Deaths DESC

![image](https://github.com/vatsal-patel-vkp/SQL-Portfolio/assets/107895872/76928683-50b4-4e1d-82b7-5327ca520190)


SELECT date, total_cases, total_deaths, (total_deaths/total_cases)*100 AS Death_Rate
FROM PortfolioProject..[Covid-deaths]
WHERE continent IS NOT NULL
ORDER BY 1,2
 
SELECT date, SUM(new_cases) AS New_Cases, SUM(new_deaths) AS New_DeathCases
FROM PortfolioProject..[Covid-deaths]
GROUP BY date

![image](https://github.com/vatsal-patel-vkp/SQL-Portfolio/assets/107895872/1a30527e-664b-4feb-b76b-5a86443b3bfd)

SELECT SUM(new_cases) AS Total_Cases, SUM(new_deaths) AS Total_DeathCases, SUM(new_deaths) / SUM(new_cases)*100 AS DeathPercentage
FROM PortfolioProject..[Covid-deaths]
WHERE continent IS NOT NULL
ORDER BY 1,2

![image](https://github.com/vatsal-patel-vkp/SQL-Portfolio/assets/107895872/81e49a30-0be8-41f7-844a-07f7ac86616e)


============================================================




-- Covid Vaccination

SELECT * 
FROM [Covid-Vaccination]

![image](https://github.com/vatsal-patel-vkp/SQL-Portfolio/assets/107895872/672fc387-5f80-4d70-8a4a-74811529dd7e)


SELECT * 
FROM [Covid-deaths] AS dea
JOIN [Covid-Vaccination] AS vacc
ON dea.location = vacc.location
AND dea.date = vacc.date

![image](https://github.com/vatsal-patel-vkp/SQL-Portfolio/assets/107895872/342287fe-7b44-4bd3-aece-5b0b087bc10c)


SELECT dea.date,dea.continent, dea.location, dea.population, vacc.new_vaccinations, SUM(CONVERT(float, vacc.new_vaccinations)) OVER (Partition by dea.location 
ORDER by dea.location, dea.date) as RollingPeopleVaccinated  
FROM [Covid-deaths] AS dea
JOIN [Covid-Vaccination] AS vacc
ON dea.location = vacc.location
AND dea.date = vacc.date
WHERE dea.continent IS NOT NULL
ORDER BY 1,3

![image](https://github.com/vatsal-patel-vkp/SQL-Portfolio/assets/107895872/aa07a93f-ac0a-4c76-babb-a798131d6532)


-- Using CTE

With Popvsvacc (date, continent, location, population, new_vaccinations, RollingPeopleVaccinated)
as
(
SELECT dea.date, dea.continent, dea.location, dea.population, vacc.new_vaccinations, SUM(CONVERT(float, vacc.new_vaccinations)) OVER (Partition by dea.location 
ORDER by dea.location, dea.date) as RollingPeopleVaccinated  
FROM [Covid-deaths] AS dea
JOIN [Covid-Vaccination] AS vacc
ON dea.location = vacc.location
AND dea.date = vacc.date
WHERE dea.continent IS NOT NULL
--ORDER BY 1,3
)
SELECT *, (RollingPeopleVaccinated/population)*100
FROM Popvsvacc

![image](https://github.com/vatsal-patel-vkp/SQL-Portfolio/assets/107895872/16fe036c-51cc-43ec-93ae-798e52abe1ba)


-- Temp Table

Create Table #PercentPopulationVaccinated
(
Continent nvarchar(255),
Location nvarchar(255),
Date datetime,
Population numeric,
New_Vaccinations numeric,
RollingPeopleVaccinated numeric
)

Insert into #PercentPopulationVaccinated
SELECT CAST(dea.date AS datetime2), dea.continent, dea.location, dea.population, vacc.new_vaccinations, SUM(CONVERT(float, vacc.new_vaccinations)) OVER (Partition by dea.location 
ORDER by dea.location, dea.date) as RollingPeopleVaccinated  
FROM [Covid-deaths] AS dea
JOIN [Covid-Vaccination] AS vacc
ON dea.location = vacc.location
AND dea.date = vacc.date
WHERE dea.continent IS NOT NULL
--ORDER BY 1,3

SELECT *, (RollingPeopleVaccinated/population)*100
FROM #PercentPopulationVaccinated
