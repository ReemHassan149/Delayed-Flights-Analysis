# Delayed-Flights-Analysis
This is a comprehensive set of dashboards focusing on flight performance, delays, and cancellations. Below is a structured, professional analysis report . It includes an overview, key insights, and the technical measures used to build the logic.
# US Flight Reliability & Delay Analysis Dashboard
## Project Overview
This project provides a deep-dive analysis of airline operational performance, focusing on flight delays, cancellations, and diversions. The dashboard was built to identify seasonal trends, carrier reliability, and the primary root causes of disruptions within the aviation industry.
### DASHBOARD
- ![Main](https://github.com/user-attachments/assets/7d823e52-cc84-4bd7-a751-ee863dbcc8a4)
- ![Delay Reasons](https://github.com/user-attachments/assets/2bdf6712-bd34-4ae7-91ec-41dfc62642ca)
- ![Cancelled](https://github.com/user-attachments/assets/da6df657-6579-4682-aadc-16728b06d485)
- ![Diverted](https://github.com/user-attachments/assets/49251a38-e4a0-4c08-8240-8093009d5331)
- ![Not Delayed Nor Cancelled](https://github.com/user-attachments/assets/bb9a5499-a796-4774-a00b-ba86328b942e)\
- ![Avg Delay](https://github.com/user-attachments/assets/d0ee1737-d486-4502-9db8-c2bc433371e2)
- ![Flights Delay Star Schema](https://github.com/user-attachments/assets/fb0b5876-c187-4fbe-9470-9641b2d636e4)
- ![Flights Delay Measures](https://github.com/user-attachments/assets/1dbfa666-8bc0-4767-a37f-9d2a31ace90a)

### Key Datasets Explored:
- **Flight Volume**: ~2 million flights.

- **Temporal Analysis**: Monthly and daily performance trends.

- **Geographic Focus**: Major US hubs (ORD, ATL, DFW) and regional states.

- **Delay Categories**: Carrier, Weather, NAS, Security, and Late Aircraft.
  
## Key Insights & Findings
### 1. Operational Overview
- **Volume**: Out of 2 million total flights, the system successfully processed 1.936M non-cancelled and 1.934M non-delayed flights.

- **Disruptions**: There were 635 cancellations and 7,790 diversions.

- **Holiday Impact**: A significant spike in cancellations and delays occurs in December, likely due to winter weather and peak holiday travel volume.

### 2. Delay Root Cause Analysis
Delays are categorized into five primary buckets. Carrier Delays are the leading cause of disruption:

- **Carrier Delay**: 983 incidents (Leading cause)

- **Weather Delay**: 599 incidents

- **NAS Delay**: 574 incidents

- **Late Aircraft Delay**: 564 incidents

- **Security Delay**: 156 incidents (Least frequent)

### 3. Geographical & Carrier Performance
- **Most Affected Hubs**: Chicago O'Hare (ORD) and Hartsfield-Jackson (ATL) consistently show the highest volume of both delayed and diverted flights.

- **Regional Cancellations**: Illinois (32%) and Texas (28%) account for the majority of flight cancellations.

- **Carrier Reliability**: Southwest Airlines handles high volume but also experiences the highest number of diverted flights (~1.4K).

### 4. Taxi Times (Efficiency)
- The average Taxi-In time across all carriers is 7 minutes.

- The average Taxi-Out time is significantly higher at 18.24 minutes, indicating ground congestion is more prevalent during departures than arrivals.

## DAX Measures & Logic
The following measures were created in Power BI to drive the visualizations and provide dynamic insights:

### Measures
- **No. Flights**:	Total count of all flight records in the dataset.
- **All delayed No.**:	Total count of flights where arrival delay is >0.
- **Avg Arr Delay**:	Calculates the mean arrival delay (in minutes) across all flights.
- **NO. Cancelled Flights**:	Sum of flights where the cancellation flag is active.
- **No. Diverted Flights**:	Count of flights that were redirected to an alternate airport.
- **Carrier Delay**:	Total minutes/count of delays attributed to airline operational issues.
- **NAS Delay**:	Delays caused by the National Airspace System (heavy traffic, air traffic control).
- **Weather Delay**:	Delays specifically caused by extreme weather conditions.
- **Late Aircraft Delay**:	Ripple-effect delays caused by the late arrival of a previous flight.
- **Security Delay**:	Delays caused by terminal or security screening issues.
- **Not Cancelled Flights**:	Total flights minus the cancelled flights.
- **Not Delayed Flights**:	Total flights minus the delayed flights.

## Tools Used
- **Power BI**: Data modeling, DAX development, and visualization. I merged data from 2 csv files to the main file using power query and made star schema.
- **Data Cleaning**: Handled null values in delay reasons and formatted temporal data.

## Recommendations
Based on the data trends observed in the dashboard, the following strategic actions are recommended:

- **Winter Readiness Program**: With a massive spike in cancellations and delays during December (481 cancellations vs. near-zero in summer), airlines should increase de-icing equipment and staffing levels at hubs like Chicago O'Hare (ORD) at least 30 days prior to the peak season.

- **Optimize Taxi-Out Efficiency**: Since the average Taxi-Out (18.24m) is more than double the Taxi-In (7m), ground operations should focus on departure sequencing. Reducing taxi-out time by even 2 minutes across 2M flights would result in massive fuel savings and improved passenger satisfaction.

- **Carrier-Specific Training**: American Airlines and SkyWest lead in cancellations. A deep-dive audit into their maintenance and crew scheduling protocols is recommended to identify why they are more prone to cancellations than competitors like United or Southwest.

- Regional Focus (IL & TX): Over 60% of cancellations are concentrated in Illinois and Texas. Developing "Regional Recovery Plans"—such as standby aircraft positioned specifically in these states—could help mitigate the ripple effect across the national network.
