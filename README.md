# 🏥 OptiCare Healthcare Analytics

### Power BI Healthcare Analytics Dashboard

A three-page Power BI dashboard designed to analyse **patient outcomes, 30-day readmissions, operational performance, treatment costs and data quality** across a synthetic healthcare network.

The project demonstrates an end-to-end analytics workflow covering **data preparation, data modelling, DAX measures, interactive reporting and analytical interpretation**.

---

## 🎯 Business Objective

Healthcare organisations need reliable reporting to understand where differences in patient outcomes, operational performance and costs are occurring.

The objective of this dashboard is to provide an interactive view of:

- Patient volume and encounter trends
- 30-day readmission patterns
- Mortality and patient satisfaction
- Treatment costs
- Waiting times and length of stay
- Hospital and department variation
- Data quality issues requiring further investigation

The dashboard is designed as an **analytical decision-support tool**, helping users identify areas that may warrant deeper clinical or operational review.

---

## 📊 Dashboard

### 1. Executive Overview

Provides a high-level view of healthcare network performance through key KPIs and trends.

**Key metrics:**
- Total Patients
- Total Encounters
- Total Treatment Cost
- 30-Day Readmission Rate
- Mortality Rate
- Average Length of Stay

![Executive Overview](screenshots/executive-overview.png)

---

### 2. Patient Outcomes & Readmission Intelligence

Examines 30-day readmission patterns across different patient and encounter characteristics.

**Analysis includes:**
- Readmission rate by diagnosis
- Readmission rate by age group
- Readmission rate by chronic condition
- Readmission rate by admission type
- Mortality
- Patient satisfaction
- Length of stay

![Patient Outcomes & Readmission Intelligence](screenshots/patient-outcomes-readmission.png)

---

### 3. Operations, Cost & Data Quality

Explores operational performance, treatment costs and data reliability across the healthcare network.

**Analysis includes:**
- Average waiting time by department
- Treatment cost by department
- Treatment cost vs length of stay
- Average length of stay by hospital
- Missing and invalid data
- Duplicate records identified during preparation

![Operations, Cost & Data Quality](screenshots/operations-cost-data-quality.png)

---

## 🛠️ Tools & Technologies

| Area | Tools |
|---|---|
| Business Intelligence | Power BI |
| Data Transformation | Power Query |
| Data Modelling | Star Schema |
| Calculations | DAX |
| Data Analysis | SQL, Python |
| Data Preparation | Power Query, Python |
| Visualisation | Power BI |
| Version Control | GitHub |

---

## 🧩 Data Model

The project uses a **star schema** with the encounter table as the central fact table.

### Fact Table
- `Fact_Encounter`

### Dimension Tables
- `Dim_Patient`
- `Dim_Hospital`
- `Dim_Department`
- `Dim_Diagnosis`
- `Dim_Treatment`
- `Dim_Calendar`

The model uses a one-to-many relationship between dimensions and the encounter fact table, supporting consistent filtering and KPI calculations.

---

## 🔄 Data Preparation

The raw healthcare dataset required several preparation and validation steps before reporting.

### Data quality handling included:

- Removed 250 duplicate encounter records
- Identified 600 encounters with missing diagnosis information
- Identified 480 encounters with missing discharge dates
- Identified 100 invalid waiting-time values
- Treated invalid negative waiting times as missing
- Retained records with missing diagnosis or discharge information for monitoring rather than removing them
- Standardised data types and transformed fields for reporting
- Created patient age groups for cohort analysis

---
## 📐 Key DAX Measures

The dashboard uses DAX measures to calculate core healthcare KPIs and support comparative analysis.

**Total Encounters**
`COUNTROWS(Fact_Encounter)`

**Total Treatment Cost**
`SUM(Fact_Encounter[Treatment_Cost])`

**30-Day Readmission Rate**
`DIVIDE([Readmitted Encounters], [Total Encounters])`

**Mortality Rate**
`DIVIDE([Deceased Encounters], [Total Encounters])`

Additional DAX was used for network-level comparisons and department-level readmission analysis.

## 🔎 Key Analytical Areas

### Patient Outcomes

The dashboard compares observed readmission and mortality patterns across patient and encounter cohorts.

### Operational Performance

Waiting time and length of stay are analysed across departments and hospitals to identify areas of variation.

### Cost Analysis

Treatment costs are examined by department and alongside length of stay to identify patterns and potential outliers.

### Data Quality

Missing values, duplicate records and invalid measurements are explicitly monitored rather than hidden from the reporting process.

## ⚠️ Interpretation & Limitations

This project uses **synthetic healthcare data** and contains no real patient information.

The dashboard identifies observed patterns and associations within the dataset. Differences between hospitals, departments or patient groups should not be interpreted as evidence of causation or clinical effectiveness.

For example, a higher readmission rate in one cohort may indicate an area for further investigation, but the dashboard alone cannot establish why the difference exists.

The results are intended for **analytical demonstration and portfolio purposes**, not clinical decision-making.

## 🚀 Future Improvements

Potential extensions to the dashboard include:

- Drill-through pages for hospital and department investigation
- Additional time-based analysis
- Expanded data-quality monitoring
- Further investigation of readmission patterns
- Automated data refresh workflows
- Power BI Service deployment and sharing
