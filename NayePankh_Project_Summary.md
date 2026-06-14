# NayePankh Foundation — Data Analytics Project Summary

**Project Type:** Option 2 — Data Analytics Project (Excel Analysis + Power BI Dashboard)
**Datasets Used:** Donations Dataset & Volunteers Dataset (synthetic/sample data created for demonstration purposes)

---

## 1. About the Datasets

Since real organizational data was not available, two realistic **synthetic datasets** were created to simulate NayePankh Foundation's operations.

### 1.1 Donations Dataset
- **Total Records:** 1,500 donation transactions
- **Time Period:** January 2024 – December 2025
- **Columns:**
  - `Donor_ID`, `Donor_Name`, `Email` — donor identity
  - `Date` — date of donation
  - `Amount_INR` — donation amount (₹)
  - `Payment_Mode` — UPI, Credit Card, Debit Card, Net Banking, Cash, Bank Transfer
  - `Campaign_Name` — 10 campaigns (e.g., Education for All, Scholarship Fund, Tree Plantation Drive)
  - `City` — donor's city
  - `Recurring_Donor` — Yes/No

### 1.2 Volunteers Dataset
- **Total Records:** 800 volunteer profiles
- **Columns:**
  - `Volunteer_ID`, `Volunteer_Name`, `Age`, `Gender`, `Email`, `Phone`
  - `Join_Date` — date volunteer joined
  - `City`, `Education_Level`
  - `Activity_Type` — Teaching, Social Media, Event Management, Content Writing, Administration, Fundraising Support, Field Survey, Logistics
  - `Hours_Contributed_Per_Month`
  - `Performance_Rating` (scale 2.0 – 5.0)
  - `Status` — Active / Inactive / On Leave

---

## 2. Excel Analysis — What We Did

Both datasets were imported into Excel as Tables and analyzed using **PivotTables, helper columns, and summary formulas**, with a separate sheet created for each analysis.

### 2.1 Donations Dataset (Excel)
| Analysis | Method | Key Result |
|---|---|---|
| Donation Analysis (overall stats) | Formulas (`SUM`, `AVERAGE`, `MAX`, `MIN`, `COUNT`) | Total = ₹57,23,284.69, Avg = ₹3,815.52, Max = ₹49,677.31, Min = ₹101.26 |
| Donation Trend Analysis | PivotTable, `Date` grouped by Month & Year | Monthly donation pattern from Jan 2024 – Dec 2025 |
| Top Campaigns Analysis | PivotTable, `Campaign_Name` vs Sum of `Amount_INR` | Scholarship Fund tops the list |
| City-wise Donation Analysis | PivotTable, `City` vs Sum of `Amount_INR` | Lucknow, Indore, Pune lead in total donations |
| Payment Mode Distribution | PivotTable, `Payment_Mode` vs Sum of `Amount_INR` | UPI is the most-used payment mode |
| Recurring vs One-time Donors | PivotTable, `Recurring_Donor` vs Count & Sum | One-time donors dominate by count and value |
| Top 10 Donors | PivotTable + Value Filter (Top 10 by Sum) | Identified highest-contributing individual donors |

### 2.2 Volunteers Dataset (Excel)
| Analysis | Method | Key Result |
|---|---|---|
| Status Distribution | PivotTable, `Status` vs Count | 479 Active, 233 Inactive, 88 On Leave |
| Volunteer Growth Trend | PivotTable, `Join_Date` grouped by Month & Year | Joining pattern over 2024–2025 |
| Activity Type Distribution | PivotTable, `Activity_Type` vs Count | Content Writing has the most volunteers (115) |
| City-wise Volunteer Count | PivotTable, `City` vs Count | Kolkata, Agra, Ahmedabad have the most volunteers |
| Avg Hours Contributed | PivotTable, Average of `Hours_Contributed_Per_Month` by Activity_Type/City | Identified most time-intensive activities |
| Avg Performance Rating | PivotTable, Average of `Performance_Rating` by Status | Overall average rating = 3.70 |
| Age Group Analysis | Helper column (`IFS` formula) + PivotTable | Distribution across 18-25, 26-35, 36-45, 46+ |
| Gender Distribution | PivotTable, `Gender` vs Count | 389 Female, 374 Male, 37 Other |
| Education vs Activity Type | Cross-tab PivotTable | Mapped education levels to volunteer roles |

