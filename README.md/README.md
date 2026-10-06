# 🏥 Hospital Operations, Patient Flow & Readmission Analytics

## 📊 Power BI Data Analytics Project

This project analyzes hospital patient encounters, readmission patterns, patient demographics, hospital operations, and clinical treatment information using **Microsoft Power BI**.

The goal is to transform raw hospital data into an interactive analytics dashboard that helps identify important patterns related to **patient flow, hospital utilization, and 30-day readmission**.

---

## 🎯 Project Objective

The main objectives of this project are:

- Analyze overall hospital encounters and patient volume
- Understand patient demographic distributions
- Analyze hospital admission and discharge patterns
- Identify 30-day readmission patterns
- Analyze length of hospital stay
- Study medication, laboratory, procedure, and diagnosis activity
- Analyze clinical indicators such as A1C and glucose results
- Identify factors associated with patient readmission
- Provide interactive dashboards for hospital performance analysis

---

## 🗂️ Dataset

The project uses the publicly available:

**Diabetes 130-US Hospitals for Years 1999–2008**

### Dataset Information

- **101,766 hospital encounters**
- **130 US hospitals / integrated delivery networks**
- Data period: **1999–2008**
- Patient encounter and clinical information
- Readmission information
- Admission and discharge information
- Medication and laboratory information

### Dataset Source

UCI Machine Learning Repository:

https://archive.ics.uci.edu/dataset/296/diabetes+130+us+hospitals+for+years+1999-2008

---

## 🛠️ Tools & Technologies

- **Microsoft Power BI**
- **Power Query**
- **DAX**
- Data Modeling
- Interactive Data Visualization

---

## 🔄 Project Workflow

```text
Raw Hospital Dataset
        ↓
Data Import
        ↓
Power Query Data Cleaning
        ↓
Data Transformation
        ↓
Mapping Tables
        ↓
Data Modeling & Relationships
        ↓
DAX Measures
        ↓
Interactive Dashboard Development
        ↓
Advanced Analytics
        ↓
Final Hospital Analytics Report
```

---

## 🧹 Data Cleaning & Transformation

Power Query was used to prepare the raw dataset for analysis.

### Main cleaning activities

- Replaced unknown `?` values with `Unknown`
- Removed the highly incomplete `weight` column
- Cleaned medical specialty information
- Cleaned payer information
- Cleaned diagnosis fields
- Checked duplicate encounters
- Prepared admission type mapping
- Prepared discharge disposition mapping
- Prepared admission source mapping
- Created an age-group dimension for correct chronological sorting

---

## 🧩 Data Modeling

The project uses separate mapping/dimension tables to improve the data model.

### Dimension Tables

- `Dim_Admission_Type`
- `Dim_Discharge`
- `Dim_Admission_Source`
- `Dim_Age`

These tables are connected to the main `diabetic_data` table using appropriate relationships.

---

## 📐 DAX Measures

Important DAX measures created in the project include:

### Total Encounters

```DAX
Total Encounters = COUNTROWS(diabetic_data)
```

### Total Patients

```DAX
Total Patients = DISTINCTCOUNT(diabetic_data[patient_nbr])
```

### Readmitted Within 30 Days

```DAX
Readmitted <30 Days =
CALCULATE(
    COUNTROWS(diabetic_data),
    diabetic_data[readmitted] = "<30"
)
```

### Readmission Rate

```DAX
Readmission Rate =
DIVIDE(
    [Readmitted <30 Days],
    [Total Encounters],
    0
)
```

### Average Length of Stay

```DAX
Average Length of Stay =
AVERAGE(diabetic_data[time_in_hospital])
```

### Average Medications

```DAX
Average Medications =
AVERAGE(diabetic_data[num_medications])
```

### Total Procedures

```DAX
Total Procedures =
SUM(diabetic_data[num_procedures])
```

### Average Lab Procedures

```DAX
Average Lab Procedures =
AVERAGE(diabetic_data[num_lab_procedures])
```

### Average Diagnoses

```DAX
Average Diagnoses =
AVERAGE(diabetic_data[number_diagnoses])
```

### Total Readmissions

```DAX
Total Readmissions =
CALCULATE(
    COUNTROWS(diabetic_data),
    diabetic_data[readmitted] <> "NO"
)
```

---

# 📊 Dashboard Pages

## 1. Hospital Operations & Readmission Overview

Provides a high-level summary of hospital performance.

### Key KPIs

- Total Encounters
- Total Patients
- Readmitted Within 30 Days
- Readmission Rate
- Average Length of Stay

### Analysis

- Readmission Status
- Readmission by Age Group
- Readmission by Gender
- Average Length of Stay by Readmission Status
- Encounters by Admission Type
- Encounters by Discharge Disposition
- Encounters by Admission Source

