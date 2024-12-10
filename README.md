# Leveraging Vehicle ads Data for Fraud Prevention and Operational Efficiency 
## Introduction

According to the Insurance Bureau of Canada, insurance fraud costs Canadians well over $1 billion a year in added insurance premiums ([source](https://www.ibc.ca/news-insights/news/vigilance-is-key-in-fighting-insurance-fraud)). Preventing this fraud will not only reduce costs for Definity but also improve customer satisfaction. In this project, using the **Poland Cars for Sale** dataset ([link](https://www.kaggle.com/datasets/bartoszpieniak/poland-cars-for-sale-dataset)), I have performed vehicle segmentation, anomaly detection, and time series analysis with the goal of generating insights to enhance operational efficiency and streamline fraud prevention for Definity.

Data cleaning and exploratory data analysis (EDA) were performed before performing the three main tasks. 

## Data Cleaning
A vast majority of the data cleaning process was dealing with null values. The dataset contains substantial null values in columns such as CO2 emissions, first owner (whether the vehicle has had one owner), vehicle version, vehicle generation, origin country, and car first registration day, as shown in the null matrix below:

![Null Matrix](Plots/null_matrix.png)

For those columns that contained null values for about half of the dataset, the columns were dropped, except for "first owner," because I discerned that vehicles that are not first owners had null values, so I filled them accordingly. For the remaining few null values, those observations were dropped as they were not many and wouldn't lead to consequential information loss.

For EDA insights, visit the [vehicle_segmentation notebook](vehicle_segmentation.ipynb).


## Vehicle Segmentation

To streamline fraud prevention and improve risk assessment, K Prototypes clustering was used to segment vehicles into three groups based on key features that were carefully selected based on insights discerned from EDA and also practical business relavance which include**Mileage_km**, **Power_HP**, **Displacement_cm3**, **Price_CAD**, **Years_From_Production_To_Offer**, and **Type**. The optimal number of clusters was determined using the Elbow Method and Silhouette Scores, with 3 clusters providing the best balance between cluster cohesion and separation. K Prototypes was chosen for its ability to handle both categorical and numeric features, ensuring robust segmentation despite the mixed data types.

The identified clusters provide insights into vehicle characteristics in each cluster. The **Older City Commuters (Cluster 0)** are compact, older cars with low engine power and relatively high mileage. The **Modern Power Vehicles (Cluster 1)** consist of newer, higher-powered vehicles with lower mileage and higher prices. The **Seasoned Family Travelers (Cluster 2)** include older, high-mileage station wagons. Definity can explore historical data for vehicles in each cluster to determine preferences, the type of claims associated with each cluster, the ones that are high risk (mitigating the risks of information assymetry inclusidung adverse seection and moral hazard) and leveraging the insighs to  Increase customer acquisition and retention by crafting appealing offers tailored to each cluster's preferences, Reduce information asymmetry by offering coverage options that align with the risk profiles and needs of each cluster.
, and Identify and mitigate fraudulent claims, ensuring cost savings and operational efficiency.
eg Claims from a vehicle that deviate from the historical data trends of its cluster (e.g., unusually frequent or expensive claims) can be flagged for deeper scrutiny.
Clusters with higher instances of fraud can be monitored more intensively.
These clusters enable Definity to better target high-risk vehicles, improve underwriting, and optimize marketing strategies.

By strategically integrating cluster insights into fraud detection, tailored coverage, and targeted marketing, Definity Insurance can:
- Mitigate financial risks associated with fraudulent claims.
- Deliver personalized, competitive coverage options to customers.
- Strengthen market position through focused, customer-centric campaigns.

This approach not only reduces operational inefficiencies but also enhances customer experience, establishing Definity as an industry leader in innovation which aligns with Definity's ambition. :)

### Cluster Centroids

| Cluster | Mileage (km) | Power (HP) | Engine Size (cm3) | Price (CAD) | Age (Years) | Type            |
|---------|------------|----------|------------------|-----------|-------------------------------|-----------------|
| 0       | 150,000    | 95       | 1,402            | 7,173     | 10                            | City Car        |
| 1       | 51,000     | 145      | 1,640            | 27,000    | 3                             | SUV             |
| 2       | 223,000    | 146      | 1,981            | 8,097     | 12                            | Station Wagon   |

### Cluster Visualization

![Cluster Visualization](Plots/cluster_viz.png)

