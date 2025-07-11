# Demand Forecasting by Product and Store Tier

To analyze sales performance, pricing strategy, promotional effectiveness, and store-wise variation across 5 FMCG product categories.
This project focuses on demand forecasting, price sensitivity modeling, and retail merchandising strategies

## Dataset Overview
**Dataset**: Breakfast at the Frat (524,950 rows across 156 weeks)
- **Transactions File**: 524,950 records of weekly store-product sales, including units, spend, visits, price, base price, and promotional flags.
- **Product Lookup**: Contains metadata like product description, brand, category, and size.
- **Store Lookup**: Includes store size, location, and segmentation into Value, Mainstream, and Upscale tiers.

---

## Data Cleaning Steps (Python)

1. **Standardized Columns & Date Format**
2. **Imputed Missing Values**
   - `units`: Recalculated based on `visits` and `hhs`
   - `base_price`: Derived using TPR logic and group-wise medians
   - `price`: Filled based on `base_price` or average historical prices
3. **Derived Metrics**
   - `discount_pct`, `units_per_visit`, `visits_per_hhs`
4. **Outlier Tagging**
   - Based on 95th percentile thresholds for:
     - `units_per_visit` (> 1.50)
     - `visits_per_hhs` (> 1.10)
5. **Final Checks**
   - Ensured all fields were consistent, and nulls were appropriately handled

---

## Exploratory Data Analysis (EDA)

### Category-Level Analysis
- Total spend and units per category
- Average prices and discount rates
- Sales distribution by store tier

### Store Segment Performance
- Matrix of `Category x Store Tier` sales
- Identification of category dominance by tier

### Brand Performance
- Top brands by total spend
- Discount dependency per brand (scatter analysis)

### Time Series Trends
- Weekly sales trends (Units & Spend)
- Overlay of outlier spikes for anomaly detection

---

## Output Files for Power BI

- `category_sales.csv`
- `category_discounts.csv`
- `category_summary.csv`
- `top_brands_sales.csv`
- `brand_discounts.csv`
- `brand_discount_summary.csv`
- `category_store_tier_matrix.csv`
- `weekly_sales.csv`
- `sales_outliers.csv`


<img width="1911" height="1100" alt="EDA DASHBOARD" src="https://github.com/user-attachments/assets/7e1edf47-f315-41ca-8f76-541a481cf34e" />
