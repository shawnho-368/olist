# Olist E-Commerce Customer Retention Analysis

## Project Overview
This project analyzes customer retention patterns in the Olist Brazilian e-commerce marketplace, investigating what differentiates customers who make repeat purchases from those who don't. The analysis examines operational metrics, order characteristics, product preferences, and geographic patterns across approximately 96,000 customers and 100,000 orders spanning September 2016 to August 2018.

**Key Finding:** The dataset reveals an exceptionally low retention rate of 1.87%, with retained customers showing remarkably similar characteristics to churned customers across nearly all dimensions analyzed—suggesting that retention drivers in this marketplace are influenced by factors beyond the transactional data available.

## Business Question
**What factors drive customers to make repeat purchases, and what characteristics distinguish one-time buyers from repeat customers?**

## Dataset
**Source:** [Olist Brazilian E-Commerce Public Dataset](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) via Kaggle

**Time Period:** September 2016 - August 2018

**Key Tables:**
- Orders: Order information, status, and timestamps
- Customers: Customer location and unique identifiers  
- Order Items: Products purchased with pricing
- Products: Product categories and attributes
- Reviews: Customer satisfaction scores
- Payments: Payment methods and values
- Sellers: Seller location and information

## Methodology

### Defining Retention
Retention is defined as **making a second purchase within 180 days of the first purchase**. This window was chosen based on analysis of actual repeat purchase timing, capturing approximately 75% of repeat purchase behavior while maintaining sufficient sample size.

### Eligible Customer Cohort
To ensure fair measurement, only customers whose first purchase occurred at least 180 days before the dataset end date were included in the analysis. This ensures all customers had equal opportunity to demonstrate retention.

**Key Data Structure Note:**
- `customer_unique_id`: The actual unique person identifier
- `customer_id`: Order/address-specific identifier  

The same person can have multiple `customer_id` values but maintains one `customer_unique_id`. Proper handling of this distinction is crucial for accurate retention measurement.

### Analysis Dimensions
The analysis systematically examines:
1. **Operational Metrics**: Order approval time, carrier handoff time, delivery speed, delivery accuracy
2. **Customer Satisfaction**: Review scores and ratings
3. **Order Characteristics**: Order value, basket size, item quantity
4. **Product Preferences**: Product categories, price points
5. **Geographic Patterns**: State and city-level retention variations

## Key Findings

### 1. Exceptionally Low Retention (1.87%)
Of 68,940 eligible customers, only 1,292 (1.87%) made a repeat purchase within 180 days—far below typical e-commerce benchmarks of 20-40%.

### 2. Minimal Operational Differentiation
Retained and churned customers experienced nearly identical:
- Median order approval times (~140 minutes)
- Time to carrier delivery (~3 days)
- Delivery times to customer (~12 days)
- Delivery accuracy (estimates vs actual)
- Customer satisfaction scores (~4.0 stars)

### 3. Similar Order & Product Patterns
Both segments showed:
- Comparable median order values (~R$ 100)
- Similar basket sizes and item quantities
- Overlapping product category preferences (bed_bath_table, health_beauty, sports_leisure)

### 4. Limited Geographic Variation
While some state-level differences exist, all regions exhibited low retention relative to industry standards.

## Business Implications

The lack of clear differentiating factors in transactional data suggests retention in this marketplace is likely driven by:

1. **Specific Product Needs**: Customers may use Olist for one-time or infrequent purchases rather than regular shopping
2. **Competitive Dynamics**: High competition in Brazilian e-commerce may prevent platform loyalty
3. **Marketplace Structure**: As an aggregator rather than direct retailer, Olist may face brand loyalty challenges
4. **Unmeasured Factors**: Important drivers like marketing engagement, loyalty programs, and customer service quality aren't captured in transactional data

## Recommendations

1. **Develop Loyalty Programs**: Create incentives beyond competitive pricing to encourage repeat purchases
2. **Category-Specific Strategies**: Focus on categories with recurring purchase patterns (health_beauty, pet_shop)
3. **Post-Purchase Engagement**: Implement targeted email campaigns and personalized recommendations
4. **First Purchase Experience**: Build emotional connections and memorable brand experiences
5. **Seller Quality Programs**: Ensure consistently high seller performance to build marketplace trust

## Technical Implementation

### Technologies Used
- **Python 3.9+**
- **Pandas**: Data manipulation and analysis
- **Matplotlib & Seaborn**: Data visualization
- **Jupyter Notebook**: Interactive analysis environment

### Project Structure
```
olist-retention-analysis/
├── data/                                      # Raw data files (not included in repo)
│   ├── olist_customers_dataset.csv
│   ├── olist_orders_dataset.csv
│   ├── olist_order_items_dataset.csv
│   ├── olist_products_dataset.csv
│   ├── olist_order_reviews_dataset.csv
│   ├── olist_order_payments_dataset.csv
│   ├── olist_sellers_dataset.csv
│   └── product_category_name_translation.csv
├── olist_retention_analysis.ipynb            # Main analysis notebook
├── README.md                                  # Project documentation
├── .gitignore                                 # Git ignore file
└── requirements.txt                           # Python dependencies
```

### Setup Instructions

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/olist-retention-analysis.git
   cd olist-retention-analysis
   ```

2. **Download the dataset**
   - Download the [Olist dataset from Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)
   - Extract all CSV files to the `data/` directory

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Run the analysis**
   ```bash
   jupyter notebook olist_retention_analysis.ipynb
   ```

## Limitations

1. **Data Scope**: Analysis limited to transactional data; lacks marketing engagement, customer service interactions, and competitive behavior
2. **Time Period**: Dataset spans only 2 years; longer timeframes might reveal different patterns  
3. **Market Context**: Missing context on Olist's market position and competitive landscape during this period
4. **Causation**: Analysis identifies patterns but cannot definitively establish causal relationships

## Acknowledgments
- Dataset provided by Olist via Kaggle
- Analysis inspired by common e-commerce retention challenges and best practices

## License
This project is licensed under the MIT License - see the LICENSE file for details.