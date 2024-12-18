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

## Data cleaning 

- The aim is to refine our dataset to ensure it is structured and ready for analysis. 

The cleaned data should meet the following criteria and constraints:

- Only relevant columns should be retained.
- All data types should be appropriate for the contents of each column.
- No column should contain null values, indicating complete data for all records.

Below is a table outlining the constraints on our cleaned dataset:

| Property | Description |
| --- | --- |
| Number of Rows |134380 |
| Number of Columns | 8 |

Here is a tabular representation of the expected schema for the clean data:

| Column Name | Data Type | Nullable |
| --- | --- | --- |
| Geography type| VARCHAR | NO |
| Geography| VARCHAR | NO |
| Year| VARCHAR | NO |
| Month | VARCHAR | NO |
| Date | VARCHAR | NO |
| Cancer group | VARCHAR | NO |
|  Metric | VARCHAR | NO |
| Statistic| INTEGER | NO |

- What steps are needed to clean and shape the data into the desired format?

1. Remove Unnecessary Columns: Remove irrelevant columns such as Year, Month, and Metric to focus on critical data.
2. Filter Data for East of England: Extract data specific to the East of England region from the geography column (Geography_type, Geography, Date, Cancer_group and Statistic).
3. Format Date Column: Ensure the Date column is in the appropriate date format for consistent analysis (year-month-day=yy/mm/dd).
4. Remove Outliers: Exclude the outlier 'ALL SITES COMBINED' from the Cancer Group column to prevent skewed results.
5. Rename Columns: Rename Geography to Region and Statistic to Cancer_Diagnoses for clarity.
6. View: Create a view so the that can be pushed to power bi.


### Transform the data 


```sql
SELECT 
    Geography_Type,
    Geography AS Region, -- Rename Geography to Region
    CONVERT(DATE, Date, 103) AS Date, -- Format the Date column to proper date format
    Cancer_Group,
    Statistic AS Cancer_Diagnoses     -- Rename Statistic to Cancer_Diagnoses
FROM 
    NHS_CANCER
WHERE 
    Geography = 'East of England'
    AND Cancer_Group != 'All sites combined';
```


### Create the SQL view 

```sql
/*
#1. REMOVE UNNECESSARY COLUMNS (YEAR, MONTH, MATRIC) BY ONLY SELECTING THE ONE WE NEED.

#2. EXTRACT DATA OF EAST OF ENGLAND FROM THE GEOGRAPHY COLUMN.

#3. Format the date column to the appropreate format

#4. REMOVING THE OUTLIER (ALL SITES COMBINED) from Cancer_group 

#5. RENAME THE COLUMN SUCH AS GEOGRAPHY TO REGION AND STATISTIC TO CANCER_DIAGNOSES
*/

-- 1.
Create View for Importation to PowerBi

CREATE VIEW NHS_DATA AS

-- 2.
SELECT 
    Geography_Type,
    Geography AS Region, -- Rename Geography to Region
    CONVERT(DATE, Date, 103) AS Date, -- Format the Date column to proper date format
    Cancer_Group,
    Statistic AS Cancer_Diagnoses     -- Rename Statistic to Cancer_Diagnoses
-- 3.
FROM 
    NHS_CANCER
WHERE 
    Geography = 'East of England'
    AND Cancer_Group != 'All sites combined';

```
 ![Data Cleaning](assets/images/Cleaning data.jpg)

 # Testing 

- Data quality and validation checks

Here are the data quality tests conducted:

1. Row count check

2. Column count check (5)

3. Data typle check (string format, data format and numerical)

4. Duplicate count check ( each records must be unique in the dataset)

5.  Check for Null or Empty Values

6. Outliers check

## EXPECTATION

Row count < 134380 

Column count = 5

Geography_Type = varchar

Region = varchar

Date = Date format

Cancer_Group = varchar

Cancer_Diagnoses = Numerical/Integer

Duplicate = 0

Null value or empty check = 0

### Row count check
```sql
/*
# Rows count check
*/

Select COUNT(*) AS NO_Of_Rows
from NHS_DATA;

```

## Column count check
### SQL query 
```sql
/*
# Columns count check
*/

Select 
   COUNT (*) AS column_count 
From 
   INFORMATION_SCHEMA.COLUMNS
WHERE 
   TABLE_NAME = 'NHS_DATA';
```
### Output 
![Row and column count check](assets/images/count after cleaning - Copy.jpg)


