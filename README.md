# PROGRAMS OFFERED BY NATIONAL COUNCIL FOR HIGHER EDUCATION ANALYSIS
## Table of contents
[Project Overview](#project-overview)  
[Data Source](#data-source)  
[Tools Used](#tools-used)  
[Data Cleaning & Preparation](#data-cleaning&preparation)  
[Explanatory Data Analysis](#explanatory-data-analysis)  
[Data Analysis](#data-analysis)  
[Analysis Results](#analysis-results)  

## Project Overview
- This project analyses different **programs** offered by the **National Council for Higher Education**. The goal is to analyze different programs offered in different learning institutions, courses that are due to expire, expiry trend, accreditation trend and program levels
- The project harnesses **Microsoft Excel** for data preparation and transformation, and **Power BI** for analysis and building interactive dashboards that enable users to explore different programs in different institutions. This project serves as a living tool for monitoring courses that are bound to expire, **Active** and courses that are still **Under Review useful for stakeholders, policy makers and the general public.

[view Dashboard](https://app.powerbi.com/onelake/details/me/dataset/12b7a57d-627d-434b-8342-e9377a7dfe5d/overview?experience=power-bi)


## Data source
 - A CSV file showing different **Programs**, **Institution Names**, **District**, **Accreditation Date**, **Expiry Date** and **Status** was downloaded from the National Council for Higher Education website. [Download here](https://unche.or.ug/all-academic-programs/)
 - A pdf containing the same data was also extracted from the same website to ensure **Consistency**and **Validity**. [Download here](https://unche.or.ug/all-academic-programs/)

## Tools used
- Excel - Data extraction & preparation
- Power BI - Data Analysis, Reports & Visualization

## Data Cleaning & Preparation.
In this initial preparatory stage, we performed the following tasks;
- Extracted data from tables in PDF files using  power query
- Loaded the CSV file into power query
- Promoted Headers
- Removed errors and nulls.
- Assigned the right data types (Dates, Texts, whole numbers)
- Added customized columns grouping Universities, Colleges, Institutions, Training Centres alone.
- Extracted Expiry and Accreditation Year from Expiry Date and Accreditation Date respectively.
- Loaded standardized tables to create proper/clean datasets in excel form and stored them in a folder.

## Explanatory Data Analysis
 Explanatory Data Analysis process focused at answering the following:
-	How many programs are offered?
-	How many Institutions that teach the accredited courses
-	Total programs offered at different institutions
-	What is the Expiry trend of courses?
-	What is the trend of accredited courses?
-	What are the different levels of courses offered? i.e. Bachelors, Masters, PhD, Certificates etc.
-	Status of programs i.e. Active or Under Review

## Data Analysis
To derive meaningful insights from the data, I performed various calculations using DAX formulas Power BI as broken down below:

-	**Total Institutions**
``` Total Institutions = DISTINCTCOUNT(tableExport[Institution Name])```

-	**Total Programs**
``` Total Programs = COUNT(tableExport[Program Name])```

-	**Universities**
``` Universities = CALCULATE(DISTINCTCOUNT('tableExport'[Institution Name]),'tableExport'[Institution type] = "University")```

-	**Colleges**
``` Colleges = CALCULATE( DISTINCTCOUNT('tableExport'[Institution Name]), 'tableExport'[Institution Type] = "College")```


- **Institutes**
```Institutes = CALCULATE(DISTINCTCOUNT('tableExport'[Institution Name]),'tableExport'[Institution Type] = "Institute")```

-	**Training Centres**
``` Training Centres = CALCULATE( DISTINCTCOUNT('tableExport'[Institution Name]),'tableExport'[Institution Type] = "Training Centre")```

-	**Others**
``` Others = CALCULATE(DISTINCTCOUNT('tableExport'[Institution Name]), 'tableExport'[Institution Type] = "Other")```

*Categorizing Institutions into different levels*

```Institution level = if Text.Contains(Text.Lower([Institution Name]), "university") then "University"else if Text.Contains(Text.Lower([Institution Name]), "college") then "College"else if Text.Contains(Text.Lower([Institution Name]), "institute")  or Text.Contains(Text.Lower([Institution Name]), "institution") then "Institute"else if Text.Contains(Text.Lower([Institution Name]), "centre") or Text.Contains(Text.Lower([Institution Name]), "center") then "Training Centre" else "Other"```

*Categorizing Programs into different levels*

```Program levels = if Text.Contains(Text.Lower([Program Name]), "phd") or Text.Contains(Text.Lower([Program Name]), "doctor") then "PhD"else if Text.Contains(Text.Lower([Program Name]), "master") or Text.Contains(Text.Lower([Program Name]), "msc") or Text.Contains(Text.Lower([Program Name]), "mba") then "Master"else if Text.Contains(Text.Lower([Program Name]), "bachelor") or Text.Contains(Text.Lower([Program Name]), "bsc") or Text.Contains(Text.Lower([Program Name]), "ba") then "Bachelor"else if Text.Contains(Text.Lower([Program Name]), "diploma") then "Diploma"else if Text.Contains(Text.Lower([Program Name]), "certificate") then "Certificate"else "Other"```

## Analysis Results
-	3,434 Programs are offered in different institutions of higher learning
-	Out of the 3,434 Programs offered in different institutions, 93.88% are **Active** whereas 6.12% are still **Under Review** 
-	Of the 3,434 Programs are offered in different institutions of higher learning, 1,289 are at **Bachelors level**, 1,190 at **Diploma level**,657 at **Masters level** and 159 at **Phd level**
-	There are 205 institutions of higher learning 82 being **Universities**, 36 **Colleges**, 57 **Institute, 2 **Training Centers** and the 28 categorized in others.
-	Of the 205 institutions, **Kampala** has the highest number of institutions(70) followed by  **Wakiso** with 15 and **Luwero** having 8
-	**Makerere University** offers the highest number of programs (267) both at Diploma, Bachelors, Masters and PhD level.
-	**Kampala International University** is the second institution with a high number of courses (188) being the leading private University with the highest number of programs compared to others
-	**Kyambogo University** appears as the third University with 128 programs offered being the second Public University with the highest number of programs   
-	Uganda Christian University and Nkumba University follow being the second and third Private Universities highest number of programs with 122 and 100 respectively  
-	Between 2020 and 2024 the Accreditation trend is rapidly increasing implying that majority of the courses were accredited between 2020 and 2024 as compared to 2024-2026 where the Accreditation trend is rapidly decreasing meaning that less Programs were accredited between 2024 and 2026   
-	Between 2025 and 2029 the Review Trend of programs is rapidly increasing. This corresponds to the increasing Accreditation trend between 2020 and 2024 implying that courses that were accredited between 2020 and 2024 are bound to be Under Review between 2025 and 2029  
