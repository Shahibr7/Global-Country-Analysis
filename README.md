# Global Insights: Analysing Socio-Economic and Environmental Trends
## Introduction
Our world is becoming increasingly interconnected through different means such as social media, transportation, cultural exchanges, global trade etc. Understanding the different dynamics of countries globally is key for understanding the challengies and opportunities that shape our present and future.

In this project, I will be looking at the 'Global Country Information Dataset 2023' in detail to understand the relationships and trends between a wide range of socio-economi, environmental, demographic indicators and countries of the world. The dataset consists of many data points, including but not limited to: population density, birth rates, GDP and life expectancy. This dataset not only enables a deep dive into individual country profiles, but also enables for a comparative and correlational analysis across various metrics.

Dataset sourced from: https://www.kaggle.com/datasets/nelgiriyewithana/countries-of-the-world-2023.

## Tools 
MySQL: Primary programming language used for data querying, manipulation and analysis.

PowerBI: For advanced data visualization and analysis.

## Project Structure
The project directory is organised as follows to ensure easy access and management of project resources:
'/MySQL Scripts and hypothesis' - This is an excel which refers to all of the SQL queries used for this project and their respective results.

'/PowerBI Visuals' - PowerBI visualisation file.

## Methodology

Initially, I obtained and downloaded the dataset from Kaggle. After downlaoding the data, I exported the file in Excel and scanned through the dataset, looking for missing columns, inconcistencies which I made sure to clean out before starting my analysis. I then ram basic SQL queries on MySQL to ensure the data has been loaded correctly. Examples of such queries were: SELECT * FROM Global_Countries LIMIT 10;

I ran into a problem when attempting to import the data onto MySQL. Whilst importing the data, MySQL kept returning an error message indicating the datatypes did not match. For example, I set one of my columns as INT when the actual data had empty values or special character. To resolve this issue, I cleansed the data by removing special characters such as commas and percentage signs and replacing empty strings with the 'NULL' value.

## Questions + Hypothesis
### Economic Development:
Question: How does GDP correlate with life expectancy across countries?

Hypothesis: Higher GDP is associated with higher life expectancy. This could be as a result of many factors, such as access to better healthcare.

### Healthcare Analysis:
Question: How does the availability of physicians per thousand people impact infant mortality rates?

Hypothesis: Greater availability of physicians correlates with lower infant mortality rates, suggesting better healthcare access results I improved health outcomes. 

### Education and Development
Question: What relationship exists between primary, tertiary education enrollment and unemployment rate?

Hypothesis: Higher education enrollment are associated with lower unemployment rates, suggesting that better education contributes to improved job opportunities and economic stability.

## Results & Findings
### 1. How does GDP correlate with life expectancy across countries?

Based on the project analysis of the latest dataset, here is what I found regarding the correlation between GDP and life expectancy:

After analysing and comparing the top 10 countries with the highest GDP against the top 10 countries with the lowest GDP, a clear correlation emerged. Countries with higher GDP tend to have higher life expectancies. Below is a summary of the data gathered:

- Average GDP of all countries: $492.48 billion
- Average life expectancy of all countries: 72.28 years
- Average GDP of top 10 highest GDP countries: $6.43 trillion
- Average life expectancy of top 10 highest GDP countries: 79.50 years
- Average GDP of top 10 lowest GDP countries: $517.04 million
- Average life expectancy of top 10 lowest GDP countries: 70.37 years

The above results show that the average life expectancy of all countries is 72.28 years. Countries with higher GDP have a life expectancy above this average, at 79.50 years, while countries with lower GDP have a life expectancy below the overall average, at 70.37 years. However, this analysis is based on extreme records, focusing on countries with the highest and lowest GDP, which may not be representative of the entire dataset. To gain a more comprehensive understanding, I further analyzed the data using the following SQL query:

( WITH AverageEcon AS (
    SELECT AVG(gdp_dollars) AS Average_gdp,
           AVG(life_expectancy) AS Average_life_expectancy
           FROM world
           WHERE gdp_dollars IS NOT NULL AND life_expectancy IS NOT NULL
)
SELECT country, gdp_dollars, life_expectancy,
CASE WHEN gdp_dollars > (SELECT Average_gdp FROM AverageEcon) AND life_expectancy > (SELECT Average_life_expectancy FROM AverageEcon) THEN 'Above Average'
     WHEN gdp_dollars < (SELECT Average_gdp FROM AverageEcon) AND life_expectancy < (SELECT Average_life_expectancy FROM AverageEcon) THEN 'Below Average'
     WHEN gdp_dollars > (SELECT Average_gdp FROM AverageEcon) AND life_expectancy < (SELECT Average_life_expectancy FROM AverageEcon) THEN 'High GDP, Low Life Expectancy'
     WHEN gdp_dollars < (SELECT Average_gdp FROM AverageEcon) AND life_expectancy > (SELECT Average_life_expectancy FROM AverageEcon) THEN 'Low GDP, High Life Expectancy'
     ELSE 'Unusual Case'
END AS 'Relationship Between gdp and life expectancy'
FROM world 
WHERE gdp_dollars IS NOT NULL AND life_expectancy IS NOT NULL; )

