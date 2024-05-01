# Global Insights: Analysing Socio-Economic and Environmental Trends
## Introduction
Our world is becoming increasingly interconnected through different means such as social media, transportation, cultural exchanges, global trade etc. Understanding the different dynamics of countries globally is key for understanding the challengies and opportunities that shape our present and future.

In this project, I will be looking at the 'Global Country Information Dataset 2023' in detail to understand the relationships and trends between a wide range of socio-economi, environmental, demographic indicators and countries of the world. The dataset consists of many data points, including but not limited to: population density, birth rates, GDP and life expectancy. This dataset not only enables a deep dive into individual country profiles, but also enables for a comparative and correlational analysis across various metrics.

Dataset sourced from: https://www.kaggle.com/datasets/nelgiriyewithana/countries-of-the-world-2023.

## Primary Objectives of Project
1. Analyze population density and land area to explore spatial distribution patterns and understand the implications of population spread in relation to resources and infrastructure.
2. Investigate the relationship between the percentage of agricultural land and indicators of food security, drawing connections to sustainability practices and economic stability.
3. Examine the impact of carbon dioxide emissions on environmental health and climate change, integrating discussions on global policies and their effectiveness.
4. Explore the interplay between economic indicators such as GDP, tax revenue, and employment with socio-economic outcomes to assess economic health and development strategies.
5. Study educational enrollment rates across primary and tertiary levels to gauge the progress in human capital development and its impact on economic growth and social advancement.
6. Analyze healthcare metrics, including infant mortality and life expectancy, to evaluate the well-being and quality of life across different regions.
7. Examine labor market dynamics, investigating factors such as labor force participation and unemployment rates, to understand their implications on national economic conditions and individual livelihoods.
8. Investigate urbanization trends to comprehend their social, economic, and environmental consequences, emphasizing the challenges and opportunities of urban growth.

## Tools 
MySQL: Primary programming language used for data querying, manipulation and analysis.

PowerBI: For advanced data visualization and analysis.

## Project Structure
The project directory is organised as follows to ensure easy access and management of project resources:

'/data' - Contains the raw CSV files downloaded from Kaggle.

'/Queries' - SQL scripts and other code files used in the analysis.

'/PowerBI Visualisation' - PowerBI visualisation file.

## Methodology

Initially, I obtained and downloaded the dataset from Kaggle. After downlaoding the data, I exported the file in Excel and scanned through the dataset, looking for missing columns, inconcistencies which I made sure to clean out before starting my analysis. I then ram basic SQL queries on MySQL to ensure the data has been loaded correctly. Examples of such queries were: SELECT * FROM Global_Countries LIMIT 10;

I ran into a problem when attempting to import the data onto MySQL. Whilst importing the data, MySQL kept returning an error message indicating the datatypes did not match. For example, I set one of my columns as INT when the actual data had empty values or special character. To resolve this issue, I cleansed the data by removing special characters such as commas and percentage signs and replacing empty strings with the 'NULL' value.

## Results & Findings

## Conclusion

