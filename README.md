# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 4: Singapore Dengue Cases Prediction

## Table of Contents
- [Background](#Background)  
- [Problem Statement](#Problem-Statement) 
- [Dataset](#Dataset)
- [Executive Summary](#Executive-Summary)
- [Conclusions and Recommendations](#Conclusions-and-Recommendations)  

## Background


[Return to top](#Table-of-Contents)  

## Problem Statement
The goal of this project is to predict the number of dengue cases in Singapore on a subzone-level in order to enable targeted intervention and better resource allocation. 

[Return to top](#Table-of-Contents)  

## Dataset
We curated the dataset from:
1. [Historical daily weather](http://www.weather.gov.sg/climate-historical-daily/): Daily weather data includes rainfall, tempurature and wind speed in Singapore
2. [Weekly dengue cases](https://data.gov.sg/dataset/weekly-number-of-dengue-and-dengue-haemorrhagic-fever-cases): Weekly number of dengue cases from 2014 to 2018 in Singapore
3. [Google trends](https://trends.google.com/trends/explore?date=today%205-y&geo=SG&q=%2Fm%2F09wsg): Google search terms containing ‘dengue’ in Singapore
4. [Dengue clusters](http://outbreak.sgcharts.com/data): Dengue cluster records in Singapore used for this project were from 2015 to 2018
5. [Master Plan Subzone Boundary (No Sea)](https://data.gov.sg/dataset/master-plan-2014-subzone-boundary-no-sea?resource_id=c30bfcc0-7e23-4959-b4d9-c5da5e00af54): A shapefile that contained the geographic information of all 323 subzones in Singapore

[Return to top](#Table-of-Contents)

## Executive Summary

### EDA

To visualize the spatial distribution of infecting locations in Singapore from 2015 to 2018, we plotted all infecting locations involved in the dengue clusters during this period and mapped them to the corresponding subzones. The resulting map is color-coded with the cumulative case numbers, revealing that the top 10 infecting subzones were mainly concentrated in the east, north-east, north, and central regions.
<img src="images/EDA_spatial distribution.png" width="1000"/>

To investigate the potential correlation between weather patterns and dengue cases, we mapped the average weekly total rainfall, weekly mean temperature, and weekly mean wind speed with the spatial distribution of infecting locations. However, due to the unavailability of data for all subzones, it is challenging to establish a clear relationship between rainfall and dengue cases in each subzone.

### Modeling


### Cost-benefit Analysis
- **Targeted intervention**: With 323 subzones in Singapore, assume the cost of intervention in each subzone would be 10,000 SGD. By predicting the number of dengue cases at the subzone level, it becomes possible to identify the top 10 subzones that are at the highest risk of dengue transmission for every week. Targeting these subzones with intervention measures can prevent the majority of dengue cases and reduce the overall cost of intervention to 100,000 SGD (10 subzones x 10,000 SGD per subzone), instead of 3,230,000 SGD (323 subzones x 10,000 SGD per subzone) if intervention measures were applied uniformly.

- **Resource allocation**: Each subzone of Singapore has an average population of 15,900 (5 Million/315 residential subzones), and sometimes it can have limited medical personnel and supplies to combat dengue (e.g. during COVID period). By predicting the number of dengue cases at the subzone level, it becomes possible to allocate resources efficiently. If a particular subzone is predicted to have a high number of dengue cases, resources such as medical personnel, mosquito control measures, and other supplies can be allocated to that subzone. For example, if a subzone is predicted to have 50 cases, it may require 10 medical personnel to treat patients, 15 mosquito control workers to eliminate breeding sites, and additional supplies such as mosquito nets and repellent. However, if another subzone is predicted to have only 5 cases, it may require much fewer resources to combat the disease.
    
[Return to top](#Table-of-Contents)

## Conclusions and Recommendations  




[Return to top](#Table-of-Contents)  

