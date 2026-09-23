# Hospital Operations & Patient Analytics Dashboard

A 4-page Power BI dashboard built for CityCare Hospital, analyzing patient admissions, readmissions, bed capacity, provider workload, and revenue across 2023–2024.

## Dashboard Pages

### 1. Hospital Overview
- Cards: Total Patients Admitted, Total Revenue, Patient Readmission Rate, Average Stay Duration, Bed Occupancy Rate %
- Monthly Admissions & Revenue Trend (dual-axis line chart)
- Revenue by Insurance Type (donut chart)

### 2. Clinical & Operational Insights
- Cards: Readmission Rate, Readmission >30 Days, Readmission <30 Days
- Readmission Rate by Diagnosis (bar chart)
- Admissions by Ward (bar chart)
- Bed Occupancy by Ward (bar chart)

### 3. Patient & Provider Insights
- Cards: Total Patients, Avg Patient Age, Avg Length of Stay
- Admissions by Age Group (bar chart)
- Admissions by Gender (donut chart)
- Admissions by Specialty (bar chart)

### 4. Financial Insights
- Cards: Total Revenue, Avg Revenue per Patient, Revenue Growth (YoY)
- Revenue by Ward (bar chart)
- Revenue by Diagnosis (bar chart)
- Avg Cost by Insurance Type (bar chart)

## Key Insights

- Diabetes has both the highest readmission rate (46.2%) and high patient volume (3,026 admissions) — a genuine clinical priority, not a small-sample outlier.
- Nephrology & Urology has low admission volume but the 2nd-highest bed occupancy rate (85.8%) — a capacity-planning flag that raw admission counts alone would miss.
- Cardiology is the busiest ward overall (~4.4K admissions) and also has the highest bed occupancy (86%).
- Early readmissions (<30 days: 15.4%) were tracked separately from late ones (>30 days: 22.4%), since early readmissions are a stronger signal of care-quality issues.
- Revenue and admissions volume move closely together month-to-month.
- Year-over-year revenue grew ~2.0% (2023 → 2024), while admissions grew ~2.5%.

## Tools & Techniques Used

- Power BI Desktop — report authoring and data modeling
- DAX — custom measures for readmission rates, bed occupancy, YoY growth, demographic aggregations
- Power Query (M) — data cleaning (fixing Excel serial-date columns)
- Star schema data model — Fact_Admissions connected to Dim_Patient, Dim_Doctor, Dim_Diagnosis, Dim_Ward, and a Dim_Date calendar table

## Data Model

**Fact table:** Fact_Admissions — Encounter_ID, Patient_ID, Admit/Discharge dates, LOS_Days, Admission_Type, Ward_ID, Doctor_ID, Diagnosis_ID, Prior_Visits_12M, Num_Medications, Num_Lab_Procedures, Discharge_Disposition, Insurance_Type, Billing_Amount_INR, Readmitted

**Dimension tables:**
- Dim_Patient — Patient_ID, Gender, Age, City, Age_Group
- Dim_Doctor — Doctor_ID, Doctor_Name, Specialty
- Dim_Diagnosis — Diagnosis_ID, Diagnosis_Group
- Dim_Ward — Ward_ID, Ward_Name, Total_Beds
- Dim_Date — calculated calendar table (2023–2024)

## Notes

Dataset used is synthetic/sample hospital data for demonstration purposes. The .pbix file requires Power BI Desktop to open and explore interactively.
