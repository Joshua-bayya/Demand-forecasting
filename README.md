# Price Elasticity & Promotion Impact Analysis , Demand Forecasting by Product and Store Tier

Estimate product-level price elasticity and assess promotional impact (display, feature, TPR) on weekly sales across categories and store tiers.
To analyze sales performance, pricing strategy, promotional effectiveness, and store-wise variation across 5 FMCG product categories.

This project focuses on understanding how price and promotions affect demand & Predict future demand volumes

## Dataset Overview
**Dataset**: Breakfast at the Frat (524,950 rows across 156 weeks)
- **Transactions File**: 524,950 records of weekly store-product sales, including units, spend, visits, price, base price, and promotional flags.
- **Product Lookup**: Contains metadata like product description, brand, category, and size.
- **Store Lookup**: Includes store size, location, and segmentation into Value, Mainstream, and Upscale tiers.


Tools: Python (Pandas, Statsmodels), Power BI
---

## Data Cleaning Steps (Python)

1. **Cleaned and preprocessed 524K rows of transaction data**
2. **Addressed missing prices using logic around base price, spend, and TPR**
   - `units`: Recalculated based on `visits` and `hhs`
   - `base_price`: Derived using TPR logic and group-wise medians
   - `price`: Filled based on `base_price` or average historical prices
3. **Derived Metrics: Calculated price discount metrics and outlier flags using units_per_visit and visits_per_hhs**
   - `discount_pct`, `units_per_visit`, `visits_per_hhs`
   - Outliers based on 95th percentile thresholds for:
        - `units_per_visit` (> 1.50)
        - `visits_per_hhs` (> 1.10)
5. **Final Checks**
   - Ensured all fields were consistent, and nulls were appropriately handled
6. **Built log-log OLS regression models per UPC with sufficient variation and observations (n > 20)**
7. **Created a Power BI dashboard with filters, promo breakdowns, and elasticity distribution**

---

## Exploratory Data Analysis (EDA)

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


---
## Key Findings

1. Frozen pizza and snack categories show high price elasticity; oral hygiene products are largely inelastic
2. Circular features are the most effective promo type, especially in cereal(+80%) and oral care, while display promotions drove results in frozen pizza and snack categories.
3. Around 1 in 3 products were highly elastic (ε < -2)

## Measures

1. Protect elastic products with discounting, increase prices on inelastic products to capture margin.
