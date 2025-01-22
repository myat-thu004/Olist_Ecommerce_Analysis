# E-Commerce Data Analysis and Preprocessing

## Overview
This project focuses on the technical process of analyzing and preprocessing e-commerce datasets. The workflow includes data cleaning, feature engineering, exploratory data analysis (EDA), and clustering techniques to uncover insights into sales trends, customer behavior, and operational performance.

## Key Technical Processes

### Data Preparation
1. **Data Discovery**:
   - Used the Brazilian E-Commerce Public Dataset (2016-2018) from Kaggle.
   - Integrated multiple datasets including orders, items, customers, products, and reviews.

2. **Data Profiling**:
   - Identified missing values, feature distributions, and data types.
   - Key findings:
     - Orders dataset had ~0.8% missing values in date-related columns.
     - Reviews dataset had ~36% missing text data.
     - Payment and geolocation datasets had no missing values.

3. **Data Cleaning**:
   - Handled missing values by imputation or removal.
   - Standardized timestamps for time-based analysis.
   - Merged datasets for comprehensive analysis using keys like `order_id` and `customer_id`.

### Analysis and Modeling
1. **Exploratory Data Analysis (EDA)**:
   - Analyzed revenue trends:
     - Revenue increased significantly between 2016 and 2018.
     - Peak sales occurred during Black Friday (November 24, 2017).
   - Customer behavior:
     - Most customers and sellers were concentrated in São Paulo.
     - High satisfaction reflected in average review scores (mean: 4.09).

2. **Clustering**:
   - Grouped sales data into clusters based on total sales, quantity, and shipping costs.
     - Cluster C1: Small sales and low shipping costs.
     - Cluster C2: High sales with minimal shipping costs.
     - Cluster C3: Small sales but high shipping costs (large items).

3. **Linear Regression**:
   - Built a model to predict total revenue based on review scores.
   - Model explained ~65% of revenue variability, suggesting other influencing factors.

4. **Product Analysis**:
   - Categorized products by price range and identified top-performing categories:
     - Budget (<40): Home Appliances, Entertainment.
     - Mid-range (40-135): Fashion, Food, Electronics.
     - Premium (>135): Furniture, Telecommunication.

## Key Insights and Recommendations
1. **Revenue Trends**:
   - Highest sales volumes in November, driven by Black Friday.
   - Need to prepare for peak sales with improved server capacity and shipping efficiency.

2. **Customer Segmentation**:
   - Customers in São Paulo are the primary revenue contributors.
   - Focus on loyalty programs and personalized marketing for this region.

3. **Product Strategy**:
   - Offer discounts and promotions for budget-friendly categories.
   - Use loyalty programs for mid-range products.
   - Premium products can benefit from personalized services and warranties.

4. **Operational Efficiency**:
   - Address delivery delays, especially orders exceeding a 10-day delay.
   - Optimize shipping logistics for high-cost clusters.

## Usage
1. Clone the repository and place datasets in the `data/` folder.
2. Run the Jupyter Notebook `olist_ecom.ipynb` for data preprocessing and analysis.
3. Review the output visualizations and summary tables.

```bash
git clone https://github.com/your-repository/ecommerce-data-analysis.git
cd ecommerce-data-analysis
jupyter notebook olist_ecom.ipynb
```

## Acknowledgments
The datasets are part of the Olist e-commerce dataset. Thanks to the Olist team for providing such a comprehensive dataset for public analysis.

