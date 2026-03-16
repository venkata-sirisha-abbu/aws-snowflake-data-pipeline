
---

## Data Pipeline Workflow

### Step 1 – Data Ingestion
Raw sales data is stored in CSV format.

### Step 2 – Data Transformation
Python is used to clean and transform the dataset.

Tasks performed:
- Convert date columns
- Calculate total sales
- Remove missing values
- Export cleaned dataset

### Step 3 – Data Storage (AWS S3)
The cleaned dataset is uploaded to an AWS S3 bucket using the Boto3 library.

### Step 4 – Data Warehouse Loading
Snowflake external stage loads the data from AWS S3 into Snowflake tables.

### Step 5 – Data Visualization
Power BI connects to Snowflake to create interactive dashboards for sales analysis.

---

## Example Python ETL Process

```python
import pandas as pd

df = pd.read_csv("sales_data.csv")

df['order_date'] = pd.to_datetime(df['order_date'])
df['total_sales'] = df['price'] * df['quantity']

df = df.dropna()

df.to_csv("clean_sales_data.csv", index=False)