---

## 3. Power BI Dashboard — What We Built

A **3-page interactive dashboard** ("nayepankh dashboard") was built in Power BI Desktop with a consistent **black & white theme**.

### Page 1: Home Page
- Introductory image and mission statement of NayePankh Foundation
- Navigation buttons: **Home Page**, **Donation Dashboard**, **Volunteer Dashboard**

### Page 2: Donation Dashboard
**KPI Cards:**
- Total Donations: 1.5K
- Total Donation Amount: ₹5.72M
- Avg Donation Amount: ₹3.82K
- Max Donation Amount: ₹49.68K
- Min Donation Amount: ₹101.26

**Visuals:**
- **Donation Trend Over Time** — Area chart (Month-Year vs Sum of Amount)
- **Top Campaigns by Funds Raised** — Bar chart (Top 5 campaigns)
- **Payment Mode Distribution** — Bar chart
- **Top 5 Donors** — Bar chart by total contribution

**Slicers:** Select Campaign Name, Select City

### Page 3: Volunteer Dashboard
**KPI Cards (using DAX measures):**
- Total Volunteers: 800
- Total Active Volunteers: 479
- Total Inactive Volunteers: 233
- On Leave Volunteers: 88
- Total Hours Contributed: 10.85K
- Avg Performance Rating: 3.70

**Visuals:**
- **Volunteer Growth Over Time** — Area chart (Month-Year vs Count of Volunteers)
- **Activity Type Distribution** — Bar chart
- **Gender Distribution** — Bar chart
- **Age Group Distribution** — Bar chart

**Slicers:** Select City, Select Activity Type

**DAX Measures Created:**
```
Active Volunteers = CALCULATE(COUNTROWS(volunteers_dataset), volunteers_dataset[Status] = "Active")
Inactive Volunteers = CALCULATE(COUNTROWS(volunteers_dataset), volunteers_dataset[Status] = "Inactive")
On Leave Volunteers = CALCULATE(COUNTROWS(volunteers_dataset), volunteers_dataset[Status] = "On Leave")
```

---

## 4. Key Insights

### Donations
- Total funds raised: **₹57.23 lakh** across 1,500 transactions
- **Scholarship Fund** (₹9.30 lakh) and **Education for All** (₹7.42 lakh) are the top-performing campaigns
- **UPI** (₹21.88 lakh) is the dominant payment mode, far ahead of Credit Card (₹10.41 lakh)
- Only **368 out of 1,500 (~24.5%)** donations are recurring — a large opportunity to convert one-time donors into recurring supporters
- **Lucknow, Indore, and Pune** are the top-contributing cities

### Volunteers
- Of 800 volunteers, **479 (~60%) are Active**, while **233 (~29%) are Inactive** — retention is an area for improvement
- **Content Writing, Event Management, and Social Media** are the most popular activity types
- Volunteers have contributed a combined **10,852 hours/month**
- Average performance rating across all volunteers is **3.70/5.0**
- Gender distribution is fairly balanced (389 Female, 374 Male, 37 Other)

---

## 5. Recommendations

1. **Convert one-time donors to recurring donors** — only ~24.5% of donations are recurring; targeted email/UPI auto-pay campaigns could improve donor retention
2. **Focus fundraising efforts on top-performing campaigns** (Scholarship Fund, Education for All) and replicate their messaging strategy for lower-performing campaigns
3. **Promote UPI-based donations** further since it's already the most preferred mode — frictionless payment increases conversions
4. **Re-engage inactive volunteers** (233 volunteers, ~29%) through check-in surveys or flexible volunteering options
5. **Align volunteer recruitment with high-donation cities** (Lucknow, Indore, Pune) to build local community presence and improve on-ground campaign delivery

---

## 6. Tools Used
- **Microsoft Excel / WPS Office** — Data cleaning, PivotTables, formulas (SUM, AVERAGE, IFS), trend grouping
- **Power BI Desktop** — Interactive dashboard, DAX measures, slicers, multi-page navigation
- **Python (pandas)** — Synthetic dataset generation for the project

---

*Note: All data used in this project is synthetic/sample data created for demonstration purposes as part of the NayePankh Foundation Data Analytics Internship assignment.*