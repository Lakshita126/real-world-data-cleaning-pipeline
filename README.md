# Real-World Data Cleaning Pipeline

A reproducible data cleaning pipeline built with Python and Pandas to transform raw Global Superstore data into a clean, validated, and analysis-ready dataset.

## Overview

Real-world datasets often contain inconsistent data types, redundant columns, unusual values, and other data quality challenges. This project demonstrates how to inspect, clean, validate, and transform a public dataset while preserving legitimate business information.

The project also explores the cleaned data through visualizations and business analysis.

## Objectives

* Inspect and understand a real-world dataset.
* Identify potential data quality issues.
* Convert date columns into appropriate data types.
* Remove redundant information.
* Create useful features for analysis.
* Validate data quality after cleaning.
* Build a reusable and reproducible cleaning pipeline.
* Generate visual insights from the cleaned dataset.

## Dataset

**Dataset:** Global Superstore
**Source:** Kaggle
**Original size:** 51,290 rows and 27 columns.

The dataset contains order, customer, product, sales, profit, discount, shipping, market, and regional information.

## Tech Stack

* Python
* Pandas
* NumPy
* Matplotlib
* Google Colab
* Kaggle API

## Project Workflow

1. Load the raw dataset.
2. Inspect the structure, columns, and data types.
3. Check missing values and exact duplicate records.
4. Convert `Order Date` and `Ship Date` to datetime format.
5. Validate the sequence of order and shipping dates.
6. Create a `Shipping Days` feature.
7. Remove the redundant `记录数` column.
8. Investigate categorical consistency and numerical values.
9. Examine statistical outliers without automatically deleting potentially valid records.
10. Flag zero-sales and negative-profit records for analysis.
11. Validate the cleaned dataset.
12. Save the output as a CSV file.
13. Analyze sales, profit, discounts, and shipping performance.

## Data Quality Results

| Metric                          |                  Result |
| ------------------------------- | ----------------------: |
| Rows processed                  |                  51,290 |
| Final columns                   |                      29 |
| Missing values                  |                       0 |
| Exact duplicate rows            |                       0 |
| Invalid date sequences          |                       0 |
| Zero-sales records flagged      |                       1 |
| Negative-profit records flagged |                  12,544 |
| Minimum shipping duration       |                  0 days |
| Maximum shipping duration       |                  7 days |
| Average shipping duration       | Approximately 3.97 days |

These results reflect the dataset examined in this project. Zero missing values and duplicate rows were observed; the cleaning process does not claim that every possible data quality issue has been eliminated.

## Data Cleaning Decisions

### Date conversion

Converted order and shipping dates from text to datetime format to support date validation and time-based analysis.

### Redundant column removal

Removed `记录数`, a constant column containing the value `1` in every row.

### Shipping duration

Created `Shipping Days` by calculating the difference between shipping and order dates.

### Zero-sales records

Flagged the one record with zero sales for further review rather than deleting it automatically.

### Negative-profit records

Flagged records with negative profit. Negative profit can represent a genuine business loss and should not automatically be treated as invalid data.

### Outliers

Used the Interquartile Range (IQR) method to identify unusual numerical observations. Potential outliers were investigated rather than automatically removed.

## Analysis and Visualizations

The cleaned dataset was used for the following analyses:

* Total sales by category
* Yearly sales trends
* Profit by category
* Top 10 most profitable products
* Top 10 loss-making products
* Discount versus profit
* Average shipping duration by shipping mode
* Regional sales comparisons
* Sales versus profit relationship

These analyses demonstrate how data cleaning supports downstream business analysis.

## Reproducibility

The cleaning logic was organized into a reusable Python function:

`clean_global_superstore(file_path)`

The pipeline loads the raw data, converts dates, creates the shipping duration feature, removes the redundant column, and adds quality-control flags.

The automated output was compared with the previously validated cleaned dataset. The row count, column count, column order, and data values matched.

## Project Structure

```text
real-world-data-cleaning-pipeline/
├── README.md
├── requirements.txt
├── data/
│   └── global_superstore_pipeline_cleaned.csv
└── notebooks/
    └── Real_World_Data_Cleaning_Pipeline.ipynb
```

## How to Run

1. Clone or download this repository.

2. Install the required libraries:

   ```bash
   pip install -r requirements.txt
   ```

3. Open the notebook using Google Colab or Jupyter Notebook.

4. Obtain the original dataset from its Kaggle source.

5. Update the dataset path in the notebook if necessary.

6. Run the notebook cells in order.

If downloading through the Kaggle API, configure your Kaggle credentials securely. Do not upload `kaggle.json`, API tokens, or other secrets to GitHub.

## Output

The final pipeline-generated dataset is saved as:

`global_superstore_pipeline_cleaned.csv`

It includes the derived `Shipping Days` feature and the `Sales_Zero_Flag` and `Negative_Profit_Flag` columns.

## Key Learnings

* Data cleaning requires understanding the meaning of each field.
* Validating data types and date sequences is essential.
* Statistical outliers are not necessarily errors.
* Negative profit may represent a legitimate business outcome.
* Quality flags can preserve unusual records for further investigation.
* Reproducible pipelines make data preparation easier to repeat and maintain.

## Future Improvements

* Add automated unit tests.
* Create a configurable cleaning pipeline.
* Add structured logging and error handling.
* Generate a data quality report automatically.
* Add more advanced exploratory analysis and dashboards.

## Author

**Lakshita Sharma**

A data science project focused on practical data cleaning, validation, reproducibility, and business analysis.
