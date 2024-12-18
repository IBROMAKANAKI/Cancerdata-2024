# Data Portfolio: Excel --> SQL --> Power --> R (Interview Task)	

## Cancer incidence (diagnoses) in the East of England

### Data Source: https://www.cancerdata.nhs.uk/covid-19/rcrd (Geography Tab > Downloads > Download incidence and stage time trend data for all Cancer Alliances and cancer sites (~15 MB))																	
Date Downloaded: 18th November 2024	

![East of England](assets/images/East of England.png)

# Table of contents 

- [Introduction](#introduction)
- [Objective](#objective)
- [Stages](#stages)
- [Design](#design)
  - [Tools](#tools)
- [Development](#development)
  - [Pseudocode](#pseudocode)
  - [Data Exploration](#data-exploration)
  - [Data Cleaning](#data-cleaning)
  - [Transform the Data](#transform-the-data)
  - [Create the SQL View](#create-the-sql-view)
- [Testing](#testing)
  - [Data Quality Tests](#data-quality-tests)
- [Visualization](#visualization)
  - [Results](#results)
  - [DAX Measures](#dax-measures)
- [Analysis](#analysis)
  - [Findings](#findings)
  - [Validation](#validation)
  - [Discovery](#discovery)
- [Recommendations](#recommendations)
  - [Potential ROI](#potential-roi)
  - [Potential Courses of Actions](#potential-courses-of-actions)
- [Conclusion](#conclusion)

# Introduction

The statistic that one in two people will develop cancer in their lifetime underscores the growing importance of understanding cancer patterns, both globally and regionally. This figure reflects advancements in life expectancy, with age being the most significant risk factor for cancer. It also points to the increasing need for early detection, effective prevention, and well-resourced healthcare systems to manage this rising burden.
Research by Cancer Research UK highlights that over 60% of cancer cases occur in individuals aged 65 and older. Factors like smoking cessation, regular physical activity, moderate alcohol consumption, and maintaining a healthy weight could prevent over 40% of cancer cases each year in the UK. These findings emphasise the dual role of medical advancements and public health initiatives in addressing the cancer epidemic.
Understanding regional cancer trends, such as those in the East of England, becomes critical for planning targeted healthcare responses. Geographic-specific data can help allocate resources, identify high-incidence cancer types, and tailor prevention campaigns to regional demographics.
(Ahmad et al., British Journal of Cancer, 2015), which analysed how lifetime cancer risks have shifted over decades.



# Objective 

- What is the key pain point? 

Analyse cancer diagnoses data for the East of England to uncover trends and actionable insights.

# Aim
To investigate regional patterns of cancer incidence in the East of England, identify trends in diagnoses by cancer type, and provide actionable insights for healthcare planning and targeted interventions. 

This aim focuses not only on presenting data but also on interpreting it for meaningful action. It considers public health implications, emphasising regional and national comparisons, and highlights the importance of targeted responses.


- What is the ideal solution? 

To create a dashboard that provides insights into cancer incidence in the East of England that includes their 
- Geography type
- Geography
- Year
- Month
- Date
- Cancer group
- Metric
- Statistic


This will help provide insights into cancer incidence in the East of England.

# Stages

- Design
- Developement
- Testing
- Analysis 


# Design 

## Dashboard components required 
- What should the dashboard contain based on the requirements provided?

To understand what it should contain, we need to figure out what questions we need the dashboard to answer:

1. Who are the top 10 cancer groups?
2. Which 3 cancer groups have the most Statistic (Cancer diagnoses)?
3. Which 3 cancer groups have the highest average statistic?
4. Which 3 cancer groups have the highest percentage by cancer type?
5. Which 3 cancer groups have the highest Region diagnosis rate?
6. Cancer group moving average (3 and 12) to see the trend relating to the date.
7. Time series analysis (Arima Model), Forecasting, Residue and P-value.


For now, these are some of the questions we need to answer, this may change as we progress down our analysis. 


## Dashboard mockup

- What should it look like? 

Some of the data visuals that may be appropriate in answering our questions include:

1. Table
2. Treemap
3. Scorecards
4. Horizontal bar chart 


## Tools 


| Tool | Purpose |
| --- | --- |
| Excel | Exploring the data |
| SQL Server | Cleaning, testing, and analyzing the data |
| Power BI | Visualizing the data via interactive dashboards |
| R| forecasting requirements as outlined in the job description|
| GitHub | Hosting the project documentation and version control|
| Mokkup AI | Designing the wireframe/mockup of the dashboard | 

![Data Analysis Approach for Cancer Incidence in the East of England](assets/images/Flow.jpg)

# Development

## Pseudocode

- What's the general approach in creating this solution from start to finish?

1. Get the data
2. Explore the data in Excel
3. Load the data into SQL Server
4. Clean the data with SQL
5. Test the data with SQL
6. Visualize the data in Power BI
7. Generate the findings based on the insights
8. Write the documentation + commentary
9. Publish the data to GitHub Pages

## Data exploration notes

Data contain 8 columns (Geography type, Geography, Year, Month, Date, Cancer group, Metric, Statistic) and 134380 rows.


- The initial observations with this dataset? What's caught my attention so far?

  ![Excel](assets/images/Excel.jpg)

In this phase, Excel is used for Exploratory Data Analysis (EDA) to assess and clean the dataset before further processing. 

- Key tasks include:

1. Data Overview and Inspection: Row and Column Count: To ensure completeness, check the total number of records and variables.

2. Filtering and Consistency Check: Filter the data to identify relevant columns for analysis, removing errors and inconsistencies.

3. Distinct Value Check: Identify distinct values in each column to spot discrepancies and remove irrelevant data, such as erroneous or duplicate entries.

- Key Columns Overview:

1. Geography Type: Categorized into three types: Cancer Alliance, ICB (Integrated Care Board), and National.

2. Geography: Contains 63 distinct regions across the East of England.

3. Date Information: Time-based information covering the years 2018 to 2024, with data recorded on the first day of each month.

4. Metric: Describes the statistical measurement of cancer diagnoses (observed) with just one records for each value.

5. Statistic: Numeric values representing the actual cancer diagnoses from 0 to 30216.
