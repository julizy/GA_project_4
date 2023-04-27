# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 4: Singapore Dengue Cases Prediction

## Table of Contents
- [Background](#Background)  
- [Problem Statement](#Problem-Statement) 
- [Dataset](#Dataset)
- [Executive Summary](#Executive-Summary)
- [Conclusion and Recommendation](#Conclusion-and-Recommendation)  

## Background


[Return to top](#Table-of-Contents)  

## Problem Statement
The goal of this project is to predict the number of dengue cases in Singapore on a temporal and spatial level, to enable targeted intervention and better resource allocation. 

[Return to top](#Table-of-Contents)  

## Dataset
We curated the dataset from:
1. [Historical daily weather](http://www.weather.gov.sg/climate-historical-daily/): Daily weather data includes rainfall, temperature and wind speed in Singapore
2. [Weekly dengue cases](https://data.gov.sg/dataset/weekly-number-of-dengue-and-dengue-haemorrhagic-fever-cases): Weekly number of dengue cases from 2014 to 2018 in Singapore
3. [Google trends](https://trends.google.com/trends/explore?date=today%205-y&geo=SG&q=%2Fm%2F09wsg): Google search terms containing ‘dengue’ in Singapore
4. [Dengue clusters](http://outbreak.sgcharts.com/data): Dengue cluster records in Singapore used for this project from 2015 to 2018
5. [Master Plan Subzone Boundary (No Sea)](https://data.gov.sg/dataset/master-plan-2014-subzone-boundary-no-sea?resource_id=c30bfcc0-7e23-4959-b4d9-c5da5e00af54): A shapefile that contained the geographic information of all 323 subzones in Singapore

[Return to top](#Table-of-Contents)

## Executive Summary

### Exploratory Data Analysis (EDA)

To visualize the spatial distribution of infecting locations in Singapore from 2015 to 2018, we plotted all infecting locations involved in the dengue clusters during this period and mapped them to the corresponding subzones. The resulting map is color-coded with the cumulative case numbers, revealing that the top 10 infecting subzones were mainly concentrated in the east, north-east, north, and central regions.

<img src="images/EDA_spatial distribution.png" width="1000"/>

To investigate the potential correlation between weather patterns and dengue cases, we mapped the average weekly total rainfall, weekly mean temperature and weekly mean wind speed with the spatial distribution of infecting locations. However, due to the unavailability of data for all subzones, it is challenging to establish a clear relationship between weather patterns and dengue cases in each subzone.

### Modeling

The forecasting algorithm used processed data on dengue clusters with subzones during the geospatial EDA phase. LightGBM regressor was selected as the prediction model, and the data were split into training (80%) and testing (20%) sets for out-of-sample validation based on the time period. Within the training set, 30% of the data was further partitioned as the validation set during training. The Symmetric Mean Absolute Percentage Error (SMAPE) was calculated and compared for the prediction and baseline (lag 1) using the validation set during training.

The model will be used to predict on a weekly basis: starting with the first week of the test set, the model predicts the number of dengue cases for each subzone, then when it came to the second week, the true value of the past week should be already known and it will be used to predict the number of cases for the second week, and so on until the entire test set has been predicted. To evaluate the accuracy of the model, we selected the first and second weeks of test set and compared the predicted values to the true values for geographic analysis.

<img src="images/Geospatial Prediction Methods.png" width="600"/>

The training results demonstrated an average SMAPE of 33.2% for the first week prediction, which was lower than the baseline. Upon comparing the geographic distribution of our predictions with the true values, we noticed that our predictions identified the same hotspot zones as the true values. The second week prediction had similar results, indicating the stability of the model. However, based on the SMAPE of the validation set during training, we observed that certain weeks had a significantly large prediction error. This indicates that the model with autoregression alone may not be sufficient for long-term predictions. Additional data with more features that can better describe the target variable are required to improve the model's accuracy and reduce its variance.

<img src="images/Geospatial Prediction Results.png" width="1000"/>

### Cost-Benefit Analysis
- **Targeted intervention**: With 323 subzones in Singapore, assume the cost of intervention in each subzone would be 10,000 SGD. By predicting the number of dengue cases at the subzone level, it becomes possible to identify the top 10 subzones that are at the highest risk of dengue transmission. Targeting these subzones with intervention measures can prevent the majority of dengue cases and reduce the overall cost of intervention to 100,000 SGD (10 subzones x 10,000 SGD per subzone), instead of 3,230,000 SGD (323 subzones x 10,000 SGD per subzone) if intervention measures were applied uniformly.

- **Resource allocation**: Each subzone in Singapore has an average population of 15,900 (calculated by dividing 5 million by 315 residential subzones), and limited medical personnel and supplies can be a challenge in combating dengue, particularly during periods of strain on healthcare resources, such as the COVID-19 pandemic. By predicting the number of dengue cases at the subzone level, it becomes possible to allocate resources efficiently. If a particular subzone is predicted to have a high number of dengue cases, resources such as medical personnel, mosquito control measures, and other supplies can be allocated to that subzone. For instance, if a subzone is predicted to have 50 cases, it may require 10 medical personnel to treat patients, 15 mosquito control workers to eliminate breeding sites, and additional supplies such as mosquito nets and repellent. In contrast, if another subzone is predicted to have only 5 cases, it may require significantly fewer resources to combat the disease.
    
[Return to top](#Table-of-Contents)

## Conclusion and Recommendation 




[Return to top](#Table-of-Contents)  

