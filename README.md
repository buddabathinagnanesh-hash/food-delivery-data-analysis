# Food Delivery Data Analysis

## Project Overview

This project focuses on understanding and cleaning a food delivery dataset using Python and Pandas.

The objective is to inspect the dataset, identify data-quality issues, investigate inconsistencies, and prepare a cleaned dataset for future analysis.

## Project Objectives

- Understand the structure and characteristics of the dataset.
- Identify missing values and duplicate records.
- Investigate invalid values and potential outliers.
- Standardize inconsistent time formats.
- Validate order and pickup time relationships.
- Document all cleaning decisions.
- Export a cleaned dataset for further analysis.

## Dataset Information

| Description | Details |
|---|---|
| Original records | 45,584 |
| Original columns | 20 |
| Working dataset columns | 23 |
| Data type | CSV |
| Domain | Food Delivery |

## Technologies Used

- Python
- Pandas
- NumPy
- Jupyter Notebook
- VS Code
- Git and GitHub

## Data Cleaning Process

### 1. Dataset Understanding
- Inspected dataset dimensions and column names.
- Examined data types and summary statistics.
- Investigated numerical and categorical variables.

### 2. Data Quality Checks
- Checked missing values.
- Checked exact duplicate records.
- Checked duplicate order IDs.
- Investigated unusual categorical values.
- Identified potential numerical outliers.

### 3. Invalid Value Investigation
- Identified 53 ratings outside the assumed 1–5 rating range.
- Converted those invalid ratings into missing values.
- Investigated delivery partner ages below 18.
- Investigated unusual geographical coordinates.

### 4. Time Standardization
- Investigated decimal time representations.
- Standardized order and pickup times into minutes.
- Preserved next-day pickup rollover information.
- Created an order-to-pickup time interval column.

### 5. Missing Value Treatment
Missing values were retained when their actual values could not be reliably established. No rows were deleted for missing values.

### 6. Validation
- Verified that no exact duplicate rows remained.
- Confirmed that order and pickup intervals were positive for records with available order times.
- Exported the working dataset separately from the raw dataset.

## Key Findings

- Original dataset contains 45,584 records and 20 columns.
- No exact duplicate rows were identified.
- No duplicate order IDs were identified.
- 53 invalid delivery ratings were converted to missing values.
- The final missing rating count is 1,961.
- The average order-to-pickup interval is approximately 9.99 minutes.
- No negative or zero order-to-pickup intervals were identified.

## Project Structure

```text
food-delivery-data-analysis/
├── data/
│   ├── raw/
│   │   └── README.md
│   └── processed/
│       └── cleaned_food_delivery.csv
├── notebooks/
│   └── 01_data_understanding_and_cleaning.ipynb
├── docs/
│   └── cleaning_log.csv
├── README.md
└── requirements.txt
```

## How to Run

1. Clone the repository.
2. Install the required dependencies.
3. Open the Jupyter Notebook.
4. Execute the notebook cells in order.

Install dependencies:

```bash
pip install -r requirements.txt
```

## Current Project Status

Week 1: Dataset Understanding and Cleaning.

The project includes dataset inspection, data-quality investigation, time standardization, cleaning documentation, and preparation of a cleaned dataset.

## Future Scope

Further exploratory data analysis and visualization can be performed in subsequent project phases.

## Author

Gnanesh Buddabathina
