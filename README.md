# E-Commerce Data Analysis and Preprocessing

## Overview
This project focuses on the technical process of analyzing and preprocessing e-commerce datasets. The workflow includes data cleaning, feature engineering, and exploratory data analysis (EDA), leading to actionable insights about sales trends, customer behavior, and operational performance.

## Technical Workflow

### 1. Data Import and Initialization
- Utilize Python libraries such as `pandas`, `numpy`, and `matplotlib` for data manipulation and visualization.
- Import datasets:
  - `olist_orders_dataset.csv`
  - `olist_order_items_dataset.csv`
  - `olist_products_dataset.csv`
  - `olist_customers_dataset.csv`
  - `olist_order_reviews_dataset.csv`

```python
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

order = pd.read_csv("olist_orders_dataset.csv")
item = pd.read_csv("olist_order_items_dataset.csv")
product = pd.read_csv("olist_products_dataset.csv")
customer = pd.read_csv("olist_customers_dataset.csv")
review = pd.read_csv("olist_order_reviews_dataset.csv")
```

### 2. Data Cleaning
- Handle missing values by:
  - Filling null values with relevant placeholders (e.g., estimated delivery dates).
  - Dropping unnecessary columns after inspection.
- Convert timestamp columns to datetime format for time-based analysis.

```python
order['purchase_time'] = pd.to_datetime(order['order_purchase_timestamp'])
order['delivered_customer_date'].fillna(order['estimated_date'], inplace=True)
order.drop(['order_purchase_timestamp', 'order_approved_at'], axis=1, inplace=True)
```

### 3. Feature Engineering
- Merge datasets to enable comprehensive analysis.
- Create new columns such as:
  - `order_year` for annual trends.
  - `order_month` for monthly breakdowns.

```python
order_item_data = pd.merge(order, item, on="order_id")
order_item_data["order_year"] = order_item_data["purchase_time"].dt.year
order_item_data["order_month"] = order_item_data["purchase_time"].dt.month
```

### 4. Exploratory Data Analysis (EDA)
- Conduct statistical summary and distribution checks for key columns.
- Visualize sales trends:
  - Yearly and monthly revenue breakdowns.
  - Top-selling products and categories.
  - Customer review scores and sentiments.

```python
order_item_data.groupby("order_year").agg({"price": "sum"}).plot(kind="bar")
plt.title("Yearly Revenue")
plt.show()
```

### 5. Data Validation
- Validate datasets by checking for inconsistencies:
  - Shape and size of DataFrames.
  - Presence of null or duplicate entries.
- Ensure data type alignment for numerical and categorical fields.

```python
for name, df in {"Order": order, "Item": item}.items():
    print(f"{name}: Shape {df.shape}, Missing Values {df.isna().sum().sum()}")
```

## Results
- **Sales Trends**:
  - Identified peak sales months and years.
  - Established a positive trend in customer order growth.
- **Customer Behavior**:
  - Analyzed geographical and temporal order distributions.
  - Revealed patterns in product preferences and customer reviews.
- **Operational Insights**:
  - Estimated delivery times and discrepancies.
  - Identified bottlenecks in shipping timelines.

## Visualizations
Key visualizations include:
- Yearly revenue trends.
- Monthly sales performance.
- Distribution of customer review scores.
- Top-performing product categories.

## Usage
1. Clone the repository and place datasets in the `data/` folder.
2. Run the Jupyter Notebook `olist_ecom.ipynb` for data preprocessing and analysis.
3. Review the output visualizations and summary tables.

```bash
git clone https://github.com/your-repository/ecommerce-data-analysis.git
cd ecommerce-data-analysis
jupyter notebook olist_ecom.ipynb
```

## Contributing
Fork the repository and submit pull requests for improvements or new features.

## License
This project is licensed under the MIT License. See the `LICENSE` file for details.

## Acknowledgments
The datasets are part of the Olist e-commerce dataset. Thanks to the Olist team for providing such a comprehensive dataset for public analysis.

