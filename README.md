# Bike Store Sales Dashboard

### Dashboard Link : https://app.powerbi.com/links/QhRTR4o8ra?ctid=8f11c6f4-648e-4c0c-bb99-96e8408a8e2a&pbi_source=linkShare

Please not that I'm working with a free version of Power BI, so I'm unable to publish the report on the web.

## Problem Statement

This project aims to demonstrate proficiency in Power BI by transforming raw bike share data into actionable insights. The dashboard highlights key performance indicators, customer demographics, and sales trends to enable data-driven decision-making.

# Bike Store Sales Dashboard

This Power BI dashboard provides insights into the sales performance of a Bike Store, highlighting key metrics, trends, and demographics to support data-driven decision-making. It's designed as a demonstration of Power BI skills for potential employers. 

## Purpose

The main goal of this dashboard is to showcase my proficiency in Power BI development and data visualization.

## Key Metrics and KPIs

* **Riders:** Total number of riders
* **Revenue:** Total revenue generated
* **Profit:** Total profit earned
* **Net Profit Margin:** Percentage of profit relative to revenue
* **Average Revenue per Hour per Day:** Heatmap showing revenue distribution across hours and days
* **Riders Demographic (Casual vs Registered):** Donut chart comparing rider types
* **Revenue by Season:** Clustered bar chart displaying revenue breakdown by season
* **KPI over Time:** Line and clustered column chart tracking riders, average profit, and average revenue over time

## Visuals

* **Card (Right Top):** Display the total number of riders and the Net Profit Margin
* **Table (Left):** Heatmap visualizing average revenue per hour per day, using varying shades of blue to indicate performance
* **KPI over Time:** Line and clustered column chart with `dteday` on the x-axis, riders on the y-axis, and average profit and average revenue as lines
* **Revenue by Season:** Clustered bar chart displaying the sum of revenue for each season
* **Riders Demographic:** Donut chart showing the percentage of riders categorized as Registered or Casual



## Data Source

The data for this dashboard is derived from the following:

* `bike_share_yr_0.csv`
* `bike_share_yr_1.csv`
* `COST_TABLE.csv`

The data is transformed using the following SQL query:

```sql
WITH CTE AS (
    SELECT * FROM bike_share_yr_0
    UNION ALL
    SELECT * FROM bike_share_yr_1
)
SELECT
    a.dteday,
    a.season,
    a.yr,
    a.weekday,
    a.hr,
    a.rider_type,
    a.riders,
    b.price,
    b.COGS,
    a.riders * b.price AS revenue,
    (a.riders * b.price) - (a.riders * b.COGS) AS profit
FROM
    CTE a
LEFT JOIN
    COST_TABLE b
ON
    a.yr = b.yr
```

## Steps Followed

1. **Data Collection and Cleaning:** 
   * Gathered data from `bike_share_yr_0.csv`, `bike_share_yr_1.csv`, and `COST_TABLE.csv`.
   * Performed data cleaning and preprocessing to ensure data quality and consistency. 

2. **Data Modeling**:
   * Created a database named "Bike Data" in SQL Server Management Studio.
   * Imported the three CSV files (`bike_share_yr_0.csv`, `bike_share_yr_1.csv`, and `COST_TABLE.csv`) into the database using the "Import Flat File" task, creating corresponding tables.
   * Wrote and executed the provided SQL query within SQL Server Management Studio to combine and transform the data. 
   * Established a connection to the "Bike Data" database in Power BI Desktop.
   * Imported the results of the SQL query into Power BI using the established connection. 
   * Created a conditional column named "Years" to provide clearer year filtering in the dashboard. The column assigns the year 2022 if the original `yr` column value is "0" and 2023 if it's "1".
   
   Snap of View Model,

![View Model](https://github.com/user-attachments/assets/22f382fd-1928-43ae-8011-202aa3f6176f)


3. **Dashboard Design and Development:** 
   * Selected appropriate visualizations to effectively communicate insights (e.g., heatmap for average revenue, line and clustered column chart for KPIs over time).
   * Designed the dashboard layout for clarity and ease of use, considering user experience.
   * Applied formatting and styling to enhance visual appeal and professionalism.

4. **Insights and Analysis:** 
   * Explored the data to identify key trends and patterns.
   * Highlighted peak sales hours, daily sales patterns, changes in ridership, and the impact of price changes on revenue and profit.
   * Developed data-driven recommendations to optimize business performance. 


# Snapshot of Dashboard (Power BI Service)

![dashboard_snapo](https://github.com/user-attachments/assets/f0db8cf5-4be3-4d4a-bc40-046d38492ddd)

 
 # Report Snapshot (Power BI DESKTOP)

 
![Dashboard_upload](https://github.com/user-attachments/assets/b1d37a95-aab6-4c91-8e43-4a8e301bb28e)

## Insights

### 1. Rider Type

* 68.41% customers are **Registered** riders.
* 31.59% customers are **Casual** riders.

    `Thus, the majority of riders are **Registered**.`

### 2. Seasonality

* 33.39% of rides occur in **Fall** (season 3).
* 26.04% of rides occur in **Summer** (season 2).
* 24.69% of rides occur in **Spring** (season 1).
* 15.88% of rides occur in **Winter** (season 4).

    `Thus, **Fall** is the most popular season for bike rides.`

### 3. Time of Day

* The **busiest hours** for bike rides are between **5 pm and 7 pm**. 
* **Early morning hours** (between midnight and 6 am) see the **lowest ridership**.

    `This suggests that most rides are for commuting or leisure activities after work or school.`

### 4. Year-over-Year Growth

* The number of riders **increased significantly** from 2022 to 2023.
* **Revenue** and **profit** also saw **substantial growth** year-over-year.

    `This indicates positive business performance and potential for further expansion.`

### 5. Impact of Price Increase

The analysis of the impact of the price increase from 2022 to 2023 reveals some interesting insights:

* **Overall Impact:**
    * Despite a **25.1% increase** in the average price, the total number of riders increased by **64.9%**. This suggests that the price increase did not negatively impact the overall demand for bike rides.
    * Total revenue increased by **106.2%**, which is significantly higher than the increase in riders. This indicates that the price increase directly contributed to higher revenue generation.

* **Impact on Rider Types:**
    * Both **casual** and **registered** riders increased in 2023 compared to 2022.
    * **Casual riders** saw a larger increase in ridership (**50.8%**) compared to registered riders (**68.4%**).
    * The revenue from both rider types also increased substantially, with **casual riders** experiencing a higher percentage increase (**88.5%**) than registered riders (**110.6%**).

    `The price increase from 2022 to 2023 did not deter riders; in fact, it led to a significant increase in both ridership and revenue. This suggests that the demand for bike rides is relatively inelastic within this price range. The company was able to successfully pass on the increased costs to the customers without negatively impacting the demand, resulting in higher revenue and likely improved profitability.` 
