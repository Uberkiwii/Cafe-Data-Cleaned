# Café Sales Data Cleaning Project
Data retrieved from: https://www.kaggle.com/datasets/ahmedmohamed2003/cafe-sales-dirty-data-for-cleaning-training/data

---

## Overview
This project focuses on cleaning a 10,000-row café transaction dataset using **Python** and **Pandas**.  
The dataset contained missing, inconsistent, and duplicate values that required structured preprocessing before analysis.  
The objective was to produce a validated, analysis-ready dataset for future exploratory analysis or modeling.

---

## Objectives
- Identify and handle missing, inconsistent, and duplicate records.  
- Convert object-type numeric and date columns into correct data types.  
- Impute missing categorical and numerical values using context-based logic.  
- Verify arithmetic consistency across related columns.  
- Export a finalized clean dataset for downstream analytics.

---

## Cleaning Process

### 1. Initial Review
Inspected data structure using `info()` and `head()` to determine column datatypes and missingness.  
Identified that all columns were stored as object types, requiring conversion.

### 2. Duplicate Detection
Checked for duplicates using the unique `Transaction ID` column as a reference.

### 3. Missing Value Assessment
Detected approximately **8.5%** missing data across the dataset.  
Reviewed missingness by column to determine appropriate handling methods.

### 4. Categorical Imputation
Replaced nulls in **Payment Method**, **Location**, and **Item** columns with `'Unknown'`.  
Normalized capitalization using `str.title()` and removed trailing whitespace.

### 5. Numeric Conversion and Imputation
Converted **Quantity**, **Price Per Unit**, and **Total Spent** into numeric datatypes using `pd.to_numeric()`.  
Derived missing values using arithmetic relationships:  
- `Total Spent = Quantity × Price Per Unit`  
- `Price Per Unit = Total Spent ÷ Quantity`  
Remaining nulls were imputed using column means.  

Converted **Transaction Date** to datetime format and dropped rows where the date was missing.  
This removal accounted for less than 5% of data and prevented distortion in any time-based analyses.

### 6. Validation
Validated that `Total Spent` closely matched `Quantity × Price Per Unit` across all rows.  
Achieved over **99%** consistency post-cleaning.  

Confirmed that all missing values were successfully handled.

### 7. Export
Exported the cleaned dataset to: **cleaned_cafe_sales.csv**


---

## Tools & Technologies
| Category | Tools Used |
|-----------|-------------|
| Language | Python |
| Libraries | Pandas, NumPy, Matplotlib |
| Environment | Jupyter Notebook |
| Data Source | CSV file (`dirty_cafe_sales.csv`) |

---

## Results Summary
| Metric | Before Cleaning | After Cleaning |
|---------|----------------|----------------|
| Missing Values | ~8.5% | 0% |
| Invalid Data Types | 5 columns | 0 columns |
| Arithmetic Consistency | ~88% | >99% |

---

## Future Work

- Extend the project to include exploratory data analysis (EDA).
- Visualize category-level trends using Matplotlib or Seaborn.
- Create a Power BI or Tableau dashboard for interactive reporting.
---

## How to Run
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/cafe-cleaning.git
   cd cafe-cleaning
2. Install required packages:
    ```bash
    pip install pandas numpy matplotlib jupyter
3. Launch the notebook:
   ```bash
   jupyter notebook Cafe_Cleaning.ipynb
4. Run all cells to reproduce the cleaning workflow.

---
