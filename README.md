# Dissertation Work
The following is part of the code that I utilized to pull, organize, and clean Census data for my doctoral dissertation.
## Scope
In this sample, I analyzed and compared the residential distribution of Venezuelan, Cuban, and Puerto Rican migrants in Houston, TX. Houston is not a traditional migrant destination for any of these three groups: U.S.-bound Puerto Rican migration has traditionally been associated with the Northeast and Chicago, while Cuban and Venezuelan migration has generally gravitated towards South Florida. My goal was to gauge the social mobility of migrants in a new destination and understand the impact that migrants have on the local communities. Therefore, I utilize spatial regressions to compare socio-edonomic changes in the neighborhoods with the highest percent change in the selected migrant groups. 
## Data
Data for this research includes three different datasets: the U.S. Census Bureaus
American Community Survey (ACS) individual-level data, and ACS tract-level data. 
1. The first ACS dataset includes data gathered by the U.S. Census from 2005 to 2019 (repeated cross-section). 
2. The second dataset was comprised of census tract data from the ACS collected by the U.S. Census. This second datasets includes the 2010 and 2015 5-years estimates, which are based on data collected over the 5 year periods (2010 to 2014 and 2015-2019, respectively) and describes the average characteristics for those time periods.

## Methods
The analyses included here include 4 different statistical models: descriptive statistics, OLS regression, spatial autoregressive lag, and sparse spatial models. 

1. I utilized an **OLS regression** to test for the effects of birthplace on logged income and socioeconomic index (HWSEI). The OLS had four different blocks:  predicting income or HWSEI with dummy variables for birthplace, 2) and 3) introducing control variables (employment, age, family size, marital status, employment history, and educational attainment), and 4) testing the race and ethnic interaction variables. 
2. I performed **descriptive statistical analysis ** to analyze and compare neighborhood characteristics. The goal of this was to better understand the residential and sociographic characteristics of the spaces that our target populations chose as their home.
3. I employed a **spatial autoregressive lag model ** (SAR or Spatial Lag) to measure the global effects of population changes across census tracts. The SAR model can perform this analysis by calculating how the outcome variable in one area (census tract) is affected by the outcomes in nearby areas, covariates from nearby areas, and errors from nearby areas. 
4.  I built a **Sparse Spatial Genealized Model** (SSGLM) to test for spatial autocorrelation between the outcome variables and the key independent variables. SSGLMS can reduce the interference of spatial confounding and improve regression inference (Hughes & Haran, 2013). Like the GLM, the SSGLM utilizes eigenvectors that exhibit spatial dependence, improving the speed of the calculation.  I opted for a Gaussian linear model given the distribution of Delta Non-Hispanic Black score.
## Findings
First, we can easily notice the steady increase of all three populations in Harris County between 2005 and 2019


