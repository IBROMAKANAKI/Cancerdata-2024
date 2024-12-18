# Data Portfolio: Excel --> SQL --> Power --> R (Interview Task)	

## Cancer incidence (diagnoses) in the East of England

### Data Source: https://www.cancerdata.nhs.uk/covid-19/rcrd (Geography Tab > Downloads > Download incidence and stage time trend data for all Cancer Alliances and cancer sites (~15 MB))																	
Date Downloaded: 18th November 2024	

![East of England](assets/images/East of England.png)

# Table of contents 

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