## Data type check
### SQL query 
```sql
/*
# Check the data types of each column from the view by checking the INFORMATION SCHEMA view
*/

-- 1.
Select *
From 
   INFORMATION_SCHEMA.COLUMNS
WHERE 
   TABLE_NAME = 'NHS_DATA';

Select 
   COLUMN_NAME,
   DATA_TYPE
From 
   INFORMATION_SCHEMA.COLUMNS
WHERE 
   TABLE_NAME = 'NHS_DATA'
```
### Output
![Data type check](assets/images/DATA TYPE AND COLUMN NAME - Copy.jpg)


## Duplicate count check
### SQL query 
```sql
/*
# 1. Check for duplicate rows in the view
# 2. Group by the Geography_Type, Region, Date, Cancer_Group, Cancer_Diagnoses.
# 3. Filter for groups with more than one row
*/

-- 1.
SELECT 
    COUNT(*) AS Total_Duplicates
FROM (SELECT Geography_Type, Region, Date, 
      Cancer_Group, Cancer_Diagnoses,
        COUNT(*) AS Duplicate_Count
    FROM 
        NHS_DATA
-- 2.
GROUP BY 
        Geography_Type, Region, Date,
        Cancer_Group, Cancer_Diagnoses
-- 3.
HAVING 
        COUNT(*) > 1 -- Identifies duplicates
) AS Duplicates;
```
### Output
![Duplicate count check](assets/images/DUPLICATE CHECK.jpg)


## Null value or empty check
### SQL query 
```sql
/*
# 1. Check empty roll value in the view
# 2. Base on each of the column
*/

-- 1.
SELECT 
    COUNT(*) AS Total_Empty_Or_Null_Values
FROM 
    NHS_DATA
-- 2.
WHERE 
    Geography_Type IS NULL OR Geography_Type = ''
    OR Region IS NULL OR Region = ''
    OR Date IS NULL OR Date = ''
    OR Cancer_Group IS NULL OR Cancer_Group = ''
    OR Cancer_Diagnoses IS NULL OR Cancer_Diagnoses = '';
```
### Output
![Null value or empty check](assets/images/Toatal null or empty.jpg)


## Outliers check
### SQL query 
```sql
/*
# 1. Calculate Q1, Q3, and IQR for each Cancer_Group.
# 2. Find the outlier in the Cancer_diagnoses column.
# 3. The outlier must not affect the analysis
*/

-- 1.
WITH Quartiles AS (
    SELECT 
        Cancer_Group,
        PERCENTILE_CONT(0.25) WITHIN GROUP (ORDER BY Cancer_Diagnoses) 
            OVER (PARTITION BY Cancer_Group) AS Q1,
        PERCENTILE_CONT(0.75) WITHIN GROUP (ORDER BY Cancer_Diagnoses) 
            OVER (PARTITION BY Cancer_Group) AS Q3
    FROM NHS_DATA
),
-- 2.
IQR_Calculation AS (
    SELECT DISTINCT 
        Cancer_Group,
        Q1,
        Q3,
        (Q3 - Q1) AS IQR,
        (Q1 - 1.5 * (Q3 - Q1)) AS Lower_Bound,
        (Q3 + 1.5 * (Q3 - Q1)) AS Upper_Bound
    FROM Quartiles
),
-- 3.
Outlier_Flagged AS (
    SELECT 
        d.Cancer_Group,
        d.Cancer_Diagnoses,
        i.Lower_Bound,
        i.Upper_Bound,
        CASE 
            WHEN d.Cancer_Diagnoses < i.Lower_Bound OR d.Cancer_Diagnoses > i.Upper_Bound THEN 1
            ELSE 0
        END AS Is_Outlier
    FROM NHS_DATA d
    JOIN IQR_Calculation i
    ON d.Cancer_Group = i.Cancer_Group
)
-- 4.
Display records with outlier flag, bounds, and actual outlier values
SELECT 
    Cancer_Group,
    Cancer_Diagnoses,
    Lower_Bound,
    Upper_Bound,
    CASE 
        WHEN Is_Outlier = 1 THEN Cancer_Diagnoses
        ELSE NULL
    END AS Outlier_Value,
    Is_Outlier
FROM Outlier_Flagged
ORDER BY Cancer_Group, Cancer_Diagnoses;
```
### Output
![outliers](assets/images/Outlier.png)

# Visualization 


## Results


![pbit of Power BI Dashboard](assets/images/Cancer Incidence in the east of land.pbit)

![Dashboard](assets/images/assets/images/Dashboard.png)

This shows the Cancer Incidence trend in the east of england. 

