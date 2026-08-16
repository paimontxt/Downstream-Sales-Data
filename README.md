# Downstream-Sales-Data
Automation for a sales data, reducing the overall data process by 80%

# Background
This is a sample consolidated sales data process automation. In this scenario, a workbook relied entirely on manual data entry and cross-sheet formula links, resulting in a bloated file, slow performance, and high operational risk.

This project introduces a structured ETL pipeline backed by SharePoint, Power Query, a Data Model, and DAX — reducing a file from 170 MB to 20 MB and automating the majority of the sellout data workflow.

## Problem Statement

| Area | Issue |
|---|---|
| Performance | Large data volumes caused slow load times and system crashes |
| File size | Workbook reached 170 MB due to raw data stored in-sheet |
| Manual effort | Data entered manually, increasing error risk |
| Maintainability | Cross-sheet formula dependencies made changes fragile |

## Key Observations

### Data Management
- Data was entered manually, increasing effort and risk of errors
- Numerous Excel formulas linked across worksheets, requiring all data to reside in a single workbook
- Consolidating and restructuring the workbook reduces complexity and improves maintainability

### Workbook Structure
- **No merged cells** — simplifies redesign and data restructuring
- **No pivot tables** — provides flexibility to restructure without impacting reporting components

### File Storage & Collaboration
- Files stored and shared through SharePoint
- Cloud-based environment supports future integration with Power Query and Power Automate

---

## Architecture

SharePoint (Data Lake)
        │
        ▼
  Power Query (ETL)
  ├── Extract: Connect to SharePoint
  ├── Transform: M language transformations
  └── Load: Push to Data Model
        │
        ▼
   Data Model (Structured Layer)
   └── Defines relationships between fact tables
        │
        ▼
      DAX (Measures & KPIs)
      └── Dynamic calculations per filter context
        │
        ▼
   Excel Workbook (Reporting Layer)
   ├── ASL Calculation
   ├── Sell-In Target
   ├── Regular Order Recommendation
   └── Promo NPI Order Reco

---

## Tech Stack

| Tool | Role |
|---|---|
| **Power Query (M)** | Automated ETL — extract from SharePoint, transform, and load into Data Model |
| **Data Model** | Centralized structured layer; defines fact table relationships |
| **DAX** | Measures, calculated columns, and KPIs computed dynamically on filter context |
| **SharePoint** | Cloud data lake — stores 52 weeks of sellout data; primary data source |
| **Power Automate** | Planned — order recommendation notifications and workflow automation |

---

## Improvements Achieved

| Metric | Result |
|---|---|
| File size | 170 MB → **20 MB** |
| Manual coding effort | Reduced by **80%+** |
| Tool refresh & load time | **5–10 minutes** |
| Centralized data range | **52 weeks** of sales data |

- Faster file loading and minimized system crash risk
- Automated sellout data process — part of the Inventory Replenishment Forecasting data entry workflow eliminated
- Centralized data repository for storage and handling
- All reference links from the previous sellout sheet replaced with DAX measures linked to the Power Pivot / Data Model

---

## Updated Sheets

The following sheets have been updated as part of this project:

- `ASL Calculation`
- `Sell-In Target`
- `REGULAR Order Recommendation`
- `PROMO NPI Order Reco`

> All previous sellout sheet reference links have been replaced with DAX measures connected to the Power Pivot / Data Model.

---

## Future-State Roadmap

### Phase 1 — Workbook Architecture ✅ (In Progress)
- [x] Set up SharePoint repository
- [x] Power Query ETL pipeline built and executed
- [x] 52-week Sales Data loaded into Data Model
- [x] DAX measures created; sales sheet links replaced
- [x] Data validation and manipulation completed

### Phase 2 — Automation
- [ ] Redesign workbook architecture — separate raw data, transformation, and reporting layers
- [ ] Centralize all historical raw data in SharePoint as single source of truth
- [ ] Implement Power Automate workflows for automated notifications, approval workflows, and exception handling
- [ ] Order Recommendation Notification *(VBA or Power Automate — TBD)*

### Phase 3 — Advanced Integration *(Future / Access-Dependent)*
- [ ] Explore API-based integrations for direct source system connectivity
- [ ] Near real-time data integration where access permits

---

## Open Items

### Order Form Requirements

Before defining the order form structure and automation approach, the following must be confirmed:

- [ ] Who is the intended recipient or audience?
- [ ] What business purpose does the order form serve?
- [ ] What specific information or fields are required?

## Notes

- **SharePoint** serves as the centralized data platform — cloud collaboration, version control, and secure access management are handled at this layer
- **Alternative integration path:** API-based connectivity can be evaluated in the future if SharePoint-based data access becomes limited or additional system connectivity is required

---

* Supply Chain · Inventory Replenishment Forecasting Tool Improvement*
