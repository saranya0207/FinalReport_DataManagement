# Analysis of COVID-19 Cases in Malaysia Using Apache Spark and Hive
<img width="1000" height="300" alt="image" src="https://github.com/user-attachments/assets/709ea15a-2d4b-43c8-a5ae-3a3a212c7340" />

## Overview

This project analyzes COVID-19 case data across Malaysian states using a big data pipeline built on **Apache Hadoop**, **Apache Hive**, and **Apache Spark**, with final exploratory analysis and visualization done in Python (pandas, matplotlib, seaborn).

## Objectives

1. Manage and integrate multiple COVID-19 datasets using Apache Hive and Apache Spark for efficient big data processing.
2. Perform data cleaning and preprocessing to ensure data quality, consistency, and reliability.
3. Analyze the distribution and trends of COVID-19 cases across different states in Malaysia.
4. Examine the relationship between vaccination status and reported COVID-19 cases.
5. Investigate COVID-19 infection patterns across different age groups.

## Research Questions

1. Which states recorded the highest and lowest numbers of COVID-19 cases during the study period?
2. How do COVID-19 case trends vary across different states in Malaysia?
3. What is the distribution of COVID-19 cases according to vaccination status?
4. Is there a noticeable difference in case occurrences among vaccinated, partially vaccinated, and unvaccinated individuals?
5. Which age groups were most affected by COVID-19?

## Data Sources

All datasets were obtained from the Malaysian Government Open Data Portal ([data.gov.my](https://data.gov.my)):

| Dataset | Description |
|---|---|
| **Daily COVID-19 Cases by Vaccination Status and State** | Daily case counts by vaccination status (unvaccinated, partially vaccinated, fully vaccinated, boosted) and state |
| **Daily COVID-19 Cases by State** | Daily new, imported, recovered, active, and cluster cases per state |
| **Daily COVID-19 Cases by Age Group and State** | Daily case counts by age group (children, adolescents, adults, elderly) and state |

## Methodology

### Environment
- Hadoop ecosystem managed via **Apache Ambari**
- **PuTTY** for remote cluster access
- **HDFS** for distributed storage
- **Apache Hive** for data warehousing and SQL-based querying
- **Apache Spark (PySpark)** for distributed processing and analysis
- **Python** (pandas, matplotlib, seaborn) for visualization

### Pipeline Steps
1. **Data Collection** — CSV datasets downloaded from data.gov.my.
2. **Upload to HDFS** — raw files loaded into HDFS (`hdfs dfs -put`).
3. **Hive Table Creation** — external Hive tables created over the HDFS files for `cases`, `vax`, and `age` datasets.
4. **Hive Analysis** — SQL queries (e.g., state-wise total cases) run directly in Hive.
5. **Spark Processing** — a PySpark script (`covid_analysis.py`) run via `spark-submit` for distributed analytical computation.
6. **Exploratory Analysis & Visualization** — cleaned CSV outputs analyzed and visualized in Python/pandas.

## Analysis Performed

- Total COVID-19 cases by state
- Daily trend lines for new, imported, recovered, active, and cluster cases
- Comparative trends of new cases, recoveries, and active cases over time
- Active vs. recovered cases by state
- 7-day moving average of daily cases
- Vaccination status breakdown by state
- Age group distribution of cases
- Correlation heatmap between case variables
- Composite COVID-19 risk score by state (based on new cases, active cases, unvaccinated population, and elderly population)
- Monthly new cases heatmap by state
- Cases by age group and state

## Key Findings

- Selangor consistently recorded the highest case burden across nearly every metric (total cases, active/recovered cases, vaccination breakdown, and risk score), followed by W.P. Kuala Lumpur, Johor, and Sabah.
  
    <img width="1000" height="600" alt="image" src="https://github.com/user-attachments/assets/1ed654cb-6b31-41d2-8859-bb466a5dbd5d" />

- Cases rose gradually through 2021, surged sharply in late 2021–early 2022 (peak outbreak waves), then declined and stabilized through 2023–2025.
  
    <img width="1000" height="600" alt="image" src="https://github.com/user-attachments/assets/3a0ce8cc-715c-4b9d-8a54-06ceb9b9939d" />

- **Adults (18–59)** accounted for the large majority of cases (~71.6%), followed by children, adolescents, and the elderly.
  
    <img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/757b24ad-c552-4d03-9207-a68d0f309d63" />
  
- New, active, and recovered case counts are strongly positively correlated (Pearson r near 1.00).
  
    <img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/5e11fd34-8f2c-41fd-a656-2ac3590597f3" />

- Smaller states/territories (e.g., Perlis, W.P. Labuan, W.P. Putrajaya) showed consistently lower case totals across all analyses.
  
    <img width="1000" height="600" alt="image" src="https://github.com/user-attachments/assets/198e3cc1-0d7b-4988-824e-07bd585f972d" />


## Recommendations

1. Prioritize high-risk states (Selangor, Sabah, Johor, W.P. Kuala Lumpur) for healthcare resource allocation.
2. Target vaccination outreach toward states/groups with high unvaccinated case proportions.
3. Allocate age-specific resources, given the disproportionate impact on adults.
4. Use the risk-scoring approach for ongoing, data-driven outbreak preparedness.

## Repository Contents

- `FinalReport_Data_Management.ipynb` — full notebook with Hive/Spark methodology, Python analysis, charts, and discussion.
- `covid_analysis.py` — PySpark script used for distributed processing (referenced in the report; see GitHub link in notebook).
- Source CSVs (`covid_cases.csv`, `covid_cases_age.csv`, `covid_cases_vaxstatus.csv`) — input datasets used in the Python analysis stage.

## Requirements

- Python
- `pandas`, `matplotlib`, `seaborn`
- Hadoop/Hive/Spark cluster access

## Conclusion

This project demonstrates the use of Apache Hive and Apache Spark to efficiently analyze large-scale COVID-19 data in Malaysia. The analysis identified multiple COVID-19 waves, with the most significant outbreaks occurring in 2021 and early 2022. Overall, the project demonstrates how big data technologies, visualization techniques, and risk modeling can support public health decision-making, resource planning and future outbreak preparedness.
