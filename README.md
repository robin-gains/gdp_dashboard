#  World GDP Analysis Dashboard (Power BI)

##  Project Overview

This project is a Power BI dashboard that analyzes global GDP trends
across countries and years. The dashboard helps users understand
economic performance, identify top-performing countries, and detect peak
GDP growth periods using interactive visualizations.

The goal of this project is to transform raw GDP data into clear,
actionable insights using Power BI and DAX.

------------------------------------------------------------------------

##  Objectives

-   Analyze GDP growth trends across countries
-   Identify the Top 10 countries by GDP
-   Determine the peak GDP growth percentage and the year it occurred
-   Provide an interactive dashboard for quick economic insights

------------------------------------------------------------------------

##  Dataset

  Column         Description
  -------------- ------------------------
  country_name   Name of the country
  year           Year of the GDP record
  gdp            Total GDP value
  gdp%           GDP growth percentage

------------------------------------------------------------------------

##  Technologies Used

-   Power BI
-   DAX (Data Analysis Expressions)
-   Data Visualization
-   Data Modeling

------------------------------------------------------------------------

##  Dashboard Features

### 1. GDP Trend Analysis

A line chart showing how GDP has changed across years for different
countries.

### 2. Top 10 Countries by GDP

``` dax
Top10_GDP_Countries =
TOPN(
    10,
    SUMMARIZE(
        'world_gdp_data',
        'world_gdp_data'[country_name],
        "Total GDP", SUM('world_gdp_data'[gdp])
    ),
    [Total GDP],
    DESC
)
```

### 3. Peak GDP Growth Indicator

``` dax
PEAK Label =
VAR PeakValue = MAX(world_gdp_data[gdp%])
VAR PeakYear =
    CALCULATE(
        MAX(world_gdp_data[year]),
        world_gdp_data[gdp%] = PeakValue
    )
RETURN
    FORMAT(PeakValue, "0.0") & "% in " & PeakYear
```

------------------------------------------------------------------------

##  Key Insights

-   Identify which country contributes the most to global GDP
-   Discover years with major economic growth
-   Compare GDP performance across countries

------------------------------------------------------------------------

##  How to Use

1.  Download the `.pbix` file from this repository
2.  Open it in Power BI Desktop
3.  Refresh the dataset if needed
4.  Explore the interactive visuals and filters

------------------------------------------------------------------------

##  Repository Structure

World-GDP-Dashboard │ ├── world_gdp.pbix ├── README.md └── images └──
dashboard_preview.png

------------------------------------------------------------------------

##  Future Improvements

-   Add GDP per capita analysis
-   Include continent-level comparisons
-   Add forecasting for future GDP growth
-   Integrate additional economic indicators

------------------------------------------------------------------------

## 👨‍💻 Author

Robin Ravichandran

AI & ML Student \| Data Analytics Enthusiast
