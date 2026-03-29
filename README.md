# Airbnb Data Cleaning and Analysis (Python/Pandas)

This repository contains a comprehensive data cleaning and exploratory data analysis (EDA) project using a dataset of Airbnb listings. The project focuses on preparing raw, messy data for analysis and extracting initial geographical pricing insights.

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

### 1. Initial Data Inspection
The first step involves loading the data and understanding its structure, dimensions, and statistical distribution.

```python
import pandas as pd

# Load the dataset
df = pd.read_csv("airbnb.csv")

# View structure
df.head()
df.tail()

# Check dataset dimensions
print(f"Rows: {df.shape[0]} , Columns: {df.shape[1]}")

# Profile data types and null counts
df.info()

# Statistical summary of numerical columns
df.describe()
```

## Data Cleaning Steps
Prior to cleaning, the dataset had several inconsistencies. The cleaning process involved:
* **Handling Missing Data:** Identified that 11 different columns had missing values.
* **Standardizing Records:** Removed incomplete rows to provide a reliable foundation for statistical summaries.
* **Shape Transformation:** Refined the data from its original 20,770 rows to a cleaner subset.

```python
# Identify missing values
df.isnull().sum()

# Identify and check for duplicate records
df.duplicated().sum()

# Convert ID columns to object type to prevent mathematical operations
df['id'] = df['id'].astype(object)
df['host_id'] = df['host_id'].astype(object)

# Standardize date format
df['last_review'] = pd.to_datetime(df['last_review'], errors='coerce')

# Drop rows with critical missing information
df.dropna(inplace=True)
```
## Exploratory Data Analysis (EDA)

```python
# Distribution of room types
df['room_type'].value_counts()

# Feature Engineering: Calculate minimum revenue
df['min_revenue'] = df['price'] * df['minimum_nights']

# Compare average price and minimum nights by room type
df.groupby('room_type').agg(
    avg_price=('price', 'mean'), 
    avg_min_nights=('minimum_nights', 'mean')
)

# Identify minimum entry price by neighbourhood group
df.groupby('neighbourhood_group')['price'].min().sort_values(ascending=True)

# Export the final cleaned dataset
df.to_csv('airbnb_processed.csv', index=False)
```

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

## Let's connect on 
- **Instagram**: [Follow me on instagram for daily tips](https://www.instagram.com/bca_wale022/)
- **LinkedIn**: [Connect with me on linkedIn](https://www.linkedin.com/in/nasir-hussain022)
- **Contact**: [Send me an email](mailto:nasirhussainnk172@gmail.com)
