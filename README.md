# data-512-a7
This repo contains the final report, code, data documentation, and supporting materials associated with the each of the following assignments:
- A4: Common Analysis sets the stage for the subsequent assignments. In A4 you conduct a base analysis. All of the students in the class will conduct the same analysis, but with a slightly different data subset.
  - Analysis question: How did masking policies change the progression of confirmed COVID-19 cases from February 1, 2020 through October 15, 2021?
  - Data subset: Worcester, Massachusetts 
- A5: Extension Plan will require you to ask a human centered data science question that extends the work in A4: Common Analysis. 
  -  Analysis question: To what extent does weather explain the increase in infection rate of COVID-19 in Worcester, Massachusetts over time? [...] Given the complexity of the problem, I do not anticipate an extremely good predictor, but more so an idea of which pieces of information are most useful and what percentage of the variability in the covid case fluctuates can be accounted for by weather metrics. 
- A6: Presentation will require you to give a modified (shorter) PetchaKucha presentation of your completed project.
- A7: Final Report requires a written submission of a project report.

# Data sources

Descriptions of data used in A4 and A5 assignments and utilized in one or both Jupyter notebooks included in this repo:
- ‘COVID-19 Data Repository by the Center for Systems Science and Engineering (CSSE) at Johns Hopkins University’ sourced through Kaggle dataset ‘COVID-19 data from John Hopkins University’
  - [Link](https://www.kaggle.com/antgoldbloom/covid19-data-from-john-hopkins-university/activity)
  - [Documentation: Original repo](https://github.com/CSSEGISandData/COVID-19)
  - Licensed under: [Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/)
  - Contains: Confirmed cases and deaths by US county daily, both as cumulative and new cases per day.
  - Quirks: Negative new cases (or decreasing cumulative values) are a known issue documented in the discussions on kaggle. Within my county only one day contained a negative value of new cases (September 3rd, 2020). However if we are right to interpret the discrepancy as a retroactive correction being applied then on a day when there were sufficient cases to exceed the correction it could still be positive.
- U.S. State and Territorial Public Mask Mandates From April 10, 2020 through August 15, 2021 by County by Day 
  - State and territorial executive orders, administrative orders, resolutions, and proclamations are collected from government websites and cataloged and coded using Microsoft Excel by one coder with one or more additional coders conducting quality assurance. These data are derived from publicly available state and territorial executive orders, administrative orders, resolutions, and proclamations (“orders”) for COVID-19 that expressly require individuals to wear masks in public found by the CDC, et al. [Excerpt source](https://data.cdc.gov/Policy-Surveillance/U-S-State-and-Territorial-Public-Mask-Mandates-Fro/62d6-pm5i)
  - [Link](https://data.cdc.gov/Policy-Surveillance/U-S-State-and-Territorial-Public-Mask-Mandates-Fro/62d6-pm5i)
  - [Documentation](https://data.cdc.gov/Policy-Surveillance/U-S-State-and-Territorial-Public-Mask-Mandates-Fro/62d6-pm5i)
  - Licensed under: Public domain
  - Contains: State and county identifiers, date, binary field for masks required, source, url, and citation for the order.
  - Quirks: Binary field Face_Masks_Required_in_Public equal to ‘Yes’ is defined by potentially multiple policies. Defined as ‘a requirement for individuals operating in a personal capacity to wear masks 1) anywhere outside their homes or 2) both in retail businesses and in restaurants/food establishments.’ More explicit details are available via url to the corresponding order.
- Masking survey by “The New York Times and Dynata”
  - This data comes from a large number of interviews conducted online by the global data and survey firm Dynata at the request of The New York Times. The firm asked a question about mask use to obtain 250,000 survey responses between July 2 and July 14, enough data to provide estimates more detailed than the state level. (Several states have imposed new mask requirements since the completion of these interviews.) Specifically, each participant was asked: How often do you wear a mask in public when you expect to be within six feet of another person? This survey was conducted a single time, and at this point we have no plans to update the data or conduct the survey again. [Excerpt source](https://github.com/nytimes/covid-19-data/tree/master/mask-use)
  - [Link](https://github.com/nytimes/covid-19-data/tree/master/mask-use)
  - [Documentation](https://github.com/nytimes/covid-19-data/tree/master/mask-use)  
  - Licensed under: https://github.com/nytimes/covid-19-data/blob/master/LICENSE 
  - Contains: Proportion of each county that is estimated to wear their mask “in public when [they] expect to be within six feet of another person” either never, rarely, sometimes, frequently, or always.
Quirks: Snapshot data, uses weighted proportions of 200 nearest respondents to aggregate to census tracts and then weights by population to create county level data.
- Global Historical Climatology Network - WBAN:94746 Station
  - The Global Historical Climatology Network daily (GHCNd) is an integrated database of daily climate summaries from land surface stations across the globe. GHCNd is made up of daily climate records from numerous sources that have been integrated and subjected to a common suite of quality assurance reviews.
GHCNd contains records from more than 100,000 stations in 180 countries and territories. NCEI provides numerous daily variables, including maximum and minimum temperature, total daily precipitation, snowfall, and snow depth. About half the stations only report precipitation. Both record length and period of record vary by station and cover intervals ranging from less than a year to more than 175 years. [Excerpt source](https://www.ncei.noaa.gov/products/land-based-station/global-historical-climatology-network-daily)
  - Links: 
    - [Climate Data Online: Dataset Discovery](https://www.ncdc.noaa.gov/cdo-web/datasets)
    - [Climate Data Search Online](https://www.ncdc.noaa.gov/cdo-web/search)
    - Note: In both sources referenced as ‘Daily Summaries’
  - [Documentation](https://www1.ncdc.noaa.gov/pub/data/cdo/documentation/GHCND_documentation.pdf)
  - Licensed under: Public domain, NOAA’s data is “available to the public without restriction on use”
  - Contains: See description above
  - Quirks: Data availability day-to-day and station-to-station is unpredictable and must be carefully assessed when selecting which source(s) and fields to use.
- Local Climatological Data - WBAN:94746 Station
  - Local Climatological Data (LCD) consist of hourly, daily, and monthly summaries for approximately 950 U.S.  Automated Surface Observing System (ASOS) stations, as well as observations collected every 20 minutes from around 1,400 U.S. Automated Weather Observing System (AWOS) stations. Data is also available for U.S. Climate Reference Network (USCRN) stations and a small number of stations at international U.S. facilities. [Excerpt source](https://www.ncei.noaa.gov/products/land-based-station/local-climatological-data)
  - [Link](https://www.ncdc.noaa.gov/cdo-web/datatools/lcd)
  - [Documentation](https://www1.ncdc.noaa.gov/pub/data/cdo/documentation/LCD_documentation.pdf)
  - Licensed under: Public domain, NOAA’s data is “available to the public without restriction on use”
  - Contains: Measurements on precipitation, wind, pressure, humidity, snowfall, visibility, etc. aggregated to the hour, day, and month.
  - Quirks: Alphanumeric flags may be included with or instead of measurement values designating potential issues or special cases. Therefore particular cleaning is required for these fields to overcome data type issues in pandas. Data availability day-to-day and station-to-station is unpredictable and must be carefully assessed when selecting which source(s) and fields to use.