---

## 2. Patient Demographics Analysis

Analyzes the demographic characteristics of patients.

### Analysis

- Patient distribution by age group
- Patient distribution by gender
- Patient distribution by race
- Readmission patterns by age group
- Readmission patterns by gender
- Average length of stay by age group

---

## 3. Hospital Operations Analysis

Focuses on hospital utilization and operational activity.

### Analysis

- Average length of stay
- Average medications
- Average laboratory procedures
- Average diagnoses
- Total procedures
- Length of stay by admission type
- Encounters by admission type
- Encounters by admission source
- Encounters by discharge disposition
- Procedures by admission type

---

## 4. Readmission Analysis

Focuses specifically on patient readmission behavior.

### Analysis

- Total readmissions
- 30-day readmission rate
- Readmission status
- Readmission by age
- Readmission by gender
- Readmission by admission type
- Readmission by length of stay
- Readmission by previous inpatient visits
- Readmission by previous emergency visits
- Readmission by previous outpatient visits

---

## 5. Clinical & Treatment Analysis

Analyzes clinical and treatment-related information.

### Analysis

- Encounters by medical specialty
- Readmission by medical specialty
- A1C result distribution
- Glucose result distribution
- Average medications by A1C result
- Average length of stay by A1C result
- Average diagnoses by readmission status
- Total procedures by readmission status

---

# 🔎 Advanced Power BI Analytics

## Key Influencers

The Key Influencers visual is used to investigate factors associated with **30-day readmission**.

It helps explore relationships between readmission and variables such as:

- Age
- Gender
- Race
- Previous inpatient visits
- Emergency visits
- Outpatient visits
- Length of stay
- Medications
- Laboratory procedures
- Diagnoses
- Medical specialty
- A1C results
- Glucose results

---

## 🌳 Decomposition Tree

The Decomposition Tree provides an interactive way to break down readmissions across multiple dimensions.

Example analysis path:

```text
Total Readmissions
        ↓
Age Group
        ↓
Gender
        ↓
Medical Specialty
        ↓
A1C Result
        ↓
Previous Inpatient Visits
```

---

# 📈 Key Insights

Some important observations from the analysis include:

- The dataset contains more than **100K hospital encounters**.
- Patients aged **60–80 years** represent a large share of encounters.
- Approximately **11.6% of encounters were readmitted within 30 days**.
- Hospital length of stay varies across admission and readmission groups.
- Previous inpatient, emergency, and outpatient utilization can be explored as important readmission-related factors.
- A large proportion of encounters have missing/unknown A1C and glucose test results.
- Medical specialty distribution is highly concentrated in a few specialties.
- Admission and discharge patterns show significant differences across hospital encounters.

> Note: Dashboard values may vary depending on filters and selections applied in Power BI.

---

# 💡 Business Recommendations

Based on the analysis, hospitals could:

1. Monitor patients with previous inpatient utilization more closely.
2. Identify high-risk patient segments for early intervention.
3. Improve follow-up planning after discharge.
4. Analyze long-stay patients for potential readmission risk.
5. Improve documentation and availability of clinical test results.
6. Monitor readmission trends by age, gender, admission type, and specialty.
7. Use data-driven patient management strategies to reduce avoidable readmissions.

---

# 📁 Repository Structure

```text
hospital-readmission-powerbi-analytics/
│
├── README.md
├── Hospital_Readmission_Analytics.pbix
│
├── screenshots/
│   ├── executive-overview.png
│   ├── patient-demographics.png
│   ├── hospital-operations.png
│   ├── readmission-analysis.png
│   ├── clinical-treatment.png
│   ├── readmission-drivers.png
│   └── readmission-breakdown.png
│
└── documentation/
    └── project-report.pdf
```

---

# 🎓 Skills Demonstrated

- Power BI
- Power Query
- DAX
- Data Cleaning
- Data Transformation
- Data Modeling
- Data Visualization
- KPI Development
- Dashboard Design
- Healthcare Analytics
- Readmission Analysis
- Interactive Analytics
- Business Intelligence
- Data Storytelling

---

# 🚀 Future Scope

Future improvements could include:

- Predictive readmission modeling
- Patient risk scoring
- Additional clinical indicators
- Real-time hospital data integration
- Automated reporting
- Advanced statistical analysis
- Machine learning-based readmission prediction

---

# 👨‍💻 Author

**Nitish Kumar Yadav**

B.Tech Student | Aspiring Data Analyst

**Skills:** Power BI · SQL · Python · Excel · Pandas · NumPy · DAX · Power Query

---

## 📌 Project Status

**Completed ✅**

Built as a final-year Data Analytics project using Microsoft Power BI.
