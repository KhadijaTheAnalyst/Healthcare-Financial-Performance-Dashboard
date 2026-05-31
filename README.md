# Healthcare Financial Performance Dashboard

A Power BI dashboard delivering executive-ready healthcare billing and financial insights across providers, departments, patient demographics, and locations.

> *"Even simple dashboards can deliver strong value when the data model is solid and the reporting is built with the end user in mind."*

---

## Project Overview

| Attribute | Detail |
|-----------|--------|
| **Industry** | Healthcare |
| **Role** | Freelance Data Analyst |
| **Tool** | Power BI |
| **Dataset Size** | 5,000 patients · 5,000 visits |
| **Scope** | Financial performance, billing analysis, patient & provider analytics |

This dashboard was delivered for a client as a freelance project. While intentionally scoped to be clean and focused, it demonstrates the importance of domain understanding when working with healthcare and patient-related data — where accuracy, structure, and clarity are critical.

---

## Dashboard Focus Areas

- **Financial Performance** — Treatment costs, medication costs, insurance coverage, room charges, and payment status across the portfolio
- **Provider Analytics** — Performance and billing breakdown by individual providers and departments
- **Patient Demographics** — Analysis by age, gender, race, city, and insurance provider
- **Department & Diagnosis Insights** — Cost and volume trends by department, diagnosis, and procedure type
- **Operational Metrics** — Service type (Inpatient vs Outpatient), emergency visits, referral sources, room types, and satisfaction scores
- **Flexible Filtering** — Parameters and slicers enabling dynamic analysis across any dimension

---

## Data Model

Star schema with `visits` as the central fact table, linked to 7 dimension tables:

```
                    ┌─────────────┐
                    │   visits    │  ← Fact Table (5,000 rows)
                    │  (fact)     │
                    └──────┬──────┘
          ┌────────────────┼────────────────────┐
          │                │                    │
    ┌─────▼──────┐  ┌──────▼──────┐   ┌────────▼──────┐
    │  patients  │  │  providers  │   │  departments  │
    └─────┬──────┘  └─────────────┘   └───────────────┘
          │
    ┌─────▼──────┐
    │   cities   │
    └────────────┘

    + diagnoses · procedures · insurance  (lookup tables)
```

### Table Descriptions

| Table | Rows | Key Fields |
|-------|------|-----------|
| `visits.csv` | 5,000 | Date, costs, satisfaction, service type, payment status, room type |
| `patients.csv` | 4,973 | Patient ID, name, gender, age, city, race |
| `providers.csv` | 5 | Provider ID, name, gender, nationality, age |
| `departments.csv` | 5 | Department ID, department name |
| `diagnoses.csv` | 5 | Diagnosis ID, diagnosis name |
| `procedures.csv` | 5 | Procedure ID, procedure name |
| `insurance.csv` | 3 | Insurance ID, provider name |
| `cities.csv` | 40 | City ID, city name, state/region |

### Key Metrics in `visits.csv`

| Field | Description |
|-------|-------------|
| Treatment Cost | Primary billing amount per visit |
| Medication Cost | Additional medication charges |
| Insurance Coverage | Amount covered by insurer |
| Room Charges (daily rate) | Per-day room cost for inpatients |
| Patient Satisfaction Score | 1–10 rating per visit |
| Payment Status | Paid / Pending / Outstanding |
| Service Type | Inpatient / Outpatient |
| Emergency Visit | Yes / No flag |
| Referral Source | Self-Referral / Emergency / GP / Specialist |

---

## Repository Structure

```
Healthcare-Financial-Performance-Dashboard/
│
├── data/
│   ├── visits.csv          ← Fact table: 5,000 visit records
│   ├── patients.csv        ← 4,973 patient records
│   ├── providers.csv       ← 5 healthcare providers
│   ├── departments.csv     ← 5 clinical departments
│   ├── diagnoses.csv       ← 5 diagnosis types
│   ├── procedures.csv      ← 5 procedure types
│   ├── insurance.csv       ← 3 insurance providers
│   └── cities.csv          ← 40 cities across UK regions
│
├── Healthcare_Analytics.pbix   ← Power BI report file
│
└── README.md
```

---

## Key Design Decisions

- **Star schema over flat file** — Keeps the model clean, reduces redundancy, and makes measures easier to write and maintain
- **Responsible data handling** — Patient names are included only in the patient dimension; the fact table references IDs only, ensuring aggregations never expose individual-level sensitive data unnecessarily
- **Executive-first layout** — KPI cards at the top, drill-down capability below; designed for a non-technical decision-maker audience
- **Parameterised filters** — Slicers for provider, department, date range, service type, insurance, and location allow flexible self-service exploration

---

## Tools & Skills

| Area | Detail |
|------|--------|
| Data Modelling | Star schema design in Power BI |
| DAX | Custom measures for cost totals, coverage ratios, satisfaction averages |
| Visualisation | KPI cards, bar/line charts, tables, map visuals |
| UX Design | Clean layout, consistent colour palette, executive-ready formatting |
| Domain Knowledge | Healthcare billing, insurance coverage, inpatient/outpatient classification |

---

## Author

**Khadija Mustafa** — Data Analyst (Freelance & Full-Time)  
*Excel · SQL · Power BI · Tableau · BigQuery · Python · R · Google-Certified*  
📍 Luxembourg | 📧 engr.khadija.hussain@gmail.com  
[LinkedIn](https://www.linkedin.com/in/khadija-mustafa-98344527b/) · [GitHub](https://github.com/KhadijaTheAnalyst)

---
*Delivered as a freelance project. Dataset is synthetic/anonymised for portfolio use.*
