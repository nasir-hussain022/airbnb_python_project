# Airbnb Data Cleaning and Analysis (Python/Pandas)

This repository contains a comprehensive data cleaning and exploratory data analysis (EDA) project using a dataset of Airbnb listings. The project focuses on preparing raw, messy data for analysis and extracting initial geographical pricing insights.

## Table of Contents
* [Project Overview](#project-overview)
* [Dataset Description](#dataset-description)
* [Technical Workflow](#technical-workflow)
* [Data Cleaning Steps](#data-cleaning-steps)
* [Key Findings](#key-findings)
* [Tools Used](#tools-used)

## Project Overview
The objective of this project is to demonstrate professional data cleaning techniques in Python. This includes handling missing values, inspecting data distributions, and performing grouped aggregations to understand price variations across different New York City neighborhood groups.

## Dataset Description
The raw dataset (`airbnb.csv`) consists of **20,770 entries** and **22 columns**. It provides a detailed snapshot of listings, including:
* **Identification:** `id`, `name`, `host_id`, `host_name`.
* **Geographical Data:** `neighbourhood_group`, `neighbourhood`, `latitude`, `longitude`.
* **Listing Specifics:** `room_type`, `price`, `minimum_nights`, `availability_365`.
* **Feedback & Metrics:** `number_of_reviews`, `rating`, `reviews_per_month`.
* **Property Details:** `bedrooms`, `beds`, `baths`.

## Technical Workflow
1. **Initial Inspection:** Used `df.info()`, `df.head()`, and `df.tail()` to understand data types and structure.
2. **Statistical Profiling:** Leveraged `df.describe()` to identify outliers and price ranges (e.g., maximum price reached 100,000.0).
3. **Null Value Identification:** Mapped missing values across the dataset, discovering specific gaps in columns like `price` (34 nulls) and `neighbourhood` (7 nulls).
4. **Data Refinement:** Systematically removed null values to ensure the integrity of subsequent calculations.
5. **Aggregation:** Grouped the data by `neighbourhood_group` to compare minimum listing prices.
6. **Persistence:** Exported the final cleaned dataset as `airbnb_processed.csv` for further reporting.

## Data Cleaning Steps
Prior to cleaning, the dataset had several inconsistencies. The cleaning process involved:
* **Handling Missing Data:** Identified that 11 different columns had missing values.
* **Standardizing Records:** Removed incomplete rows to provide a reliable foundation for statistical summaries.
* **Shape Transformation:** Refined the data from its original 20,770 rows to a cleaner subset.

## Key Findings
The analysis revealed significant differences in the entry-level pricing (minimum price) across different neighborhood groups:
| Neighbourhood Group | Minimum Price |
| :--- | :--- |
| **Brooklyn** | 10.0 |
| **Manhattan** | 10.0 |
| **Queens** | 17.0 |
| **Bronx** | 24.0 |
| **Staten Island** | 33.0 |
*(Prices sorted in ascending order)*.

## Tools Used
* **Python 3.x**
* **Pandas:** Used for data manipulation and cleaning.
* **Jupyter Notebook:** Environment for interactive development.
