# 📋 Summary Report — Ride Booking Data Analysis

---

## 📦 Dataset Overview

| Property | Value |
|----------|-------|
| Total Records | 1,50,000 |
| Total Features | 21 |
| Time Period | 365 days (Year 2024) |
| Booking Statuses | 5 (Completed, Cancelled by Customer, Cancelled by Driver, Incomplete, etc.) |
| Vehicle Types | 7 |
| Unique Locations | 176 pickup & 176 drop locations |

---

## 1️⃣ Data Cleaning & Preprocessing

- Dataset had **no duplicate rows** after cleaning
- Missing values were found in several columns before cleaning:
  - `Avg VTAT` — 10,500 nulls
  - `Avg CTAT` — 48,000 nulls
  - `Booking Value`, `Ride Distance`, `Payment Method` — 48,000 nulls each
  - `Driver Ratings`, `Customer Rating` — 57,000 nulls each
- After cleaning: **0 null values** across all 21 columns
- Categorical columns were standardized using strip + title case
- `Date` and `Time` columns were converted to proper datetime format

---

## 2️⃣ Descriptive Analysis

### 🚗 Vehicle Type Popularity

| Vehicle Type | Bookings |
|--------------|----------|
| Auto | 37,419 *(Most Popular)* |
| Go Mini | 29,806 |
| Go Sedan | 27,141 |
| Bike | 22,517 |
| Premier Sedan | 18,111 |
| Ebike | 10,557 |
| Uber XL | 4,449 *(Least Popular)* |

**Insight:** Auto leads with 25% of total bookings. Uber XL has the least demand, likely due to higher pricing.

---

### 💰 Ride Distance & Booking Value

| Metric | Value |
|--------|-------|
| Average Ride Distance | **24.34 km** |
| Average Booking Value | **₹478.12** |

---

### ⭐ Ratings Distribution

| Metric | Value |
|--------|-------|
| Average Driver Rating | **4.26 / 5.0** |
| Highest Driver Rating | 5.0 |
| Lowest Driver Rating | 3.0 |
| Average Customer Rating | **4.40 / 5.0** |

**Insight:** Both drivers and customers are rated above 4.0 on average, indicating overall satisfaction on the platform.

---

### ❌ Cancellation Reasons

**By Customer (Top reasons):**

| Reason | Count |
|--------|-------|
| Wrong Address | 2,362 |
| Change Of Plans | 2,353 |
| Driver Not Moving Towards Pickup | 2,335 |
| Driver Asked To Cancel | 2,295 |
| AC Is Not Working | 1,155 |

**By Driver (Top reasons):**

| Reason | Count |
|--------|-------|
| Customer Related Issue | 6,837 |
| Customer Was Coughing/Sick | 6,751 |
| Personal & Car Related Issues | 6,726 |
| More Than Permitted People | 6,686 |

**Insight:** Wrong address is the top customer cancellation reason — suggesting better location pinning in the app could reduce cancellations.

---

## 3️⃣ Customer Behavior Insights

- **Total Cancellations:** 37,500 rides cancelled
- Frequent cancellers had a maximum of only **2 cancellations each**, showing no extreme repeat offenders in the dataset
- Cancellation patterns by day of week and hour of day were visualized — charts available in the notebook

---

## 4️⃣ Driver Performance Evaluation

| Metric | Value |
|--------|-------|
| Average Driver Rating | 4.26 / 5.0 |
| Total Driver Cancellations | 37,500 |
| Top Driver Cancellation Reason | Customer Related Issue (6,837) |

**Insight:** Driver cancellations are fairly evenly spread across reasons, suggesting no single dominant issue but a systemic challenge in ride matching.

---

## 5️⃣ Operational Metrics

### ⏱️ Average VTAT & CTAT by Vehicle Type

| Vehicle Type | Avg VTAT (min) | Avg CTAT (min) |
|--------------|---------------|---------------|
| Auto | 8.44 | 29.03 |
| Bike | 8.49 | 29.07 |
| Ebike | 8.47 | 29.06 |
| Go Mini | 8.46 | 29.05 |
| Go Sedan | 8.39 | 28.96 |
| Premier Sedan | 8.43 | 29.08 |
| Uber XL | 8.56 | 29.08 |

**Insight:** VTAT and CTAT are fairly consistent across all vehicle types (~8.4 min and ~29 min respectively), indicating uniform operational performance.

- **Top Pickup Location:** Khandsa (949 bookings)
- **Top Drop Location:** Ashram (936 bookings)
- Peak demand locations and time slots are visualized in the notebook

---

## 🔑 Key Findings

1. **Auto is the most preferred vehicle** — accounting for 25% of all bookings
2. **Wrong address** is the #1 reason for customer cancellations — a UX/app problem
3. **Driver ratings average 4.26** and customer ratings average 4.40 — healthy satisfaction levels
4. **Average booking value is ₹478** with an average ride distance of 24.34 km
5. **VTAT and CTAT are uniform** across all vehicle types — operationally consistent
6. **Khandsa and Ashram** are the busiest pickup and drop locations respectively
7. **37,500 total cancellations** — 25% of total bookings, which is a significant churn metric

---

*Analysis performed using Python — pandas, numpy, matplotlib, seaborn*
