-- First I'm going to select the data that I will be analyzing 

SELECT  
location,
date,
total_cases,
new_cases,
total_deaths,
population
FROM covid_deaths
order by 1,2
;

-- For this analisis we will be looking at the percentage of deaths during this period of time in the United States

SELECT  
location,
date,
total_cases,
total_deaths,
(CAST(total_deaths AS REAL) / total_cases) * 100 AS death_percentage
FROM covid_deaths
WHERE location LIKE '%states%'
order by 1,2
;

-- In this analysis we are looking at the percentage of the population that got infected in the United States

SELECT  
location,
date,
total_cases,
population,
(CAST(total_cases AS REAL) / population) * 100 AS infection_percentage
FROM covid_deaths
WHERE location LIKE '%states%'
order by location
;

-- For this part, we are looking at the countries with the highest infection rates compared to the population from 2020-2023

SELECT  
location,
date,
population,
MAX(total_cases) AS highest_infection_count,
MAX((CAST(total_cases AS REAL) / population) * 100) AS highest_infection_percentage
FROM covid_deaths
GROUP BY location, population
ORDER BY highest_infection_percentage DESC
;

-- The following analysis shows the countries witht highest death count per capita

SELECT  
location,
MAX(CAST(total_deaths AS INT)) AS total_death_count
FROM covid_deaths
GROUP BY location
ORDER BY total_death_count DESC
;

-- We will now review the total death count per continent

SELECT  
location,
MAX(CAST(total_deaths AS INT)) AS total_death_count
FROM covid_deaths
WHERE COALESCE(continent, '') = ''
GROUP BY location
ORDER BY total_death_count DESC
;


-- In the following analysis we will be looking at the death percentage per continent 

SELECT
location,  
date,
total_cases,
total_deaths,
(CAST(total_deaths AS REAL) / total_cases) * 100 AS death_percentage
FROM covid_deaths
WHERE COALESCE(continent, '') = ''
order by location
;


-- The following analysis shows the death percentage globally

SELECT  
SUM(new_cases) AS total_cases,
SUM(new_deaths) AS total_deaths,
SUM(CAST(new_deaths AS REAL)) / SUM(new_cases) * 100 AS death_percentage
FROM covid_deaths
WHERE COALESCE(continent, '') = ''
--GROUP BY date
;

-- In this analysis we are comparing the total population vs people vaccinated by using a CTE

WITH pop_vs_vac 
(continent, location, population, new_vaccinations, rolling_people_vaccinated) 
AS
(
SELECT dea.continent, dea.location, dea.population, vac.new_vaccinations,
SUM(vac.new_vaccinations) OVER (PARTITION BY dea.location)  AS rolling_people_vaccinated
FROM covid_deaths dea
JOIN covid_vaccinations vac
    ON dea.location = vac.location
    AND dea.date = vac.date
WHERE COALESCE(dea.continent, '') <> ''
ORDER BY 2,3   
) 
;
SELECT *, (rolling_people_vaccinated/population)*100 AS rolling_percentage_people_vaccinated
FROM pop_vs_vac
;

