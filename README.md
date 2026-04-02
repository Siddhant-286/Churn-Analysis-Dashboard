# Telco Customer Retention Dashboard

## Problem Statement

## Business Problem Statement
The Telecommunications company is experiencing a high customer attrition rate (26.5%), impacting monthly revenue. The management aims to identify the root causes of churn and evaluate the effectiveness of various services in retaining customers.

The primary objective of this analysis is to determine which services (like Tech Support or Security) act as "Retention Drivers" and whether demographic factors (like having a Family/Partner) correlate with higher customer loyalty.

Key Business Questions Analyzed
To address the business problem, this dashboard specifically analyzes the following critical questions:

## 1. Service Impact Analysis (Value-Added Services)

### Dashboard Snapshot (Power BI Desktop)
![Dashboard Snapshot](https://github.com/user-attachments/assets/dd402007-a3e6-48a7-be92-b35a5f40df70)

    (Most Important) Impact of Tech Support: Does providing quality Tech Support significantly reduce customer churn?

    Device Protection: Do customers who opt for Device Protection plans show lower churn rates compared to those who don't?

    Online Security & Backup: Do customers feel more "secure" and stay longer when they subscribe to Online Backup and Online Security services?

    Core Services: Is the churn limited to Internet users, or are Phone Service users also leaving at the same rate?

## 2. Demographic Loyalty Profiling

    Family Stability: Do customers with Dependents (Children) switch providers less frequently due to the hassle of changing services?

    Partnership Effect: Are customers with Partners (Married) more loyal compared to single customers?

    ## Steps followed

Step 1: Load the dataset (Telco-Customer-Churn.csv) into Power BI Desktop.

Step 2: Open Power Query Editor. Checked "Column Quality" and "Column Distribution" to ensure data consistency.

Step 3: Data cleaning involved handling the TotalCharges column (converted from Text to Decimal) and replacing errors with 0. A Conditional Column Churn Status (1 = Yes, 0 = No) was created to facilitate mathematical calculations.

Step 4: In the Report View, a professional color palette was applied to distinguish between "Safe" (Loyal) and "Risky" (Churned) segments.

Step 5: Created a separate Measure Table (_Calculations) to keep the DAX formulas organized and the data model efficient (Star Schema approach).

Step 6: Created three primary KPI Cards to display high-level metrics:
    - Total Customers
    - Total Churned Customers
    - Overall Churn Rate %
    - Revenue Lost 

![CriticalInsight](https://github.com/user-attachments/assets/8f29dae2-2587-477d-8d11-b6d86aaac3da)

Step 7: Added specific charts to visualize the data:


A Donut Chart to visualize the Churn split by Contract Type (Month-to-Month vs. Yearly).

![DonutChart](https://github.com/user-attachments/assets/078b292a-b3f1-4c41-af0a-a3cabf15ba21)

A Grouped Bar Chart to analyze Demographic loyalty (Partners & Dependents).

A Matrix Table to show detailed numbers for Internet Services (DSL vs. Fiber Optic).

![MatrixTable](https://github.com/user-attachments/assets/17d0b880-6227-4a91-a0e2-f3b1d0d15050)

 Step 8: Created DAX measures for the main KPIs using CALCULATE and DIVIDE functions.

DAX Calculations
Total Customers:

    Total Customers = COUNTROWS('Telco Customer Churn')

Total Churned Customers:

    Churned Customers = CALCULATE(COUNTROWS('Telco Customer Churn'), 'Telco Customer Churn'[Churn] = "Yes")

Overall Churn Rate %:

    Churn Rate % = DIVIDE([Churned Customers], [Total Customers], 0)

### Service Specific Churn (Example: Tech Support):

    Churn Rate (Tech Support) = DIVIDE(CALCULATE(COUNT('Telco Customer Churn'[customerID]), 'Telco Customer Churn'[TechSupport] = "Yes", 'Telco Customer Churn'[Churn] = "Yes"), CALCULATE(COUNT('Telco Customer Churn'[customerID]), 'Telco Customer Churn'[TechSupport] = "Yes"), 0)

# Dashboard 2 (Power BI Desktop)
![Dashboard Snapshot](https://github.com/user-attachments/assets/74d44b45-43c8-4656-9503-3107c2f8a541)


## Insights
This multi-page report provides several key insights into the customer churn data:

[1] Key Performance Indicators (KPIs)

    High Attrition: The company is currently losing 26.5% of its customers.

    Revenue Impact: The churn is significantly impacting the Monthly Recurring Revenue (MRR), driven largely by short-term contract holders.

[2] Service Impact Analysis (The "Retention Drivers")

    Tech Support is King: The "Churn Rate by Service" chart shows that Tech Support users have a churn rate of only ~15%, which is significantly lower than the company average.

    Security Matters: Customers with Online Security and Online Backup also show high loyalty (~21-22% Churn Rate).

    Phone Service is Neutral: Phone Service has a churn rate of ~27%, indicating that basic calling features do not increase customer loyalty.

[3] Contract & Internet Risk

    The "Red Flag" Group: Customers on Month-to-Month contracts are the most volatile, with churn rates exceeding 40%.

    Fiber Optic Risk: There is a high volume of churn among Fiber Optic users, suggesting potential dissatisfaction with price or reliability compared to DSL users.

[4] Demographic Profile

    Family Stability: The Demographics chart indicates that customers with Partners (~20% Churn) and Dependents (~16% Churn) are far more stable and less likely to switch providers compared to Single customers

    # ClimateScope: Visualizing Global Weather Trends and Extreme Events

## Problem Statement

As climate data grows in volume and complexity, there is a critical need for accessible platforms that translate raw numbers into actionable insights. Standard spreadsheets are no longer sufficient for spotting crucial environmental patterns.

The primary objective of this project is to analyze and visually represent global weather patterns using the comprehensive Global Weather Repository dataset. This project aims to uncover seasonal trends, regional variations, and extreme weather events through an interactive dashboard, providing a data-driven platform that supports climate awareness, informed decision-making, and further research into global weather dynamics.

## Key Questions Analyzed
To address the core objective, this dashboard specifically analyzes the following critical questions:

1. **Global Extremes** : 
    What are the absolute maximum and minimum temperatures, and which cities/countries experience them?

2. **Seasonal Trends** :
     How do temperature, humidity, and wind speed fluctuate across different months and quarters globally?

3.  **Precipitation Dynamics** :
     Which regions are most susceptible to heavy rainfall and severe wind velocities?

4. **Risk & Anomaly Tracking** :
     How frequent are extreme weather events (heatwaves, heavy rain, high winds), and which countries fall into the "High Risk" climate category?

# Dashboard Snapshot (Power BI Desktop)

![Global Event Dashboard](https://github.com/user-attachments/assets/6fe15c26-2b8e-4d3b-a49b-1e843f5f27b5)
## Steps Followed
- Step 1: Downloaded the Global Weather Repository dataset from Kaggle via the Kaggle API.

- Step 2: Set up the Python environment and loaded the dataset using pandas to inspect the structure, data types, and key variables (temperature, humidity, precipitation, etc.).

- Step 3: Performed Data Cleaning. Identified missing values and anomalies. Handled inconsistent entries and dropped nulls where necessary to ensure data accuracy.

- Step 4: Data Transformation. Aggregated the daily weather data into monthly and quarterly averages to improve processing efficiency and visualize long-term trends smoothly.

- Step 5: Conducted core statistical analysis to understand distributions, variable correlations, and pinpoint extreme weather events.

- Step 6: Designed the dashboard layout and selected appropriate visualization types (Choropleth maps for geography, Line charts for time-series, Bar charts for comparisons).

- Step 7: Built the interactive visualizations using Plotly. Created charts for Temperature Trends, Precipitation by Country, and a global Risk Category map.

- Step 8: Deployed the final interactive dashboard using Streamlit, integrating user controls like date sliders, country drop-downs, and city filters for dynamic data exploration.

# ClimateScope: Visualizing Global Weather Trends and Extreme Events

## Problem Statement

As climate data grows in volume and complexity, there is a critical need for accessible platforms that translate raw numbers into actionable insights. Standard spreadsheets are no longer sufficient for spotting crucial environmental patterns.

The primary objective of this project is to analyze and visually represent global weather patterns using the comprehensive Global Weather Repository dataset. This project aims to uncover seasonal trends, regional variations, and extreme weather events through an interactive dashboard, providing a data-driven platform that supports climate awareness, informed decision-making, and further research into global weather dynamics.

## Key Questions Analyzed
To address the core objective, this dashboard specifically analyzes the following critical questions:

1. **Global Extremes** : 
    What are the absolute maximum and minimum temperatures, and which cities/countries experience them?

2. **Seasonal Trends** :
     How do temperature, humidity, and wind speed fluctuate across different months and quarters globally?

3.  **Precipitation Dynamics** :
     Which regions are most susceptible to heavy rainfall and severe wind velocities?

4. **Risk & Anomaly Tracking** :
     How frequent are extreme weather events (heatwaves, heavy rain, high winds), and which countries fall into the "High Risk" climate category?

# Dashboard Snapshot (Power BI Desktop)

![Global Event Dashboard](https://github.com/user-attachments/assets/6fe15c26-2b8e-4d3b-a49b-1e843f5f27b5)
## Steps Followed
- Step 1: Downloaded the Global Weather Repository dataset from Kaggle via the Kaggle API.

- Step 2: Set up the Python environment and loaded the dataset using pandas to inspect the structure, data types, and key variables (temperature, humidity, precipitation, etc.).

- Step 3: Performed Data Cleaning. Identified missing values and anomalies. Handled inconsistent entries and dropped nulls where necessary to ensure data accuracy.

- Step 4: Data Transformation. Aggregated the daily weather data into monthly and quarterly averages to improve processing efficiency and visualize long-term trends smoothly.

- Step 5: Conducted core statistical analysis to understand distributions, variable correlations, and pinpoint extreme weather events.

- Step 6: Designed the dashboard layout and selected appropriate visualization types (Choropleth maps for geography, Line charts for time-series, Bar charts for comparisons).

- Step 7: Built the interactive visualizations using Plotly. Created charts for Temperature Trends, Precipitation by Country, and a global Risk Category map.

- Step 8: Deployed the final interactive dashboard using Streamlit, integrating user controls like date sliders, country drop-downs, and city filters for dynamic data exploration.

## 📸 Dashboard Visuals & Analysis

### 1. Global Risk Map
Visualizing countries based on their calculated climate risk categories (High, Medium, Low).
![Global Risk Map](https://github.com/user-attachments/assets/3efb67e3-1441-44ec-b48a-cbd64f05d980)

### 2. Extreme Weather Events & Risk Score
Tracking total extreme events (Heatwaves, Heavy Rain, High Winds) and the distribution of Climate Risk Scores.
![Extreme Weather Events](https://github.com/user-attachments/assets/fdf206d8-a7f1-416e-84b7-14a9a7e65830)

### 3. Precipitation & Wind Trends
Analyzing total precipitation across countries and tracking maximum wind speeds by city.
![Precipitation and Wind Trends](https://github.com/user-attachments/assets/25cb52fa-df21-456c-b434-a1625154cd37)

### 4. Temperature Extremes by City & Country
Highlighting the absolute maximum and minimum temperatures recorded across various geographic locations.
![Temperature Trends](https://github.com/user-attachments/assets/d7ec4218-7621-47d8-bb17-5a0e9ee29998)

### 5. Overall Weather Trends
Detailed breakdown of average temperature, humidity, wind speed, and precipitation over time.
![Weather Trends Overview](https://github.com/user-attachments/assets/f98f51fc-d8fc-409e-821d-2752105ce56b)

💡 Key Insights Derived
Based on the visual dashboards above, several crucial insights were identified:

[1] Key Performance Indicators (KPIs) & Extremes
Global Thresholds: The dataset recorded an absolute maximum temperature of 49°C and a minimum of -30°C.

Extreme Event Volume: The dashboard successfully tracked 1,276 total extreme weather events during the measured period, heavily dominated by Heatwave Days (1,228), followed by High Wind Events (38) and Heavy Rain Events (10).

[2] Temperature Trends
The Hotspots: Middle Eastern countries consistently recorded the highest maximum temperatures, with Kuwait, Iraq, Djibouti, and Saudi Arabia frequently hitting the 46°C - 49°C range.

Seasonal Curves: The global average temperature trends follow a distinct bell curve, peaking globally during June, July, and August (~26°C average) before dipping toward the end of the year.

[3] Precipitation & Wind Dynamics
Tropical Rainfall: Total precipitation metrics highlight that tropical nations bear the brunt of global rainfall, with Brunei (612mm), Indonesia, and Malaysia leading the charts.

Wind Velocity: City-level wind tracking identified specific high-risk zones for storms, with Suva recording maximum wind speeds of up to 172 kph.

[4] Climate Risk Profiling
Global Vulnerability: By calculating a "Climate Risk Score," the interactive map categorizes regions into High, Medium, and Low risk. The pie chart distribution reveals that while ~81% of the data falls into lower risk scores, specific geographic clusters require critical monitoring for extreme climate shifts.
