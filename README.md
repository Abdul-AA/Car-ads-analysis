# Leveraging Vehicle ads Data for Fraud Prevention and Operational Efficiency 
## Introduction

According to the Insurance Bureau of Canada, insurance fraud costs Canadians well over $1 billion a year in added insurance premiums ([source](https://www.ibc.ca/news-insights/news/vigilance-is-key-in-fighting-insurance-fraud)). Preventing this fraud will not only reduce costs for Definity but also improve customer satisfaction. In this project, using the **Poland Cars for Sale** dataset ([link](https://www.kaggle.com/datasets/bartoszpieniak/poland-cars-for-sale-dataset)), I have performed vehicle segmentation, anomaly detection, and time series analysis to enhance operational efficiency and prevent fraud for Definity.

## Data Cleaning and EDA

Data cleaning and exploratory data analysis (EDA) were performed before performing the three main tasks. 

### **Data Cleaning**

A large portion of the data cleaning process focused on addressing null values. The dataset contained significant null values in columns such as CO2 emissions, first owner status (whether the vehicle has had one owner), vehicle version, vehicle generation, origin country, and the car's first registration date. As shown in the [null matrix](file:///Users/Abdul/Desktop/Car-ads-analysis/Plots/null_matrix.png), many of these columns contained null values for about half of the dataset. These columns were dropped, except for "first owner," which was filled in based on the assumption that vehicles with missing first owner information likely had more than one owner. For the remaining features with null values, observations were dropped as they were relatively few and did not lead to significant information loss.

### **Exploratory Data Analysis (EDA)**

For further insights, you can visit the [Vehicle Segmentation EDA notebook](file:///Users/Abdul/Desktop/Car-ads-analysis/vehicle_segmentation.ipynb).


Vehichle Segmentation

