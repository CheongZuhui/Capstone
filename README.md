# Capstone Project: Singapore air traffic forecasting
This repository contains my capstone project on predicting air passenger volume at Changi Airport.\ 
Being one of the busiest international airports in the world, Singapore Changi Airport continues to face challenges in ensuring there is sufficient capacity to meet rising demands while maintaining smooth operations and positive passenger experience to remain competitive. At the same time, it is also set to face competition from other regional air hubs for traveller and passenger traffic.

In view of these challenges, this project aims to:\
(1) Analyse the trends/patterns of air passenger traffic at Changi Airport and identify any possible opportunities for growth\
(2) Predict how the number of air passengers will change in the future years in order to facilitate better resource planning
(3) Use forecasting model to look at the recovery of air passenger volume post-COVID-19

## Questions we aim to answer
1. Is there any trends and seasonal patterns in air passenger traffic at Singapore Changi Airport?
2. Is there any potential opportunities based on the analyses that Changi Airport could explore to help capture more air passenger traffic?
3. Are we able to build a model to predict future trends of air traffic figures?
4. How would air traffic have been like without COVID-19? And how is the recovery based on predicted air passenger numbers?

## Dataset
Air passenger traffic data is obtained from [SingStat](https://www.singstat.gov.sg/find-data/search-by-theme/industry/transport/latest-data) 
+ Civil Aircraft Arrivals And Departures, Passengers, Air Cargo Tonnage, Direct And Transhipment Tonnage And Mail - Changi Airport
+ Air Passenger Departures By Region/Country Of Disembarkation, Monthly
+ Air Passenger Arrivals By Region/Country Of Embarkation, Monthly

These datasets contains the number of passengers arriving, departing and transiting through Changi Airport, including breakdown by regions of embarkation/disembarkation.\ 
Note: The timeframe in the analysis is limited to Jan 1989 till date as we will only be focusing on Changi Airport.

## Summary of Exploratory Data Analysis
![image](https://github.com/user-attachments/assets/2fe6a3aa-f537-43be-ac60-aa96e12c29bb)
+ Overall increasing trend in terms of no. of passengers handled by Changi Airport over the years, except years 2003 and 2020 where there was dips in the passenger volume due to SARS outbreak and COVID-19 pandemic respectively.

![image](https://github.com/user-attachments/assets/088f4c5e-6bc1-4dc0-bd58-891bd264b122)
+ Average no. of passengers handled by Changi Airport is highest in months of December, January, July and August. This corresponds to months of winter and summer holidays during leisure travel could likely have been higher.

![image](https://github.com/user-attachments/assets/5cefed8f-0bd1-48ac-a863-e1226ddccafc)
Breakdown of numbers by regions showed that:
+ South East Asia has always been the top region in terms of passenger volume, followed by North East Asia
+ Passenger volume from South Asia growing strong, overtaking Oceania in 2012
+ Passenger volume from North America and Middle East remained relatively low, with limited growth over the years

## Modelling
Pre-COVID data (i.e. up till Dec 2019) was used to build a time-series forecasting model to predict total monthly air passenger volume.

### Model 1: Auto-ARIMA
Model identified with lowest AIC: ARIMA (12,1,12) p=12, d=1 and q=12 

+ Mean Absolute Percentage Error (MAPE): ~5.6%
++ Predicted monthly no. of passengers is off from actual value by about 5.6%
++ Value of ≤ 20% is considered a model with good prediction based on some papers related to air traffic volume

+ Root Mean Square Error (RMSE): approximately 345,000
++ Predicted monthly no. of passengers is off from actual value by about 345k

### Model 2: SARIMA
Model identified with lowest AIC: ARIMA(5,1,0)(1,0,1)[12], where p,d,q: (5,1,0) | P,D,Q: (1,0,1) | S/m: 12 

+ Mean Absolute Percentage Error (MAPE): ~6.2%
+ Root Mean Square Error (RMSE): approximately 385,000

**Based on the metrics, the Auto-ARIMA model gave us more accurate predictions.**

## Predicting air passenger traffic without COVID-19 & Recovery post-COVID
![image](https://github.com/user-attachments/assets/693e492e-de7d-41e7-8ba6-f837ad57bdfa)
+ If there was no COVID-19 pandemic, air passenger numbers would have continued to increase through the years
+ Based on the plot, actual air passenger volume came close to predicted figure in Dec 2024. This suggests that air traffic at Changi Airport should be considered to have finally recovered after almost 4-5 years since COVID hit. In fact, comparing to pre-COVID figures, the no. of passengers handled in Dec 2024 was ~6.41 million which matches the highest no. of passengers handled in any month before the COVID pandemic.

## Recommendations
To potentially capture more air passenger volume, Changi Airport may wish to consider the following:
Regions of South East Asia & North East Asia, main contributor to overall total no. of passengers:
+ Continue to maintain existing connectivity
+ Work with airline companies to explore connections with new, lesser-known cities in these regions

Region of South Asia, strong growing market:
+ Expand connections with more cities in this region so as to make Changi Airport the key connecting hub for travellers moving between South Asia and their final destination

Region of North America and Middle East, relatively low passenger volume:
+ Possible untapped market that the airport could look into to increase no. of travellers flying to/from these regions to Singapore

## Future steps
1. Incorporate recent data (e.g. 2024, 2025) when they become available to construct new model (e.g. use predicted values from current model for years 2020 – 2023 + actual values from 2024 onwards)
2. Exploration of other time-series models in attempt to build an even more accurate model, with lower error
3. Collect and include data on monthly number of flights operating in and out of the airport (i.e. connectivity) into the model as this feature may be a potential predictor for air passengers numbers

