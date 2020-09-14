# mod_2_citi_bike_model

## Introduction

Citi Bike is a Lyft-owned and operated bike-share service with over 1,000 Citi Bike stations located in Manhattan, Brooklyn, Queens, the Bronx and Jersey City. The service has experienced tremendous growth as people increasingly seek alternative methods for public transportation. In determining where to expand their services, Lyft would like to better understand the factors that are most highly correlated with high activity at any given Citi Bike Station.

## Methods

For this analysis, we used an Ordinary Least Squares (OLS) model to explore the relationship between a number of community, environmental, and spatial variables and ridership in New Jersey. We decided to use only New Jersey stations given the apparent large amounts of missing data from NYC bike stations. Of the nearly 850,000 entries in our dataset, fewer than 100 were from NYC bike stations.

For the sake of this analysis, ridership at a given station is defined as one point of contact with a station (i.e., if a rider starts or ends at a given location).

## Data Sources

- Citi Bike Trip History Data (08/01/2019 - 08/31/2020)
- Zip-Code-level Population Characteristics
- NOAA Weather Data (08/01/2019 - 08/01/2020)

## Results

<img width="712" alt="ols_results" src="https://user-images.githubusercontent.com/64563191/93050809-84cbca80-f631-11ea-9d81-0429d9146035.png">

Our OLS regression results show that the variables that seem to have the largest effect on daily ridership are:
- Temperature (+)
- Spring (dummy variable) (-)
- Median income (+)
- Distance to the PATH train (-)

However, with an R-squared value of 0.293, there is a lot of variance that we cannot account for with the variables we have included in our model.


**There is a moderately strong correlation between ridership and temperature.**

![temp_corr](https://user-images.githubusercontent.com/64563191/93051168-0e7b9800-f632-11ea-80d1-5b41bbfd4002.png)

R = 0.629151

p-value = 0.000000

The fairly high correlation coefficient of 0.63 would indicate that there seems to be a moderately strong correlation between average daily temperature and total daily ridership. This relationship is statistically significant.


**COVID-19 significantly impacted ridership in the spring of 2020.** 

Ridership seemed to be the lowest in the spring of 2020 which seemed to run contrary to the temperature findings, but it should be noted that our data contains the impact of COVID-19 on Citi Bike ridership in the spring of 2020. An ANOVA test confirmed that the differences in ridership between seasons are statistically significant. The images below depict the ridership over the past year.

![season_ridership](https://user-images.githubusercontent.com/64563191/93051257-2f43ed80-f632-11ea-8687-f45c901f0746.png)

![ridership_over_time](https://user-images.githubusercontent.com/64563191/93051249-2bb06680-f632-11ea-9f02-1f7a2a0d8b24.png)



**There seems to be a weak correlation between an area’s median income and ridership.**

![med_inc](https://user-images.githubusercontent.com/64563191/93050920-b5abff80-f631-11ea-9fe2-3fd094f67d6e.png)

R: 0.157882

p-value: 0.708853

There doesn’t seem to be a strong relationship between income and ridership, however, in our OLS regression, median income seemed to be one of the stronger predictors of median income. In this particular case, there is one zip code that contains most of the area’s citi bike stations and it’s likely median income is acting as a proxy for that zip code. It also seems to be the case that zip codes with lower median incomes also have fewer Citi Bike stations. Zip codes with higher median incomes are located near many stations, but residents may prefer to use their own means of transportation. As such, there’s a target demographic that seem to utilize Citi Bikes at higher rates than their nearby counterparts. Further exploration into the specific demographic characteristics of riders could help to better understand what contributes to ridership.


**There is a fairly weak negative correlation between distance to NJ PATH and ridership.** 

![dist_to_path](https://user-images.githubusercontent.com/64563191/93051037-da07dc00-f631-11ea-8db7-cf5eb4bfc528.png)

R: - 0.364822    

p-value: 0.007834

Bike stations located closer to PATH train stations experience higher average daily activity than those further away. This relationship is relatively weak but significant.



## Limitations and Considerations for Future Analyses

**Limitations:**
- Our data was confined to New Jersey Citi Bike Stations due to a large amount missing data from NYC Citi Bike stations. Gathering more data from NYC could help to better understand how Citi Bike ridership varies in communities that are more diverse than just Jersey City.
- A zip code analysis may have been too large an area to draw any meaningful insights from differences in ridership by community area. A more granular analysis of city blocks could have helped to understand variations in ridership from one station to the next.

**Considerations for future work:**
- Including neighborhood-level crime statistics
- Creating a feature to capture the number of  restaurants and bars that fall within a 100 foot radius of each bike station.
