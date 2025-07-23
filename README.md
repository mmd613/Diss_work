# Dissertation Work
The following is part of the code that I utilized to pull, organize, and clean Census data for my doctoral dissertation.

**TL;DR** I ran a variety of advanced statistical models (OLS, LAGSAR, SSGLM) to analyze the demographics of the incoming Cuban, Venezuelan, and Puerto Rican migrants in Houston, TX and the impact of this entrance on local neighborhood composition. Results show there is a **negative correlation** between a change in the proportions of Cuban and non-Hispanic Blacks. Analysis was run in R and STATA, and visualized in R and Excel. 
## Scope
In this sample, I analyzed and compared the residential distribution of Venezuelan, Cuban, and Puerto Rican migrants in Houston, TX. Houston is not a traditional migrant destination for any of these three groups: U.S.-bound Puerto Rican migration has traditionally been associated with the Northeast and Chicago, while Cuban and Venezuelan migration has generally gravitated towards South Florida. My goal was to gauge the social mobility of migrants in a new destination and understand the impact that migrants have on the local communities. Therefore, I utilize spatial regressions to compare socio-economic changes in the neighborhoods with the highest percent change in the selected migrant groups. 
## Data
Data for this research includes three different datasets: the U.S. Census Bureau American Community Survey (ACS) individual-level data, and ACS tract-level data. 
1. The first ACS dataset includes data gathered by the U.S. Census from 2005 to 2019 (repeated cross-section). 
2. The second dataset was comprised of census tract data from the ACS collected by the U.S. Census. This second dataset includes the 2010 and 2015 5-year estimates, which are based on data collected over the 5-year periods (2010 to 2014 and 2015-2019, respectively) and describe the average characteristics for those time periods.
## Platforms
I use a variety of platforms for the analysis, like Microsoft Office (Excel), STATA, and R (tidyverse, tidycensus, spatialreg, purrr, and others). 
## Methods
The analyses included here include 4 different statistical models: descriptive statistics, OLS regression, spatial autoregressive lag, and sparse spatial models. 

1. I utilized an **OLS regression** to test for the effects of birthplace on logged income and socioeconomic index (HWSEI). The OLS had four different blocks:  predicting income or HWSEI with dummy variables for birthplace, 2) and 3) introducing control variables (employment, age, family size, marital status, employment history, and educational attainment), and 4) testing the race and ethnic interaction variables. 
2. I performed **descriptive statistical analysis ** to analyze and compare neighborhood characteristics. The goal of this was to better understand the residential and sociographic characteristics of the spaces that our target populations chose as their home.
3. I employed a **spatial autoregressive lag model ** (SAR or Spatial Lag) to measure the global effects of population changes across census tracts. The SAR model can perform this analysis by calculating how the outcome variable in one area (census tract) is affected by the outcomes in nearby areas, covariates from nearby areas, and errors from nearby areas. 
4.  I built a **Sparse Spatial Generalized Model** (SSGLM) to test for spatial autocorrelation between the outcome variables and the key independent variables. SSGLMS can reduce the interference of spatial confounding and improve regression inference (Hughes & Haran, 2013). Like the GLM, the SSGLM utilizes eigenvectors that exhibit spatial dependence, improving the speed of the calculation.  I opted for a Gaussian linear model given the distribution of Delta Non-Hispanic Black score.
## Findings
First, we can easily notice the steady increase of all three populations in Harris County between 2005 and 2019: 
<p align="center">
  <img src="https://github.com/mmd613/Diss_work/blob/main/Figure%201-%20Total%20Population%20for%20Cuban-born%2C%20Puerto%20Rican-born%2C%20and%20Venezuelan-born%20in%20Harris%20County%2C%20TX%20.png">
</p> 

When we compare populations in Houston, we see that Cubans have higher percentages of men and Black Hispanics. Almost 60% of the Venezuelans have a college degree, double the proportion of Cubans (28%) and of Puerto Ricans (37%). Likewise, Venezuelans have a higher percentage of personal or individual income, while Cubans had the lowest ($33k). Overall, Venezuelans seem to have higher socioeconomic status while Cubans had the highest rates of poverty and lowest rates of homeownership. 
<p align="center">
  <img src="https://github.com/mmd613/Diss_work/blob/main/Table%201%20Sociodemo.png">