This code allowed me to categorize countries based on their GDP and life expectancy into four categories:

- High GDP and high life expectancy
- Low GDP and low life expectancy
- High GDP and low life expectancy
- Low GDP and high life expectancy

Using this analysis provided a better representation of the whole data. I noticed that 83 countries fell into the category of 'Low GDP, High Life Expectancy'. A good example is San Marino, a country with a GDP much lower than the average but with a life expectancy of 85.4 years, which is much higher than the average of 72.28 years. This suggests that GDP is not a perfect metric for studying life expectancy. A better metric would be GDP per capita, as it would provide a better measure of individual prosperity. However, this was a limitation of the dataset, which only included the total GDP of a country.

To further understand what metrics drive higher or lower life expectancy, I used the following SQL queries:

( SELECT * 
FROM world  
WHERE life_expectancy >= 77; )

( SELECT * 
FROM world  
WHERE life_expectancy <= 67; )

These queries returned all data for countries whre the life expectancy was 77 and higher, and 67 and lower, resepctively. I compared the average results of certain metrics between the two result sets. Below is a summary of the findings:

Average results for countries with life expectancy greater than 77:
- Density per km²: 415.1
- Birth rate: 11.2
- CO2 emissions: 421,745.4 tons
- GDP: $1.396 trillion
- Primary education enrollment: 1.02
- Tertiary education enrollment: 0.64
- Infant mortality: 4.58 per 1,000 live births
- Life expectancy: 80.55 years
- Physicians per thousand: 3.32
- Population: 50.65 million
- Urban population: 35.55 million

Average results for countries with life expectancy 67 and less:  
- Density per km²: 97.6
- Birth rate: 33.5
- CO2 emissions: 18,662.2 tons
- GDP: $39.18 billion
- Primary education enrollment: 1.00
- Tertiary education enrollment: 0.09
- Infant mortality: 48.95 per 1,000 live births
- Life expectancy: 61.80 years
- Physicians per thousand: 0.21
- Population: 26 million
- Urban population: 10.3 million

#### Interpretation of Results:
Countries with higher life expectancy generally have better healthcare, higher educational enrolment rates, greater economic wealth (higher GDP), and higher levels of urbanisation. These factors significantly contribute to the overall well-being and longevity of the population. Conversely, countries with lower life expectancy struggle with higher infant mortality rates, lower economic output (much lower Co2 emissions), fewer healthcare professionals, and lower levels of tertiary education. 

### 2. How does the availability of physicians per thousand people impact infant mortality rates?

Based on my analysis, the higher the availability of physicians per thousand people, the lower the infant mortality rate of a country. This is clearly shown in my Power BI visualisation.

I used the following SQL query:

( SELECT 
    country,
    physicians_per_thousand,
    infant_mortality,
    CASE
        WHEN physicians_per_thousand >= 2.0 THEN 'High Physicians'
        WHEN physicians_per_thousand >= 1.0 AND physicians_per_thousand < 2.0 THEN 'Moderate Physicians'
        ELSE 'Low Physicians'
    END AS physician_availability_category
FROM world
WHERE physicians_per_thousand IS NOT NULL AND infant_mortality IS NOT NULL
ORDER BY physician_availability_category, infant_mortality; )

This code categorised countries ased on the availability of physicians and retrieved data on infant mortality rates. The countries were categorised based on the number of physicians available into 'High Physicians', 'Moderate Physicians', and 'Low Physicians'. I calculated the average infant mortality rate for countries in each category and found a correlation.
- Average infant mortality rate for countries with 'High Physicians': 6.55 per 1,000 live births
- Average infant mortality rate for countries with 'Moderate Physicians': 15.37 per 1,000 live births
- Average infant mortality rate for countries with 'Low Physicians': 37.29 per 1,000 live births

### 3. What relationship exists between primary, tertiary education enrolment and unemployment rate?

Through my analysis, I found no strong relationship between education enrollment levels and unemployment rates across countries. Many countries with high education enrollments had similar unemployment rates to those with low education enrollments. However, this does not diminish the importance of education.

Based on my previous analysis comparing countries with life expectancy above 77 and those below 67, I observed a significant difference in tertiary education enrollment. While both sets of countries had similar primary education enrollment, countries with higher life expectancy had, on average, much higher tertiary education enrollment. This suggests better opportunities for education in more developed countries. While higher education may not directly reduce unemployment rates, it provides opportunities for better job prospects that may not be available in less developed countries.

## Conclusion

The analysis reveals significant insights into the factors influencing life expectancy and the availability of healthcare professionals. Higher GDP generally correlates with higher life expectancy, but GDP per capita would be a more accurate metric for individual prosperity. Countries with better healthcare, higher educational enrolment, and greater economic wealth tend to have higher life expectancies. Additionally, the availability of physicians is directly related to lower infant mortality raltes, highlighting the importance of healthcare access. 

The relationship between education enrolment and unemployment rate is less clear, indicating that while education is crucial for individualdevelopment and opportunities, it may not directly impact unemployment rates in all contexts. This analysis underscores the multifaceted nature of development and the need for comprehensive approaches to improve life expectancy and economic well-being.
