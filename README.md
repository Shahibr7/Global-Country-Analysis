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

'/data' - Contains the raw CSV files downloaded from Kaggle.

'/MySQL Scripts and hypothesis' - This is an excel which refers to all of the SQL queries used for this project and their respective results.

'/PowerBI Visuals' - PowerBI visualisation file.

## Methodology

Initially, I obtained and downloaded the dataset from Kaggle. After downlaoding the data, I exported the file in Excel and scanned through the dataset, looking for missing columns, inconcistencies which I made sure to clean out before starting my analysis. I then ram basic SQL queries on MySQL to ensure the data has been loaded correctly. Examples of such queries were: SELECT * FROM Global_Countries LIMIT 10;

I ran into a problem when attempting to import the data onto MySQL. Whilst importing the data, MySQL kept returning an error message indicating the datatypes did not match. For example, I set one of my columns as INT when the actual data had empty values or special character. To resolve this issue, I cleansed the data by removing special characters such as commas and percentage signs and replacing empty strings with the 'NULL' value.

## Questions + Hypothesis
### Economic Development:
Question: How does GDP correlate with life expectancy across countries?

Hypothesis: Higher GDP is associated with higher life expectancy. This could be as a result of many factors, such as access to better healthcare.

### Environmental Impact:
Question: Is there a correlation between population density and CO2 emissions:

Hypothesis: Higher population densities are positively correlated with higher CO2 emissions, reflecting the environmental impact of denser human settlements.

### Healthcare Analysis:
Question: How does the availability of physicians per thousand people impact infant mortality rates?

Hypothesis: Greater availability of physicians correlates with lower infant mortality rates, suggesting better healthcare access results I improved health outcomes. 

### Education and Development
Question: What relationship exists between primary, tertiary education enrollment and unemployment rate?

Hypothesis: Higher education enrollment are associated with lower unemployment rates, suggesting that better education contributes to improved job opportunities and economic stability.

## Results & Findings

## Conclusion

