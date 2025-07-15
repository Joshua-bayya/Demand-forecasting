# Demand Forecasting by Product and Store Tier

To analyze sales performance, pricing strategy, promotional effectiveness, and store-wise variation across 5 FMCG product categories.
This project focuses on understanding how price and promotions affect demand & Predict future demand volumes

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

<img width="1911" height="1100" alt="EDA DASHBOARD" src="https://github.com/user-attachments/assets/7e1edf47-f315-41ca-8f76-541a481cf34e" />
<img width="1904" height="1095" alt="Price Elasticity   promotion Impact Dashboard (1)" src="https://github.com/user-attachments/assets/6e2f5562-71a1-45f5-b13a-31b8467f6638" />


----
Which 10 products are most price-sensitive?


<img width="577" height="265" alt="image" src="https://github.com/user-attachments/assets/fb5ed797-949c-4095-a9bb-c93672769e5f" />

---
Which products have strong promo uplift?


<img width="577" height="73" alt="image" src="https://github.com/user-attachments/assets/6813c10c-7aa2-487f-bf01-35ce6b62d558" />

---
Which Categoried products more elastic?


<img width="368" height="97" alt="image" src="https://github.com/user-attachments/assets/08091575-8e49-407c-8c7e-c0f76a469e4b" />

---
Should the company lower price or run promos?
My analysis shows that promotional tactics like Display and Feature occur more frequently among high-performing items than price discounts (TPR)
This supports a strategy of targeted promotion: choose the right promo type for the right product, rather than broadly applying discounts.Especially for products with high price elasticity and strong R² values. Discounts can be used more selectively — not as a blanket tactic.