</p>

But how statistically sound are these assumptions? Using an OLS, I find that Puerto Ricans have a higher income than Venezuelans and Cubans, while controlling for all relevant social and economic variables. 
<p align="center">
  <img src="https://github.com/mmd613/Diss_work/blob/main/Screenshot%202025-07-23%20at%2014.49.49.png">
</p>

When analyzing socioeconomic prestige, Venezuelans and Puerto Ricans have a much higher socioeconomic index score than Mexicans. Meanwhile, Cubans are almost on par with Mexicans in terms of SEI. These two models suggest that all three groups are faring better than Mexican-born migrants in Harris County and that Venezuelans and Puerto Ricans enjoy better socioeconomic outcomes. 
<p align="center">
  <img src="https://github.com/mmd613/Diss_work/blob/main/Screenshot%202025-07-23%20at%2014.50.29.png">
</p>

When looking at the distribution of Hispanics in Houston, we  observe that migrant enclaves are concentrated in the outer rings of Houston, mostly southwest, west, and northeast. For the remainder of this analysis, I focus on six census tracts that observed the highest increases of all three populations (Cubans, Venezuelans, and Puerto Ricans). 
<p align="center">
  <img src="https://github.com/mmd613/Diss_work/blob/main/Hisp%20Tot.png">
</p>

For my Spatial Lag and Sparse Spatial GL models, I utilized four neighborhood-based change score variables as my outcomes: average income, poverty rate, proportion of non-Hispanic Whites, and proportion of non-Hispanic Blacks. After applying a variety of relevant socioeconomic variables for control and running diagnostic tests (like Monte Carlo and Moran tests), I landed on one statistically significant outcome. There was a meaningful interaction between a change in the Cuban population and the non-Hispanic Black population. Below, you will see the results of the Spatial Lag model, which found that census tracts that had a **percent increase** in Cuban population had a **decrease** (-2.68) in their non-Hispanic Black population.
<p align="center">
  <img src="https://github.com/mmd613/Diss_work/blob/main/Screenshot%202025-07-23%20at%2014.52.36.png">
</p>

The SSGLM also rendered similar results: the Cuban-born population and the non-Hispanic Black population share a negative correlation. 
<p align="center">
  <img src="https://github.com/mmd613/Diss_work/blob/main/Screenshot%202025-07-23%20at%2014.53.01.png">
</p>

I was able to map the residuals of the SSGLM in R, which allowed me to see which neighborhoods had the highest increases in Cuban-born population (shown in yellow)
<p align="center">
  <img src="https://github.com/mmd613/Diss_work/blob/main/Screenshot%202025-07-23%20at%2014.58.22.png?raw=true">
</p>

Inversely, here are the sharpest drops in Cuban-born population (shown in yellow)
<p align="center">
  <img src="https://github.com/mmd613/Diss_work/blob/main/Screenshot%202025-07-23%20at%2014.58.39%202.png?raw=true">
</p>

As I built these models--going from simple regressions to spatial autoregressions--I ran tests and plotted graphs to make sure I was headed the right way. Here are some examples. The GLM residuals show that the fitted residuals are somewhat clustered around positive predicted values for Delta Non-Hispanic Black, suggesting that there might be another socioeconomic characteristic missing in my model that could better explain this correlation. 
<p align="center">
  <img src="https://github.com/mmd613/Diss_work/blob/main/Screenshot%202025-07-23%20at%2014.57.28.png?raw=true">
</p>

## Conclusion
Here are the two main takeaways from this sample analysis:
1. I found that Puerto Rican and Venezuelan Migrants were faring better than Cuban and Mexican migrants in Houston, which contrasts past research where Puerto Ricans trailed behind most migrant groups. 
2. The entrance of Cubans into inner-city neighborhoods of Houston has a displacing effect on the local non-Hispanic Black population. While this research could not explain *why*, it demonstrated a nuanced method for measuring the direct and indirect effects of migration in neighborhood demographic composition. 
