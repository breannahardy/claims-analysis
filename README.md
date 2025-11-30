# Claims Analysis

This project analyzes a sample of healthcare claims data from Stony Brook University Hospital.  
The dataset includes claim headers, service lines, and diagnosis codes and is used to explore:

- Provider billing patterns  
- Payer mix  
- Common diagnoses and procedures  
- Service locations (place of service)  
- Diagnosis–procedure combinations  
- Charges by payer  
- A custom analysis of diagnoses associated with the highest total charges  

The work was completed in a Google Colab notebook using Python and pandas.

---

## Dataset Description

The claims data consists of three CSV files:

1. **HEADER file** – `STONYBRK_20240531_HEADER.csv`  
   - One row per claim  
   - Includes fields such as:  
     - `ProspectiveClaimId`  
     - Provider NPIs and names (Billing, Rendering, etc.)  
     - `ServiceFromDate`, `ServiceToDate`  
     - `PrimaryPayerName`, `PrimaryPayerCode`  
     - `PlaceOfService` (CMS POS codes)  

2. **LINE file** – `STONYBRK_20240531_LINE.csv`  
   - One row per service line  
   - Includes:  
     - `ProspectiveClaimId`  
     - `HCPCS` (procedure code)  
     - `Charges`, `Units`  
     - Line-level modifiers and positions  

3. **CODE file** – `STONYBRK_20240531_CODE.csv`  
   - One row per diagnosis code per claim  
   - Includes:  
     - `ProspectiveClaimId`  
     - `CodeValue` (ICD-10 diagnosis code)  
     - `CodePos` and qualifiers  

> (excluded via `.gitignore`).

---
## Repository Structure

```text
claims-analysis/
├─ data/                      # local only, contains the three input CSVs
├─ notebooks/
│  └─ claims_analysis.ipynb   # main analysis notebook
├─ requirements.txt           # Python dependencies
└─ README.md                  # project documentation
```
## How to Run the Notebook
1. Create or Clone the repository**
2. Create virtual environment (required for this assignment)
```
python -m venv .venvx
 .venv\Scripts\activate
```
3. Install required libraries
```
pip install -r requirements.txt
```
4. Add data files to folder
```
STONYBRK_20240531_HEADER.csv
STONYBRK_20240531_LINE.csv
STONYBRK_20240531_CODE.csv
```
5. Open and run notebook using:
- Google Colab
- Juptyer Notebook
```
notebooks/claims_analysis.ipynb
```

## Summary of Key Findings 
- The dataset contains 388 claims, mostly from inpatient hospital (POS 21) encounters.
- Medicare represents over 54% of total claims, making it the dominant payer.
- The most frequent diagnoses include acute respiratory failure (J96.01) and hypertension (I10).
- The most common procedures are 99291 (critical care) and 99213/99214 (office visits).
- The highest-charge diagnoses are severe cardiopulmonary and neurologic conditions, including
J96.01, G93.5, and I61.9.

## Required Libraries
```
pandas
matplotlib
seaborn
google-colab   # optional if running in Google Colab
```

