# New_Hackathon_Solution-
## Team :
Nirmal Pandey ,
Parth Patkar ,
Balraj Singh Shekhawat ,
Shivam Srinath

This project follows a real-world retail analytics pipeline where we start with corrupted/raw data, clean it based on business and data quality rules, and then use it to generate insights and machine learning predictions.

The workflow consists of the following steps:

We began with a retail dataset containing multiple related tables, including:

- Stores 
- Products 
- Customers 
- Sales header and line items 
- Promotions 
- Loyalty rules 

The dataset intentionally included data corruption to simulate real business data issues.


Examples of corruption:

Type	Example
- Missing values	: Emails, phone numbers, loyalty points 
- Duplicates : 	Customer IDs repeated 
- Bad formatting :	Dates in different formats, mixed-case text 
- Outliers : 	Negative stock, quantity = 500, price > ₹100K 
- Broken relationships : 	Sales linked to non-existing customers/products


## Data Cleaning Pipeline

We built a cleaning workflow to process the corrupted dataset step-by-step:

-- Standardized Formatting

Converted dates into consistent format

Normalized text cases (e.g., "gOlD" → "gold")

--  Handled Missing Values

Imputed missing values or marked as "unknown" where appropriate.

-- Removed or Flagged Invalid Records

Separated invalid foreign keys and extreme outliers into a bad data quarantine table.

--  Deduplication

Removed/merged duplicate customers and transactions.

--  Validation Against Rules

We applied data quality checks such as:

Valid phone number format

Non-negative stock and quantity

Correct loyalty tier mapping

At the end of this stage, we had:

🔹 A clean and usable dataset

## Solving Business Problem #1 — Inventory vs Sales Analysis

- Once we had clean data, we analyzed how inventory levels relate to product sales to discover:

Over-stocked items

High-demand items needing replenishment

Location-based product performance differences

- We calculated a key metric:

```
Stock-to-Sales Ratio = Total Units Sold / Current Stock Level
```

-- Interpretation
SSR Value  	
- High (>1)	 : Sales > Stock	: Customer demand is higher than stock available → risk of stockout
- Moderate (0.3–1)	: Balanced	: Stock aligns well with sales → good store planning
- Low (<0.3)	: Stock > Sales	: Overstock → inventory is not aligned with customer buying behavior


## Solving Business Problem #2 — Predicting Future Customer Spend

Next, we built a predictive model to estimate how much a customer might spend in the next period based on:

- Last year’s spend
- Purchase frequency
- Average order value
- Recency (days since last purchase)
- Loyalty tier

We used a Random Forest Regressor and saved it as a .pkl file so it can be reused without retraining.


