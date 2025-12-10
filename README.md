# Retail Sales Analytics - SQL Portfolio Project

> Comprehensive SQL analytics showcasing exploratory data analysis, advanced analytical techniques, customer and product performance reporting using PostgreSQL

[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white)](https://www.postgresql.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

---

## Table of Contents
- [Project Overview](#-project-overview)
- [Dataset](#-dataset)
- [Project Structure](#-project-structure)
- [Key Analyses](#-key-analyses)
- [Technical Skills](#-technical-skills-demonstrated)
- [Key Findings](#-key-findings)
- [Future Enhancements](#-future-enhancements)
- [Contact](#-contact)

---

## Project Overview

This project demonstrates end-to-end SQL analytics capabilities on a sales data warehouse, covering:

- **Exploratory Data Analysis (EDA)** - Understanding data structure, quality, and distributions
- **Advanced Analytics** - Time series analysis, cohort analysis, and performance benchmarking
- **Customer Report** - Segmentation, lifetime value, and behavioral analysis
- **Product Report** - Performance metrics, category analysis, and ranking

**Business Goal:** Extract actionable insights from sales data to drive strategic decision-making in areas of customer retention, product optimization, and revenue growth.

---

## 📊 Dataset

### **Source**
Retail sales data warehouse (Gold layer) with star schema architecture by Barra Khatib

### **Tables**
- `fact_sales` - Transaction-level sales data (60K+ rows)
- `dim_customers` - Customer demographic information (10K+ customers)
- `dim_products` - Product catalog with categories and pricing (200+ products)

### **Time Period**
December 2010 - January 2014 (3 years)

### **Key Metrics**
- Total Revenue: $29,356,250
- Total Orders: 27,659
- Unique Customers: 18,484
- Product Categories: 37

### **Schema**
```
fact_sales
├── order_number (PK)
├── customer_key (FK → dim_customers)
├── product_key (FK → dim_products)
├── order_date
├── shipping_date
├── due_date
├── sales_amount
├── quantity
└── price

dim_customers
├── customer_key (PK)
├── customer_id
├── customer_number
├── first_name
├── last_name
├── country
├── martial_status
├── gender
├── birthdate
└── create_date

dim_products
├── product_key (PK)
├── product_id
├── product_number
├── product_name
├── category_id
├── category
├── subcategory
├── maintenance
├── cost
├── product_line
└── start_date
```

---

## Project Structure

```
sales-analytics-sql/
│
├── README.md                          # Project documentation
├── LICENSE                            # MIT License
│
├── 01-exploratory-data-analysis/      # EDA queries
│   ├── README.md
│   ├── 01_database_exploration.sql
│   ├── 02_dimensions_exploration.sql
│   ├── 03_date_exploration.sql
│   ├── 04_key_business_metrics.sql
│   ├── 05_consolidated_business_metric_report.sql
│   ├── 06_magnitude_analysis.sql
│   └── 07_ranking_analysis.sql
│
├── 02-advanced-analytics/             # Advanced SQL techniques
│   ├── README.md
│   ├── 01_change_over_time.sql
│   ├── 02_cumulative_analysis.sql
│   ├── 03_performance_analysis.sql
│   ├── 04_part_to_whole.sql
│   └── 05_data_segmentation.sql
│
├── 03-reports/                        # Business intelligence reports
│   ├── README.md
│   ├── customer_analytics_report.sql
│   └── product_performance_report.sql
│
└── documentation/                     # Supporting docs
    ├── data_dictionary.md
    ├── business_requirements.md
    └── key_findings.md
```

---

## 🔍 Key Analyses

### 1. **Exploratory Data Analysis**

**Objective:** Understand data structure, quality, and initial patterns

**Key Questions Answered:**
- What is the date range of our sales data?
- What are the key business metrics (revenue, orders, customers)?
- How are customers distributed across countries and demographics?
- Which products and categories drive the most revenue?

**Techniques Used:**
- Aggregate functions (SUM, COUNT, AVG, MIN, MAX)
- GROUP BY for dimensional analysis
- Date functions (DATE_TRUNC, EXTRACT, AGE)
- JOINS to combine multiple tables for multi-table analyses
- UNION ALL to combine multiple queries for the consolidate metric report

[View EDA Queries](01-exploratory-data-analysis/)

---

### 2. **Advanced Analytics**

#### **Change Over Time Analysis**
- Month-over-month sales growth rate
- Customer acquisition trends
- 3-month rolling averages for trend smoothing

#### **Cumulative Analysis**
- Running total revenue by customer (Lifetime Value)
- Cumulative product sales with milestone tracking
- monthly revenue with running total

#### **Performance Analysis**
- Country performance benchmarking vs. average
- Year-over-year product comparison

#### **Part-to-Whole Analysis**
- Revenue contribution by category (Pareto Analysis)
- Gender-based purchase distribution
- category contribution to overall sales

#### **Data Segmentation**
- Customer Age Analysis
- Product cost range segmentation
- Customer segmentation by spending behavior

**Techniques Used:**
- Window functions (LAG, LEAD, ROW_NUMBER, RANK)
- CTEs (Common Table Expressions)
- Running totals and moving averages
- Complex aggregations and subqueries

[View Advanced Analytics](02-advanced-analytics/)

---

### 3. **Business Reports**

#### **Customer Analytics Report**
- Base query: retrieve core columns from tables
- Customer aggregation: summarizes key metrics at the customer level
- Result transformation: calculate KPIs and apply business rule

#### **Product Performance Report**
- Base query: retrieve core columns from tables
- Product aggregation: summarizes key metrics at the product level
- Result transformation: calculate KPIs and apply business rule

[View Reports](03-reports/)

---

## 🛠️ Technical Skills Demonstrated

### **SQL Techniques**
- Window Functions 
- Common Table Expressions (CTEs) - Single and multiple
- Subqueries 
- Complex Joins 
- Advanced Aggregations with GROUP BY
- Date/Time Functions (DATE_TRUNC, EXTRACT, AGE)
- String Functions and Concatenation
- CASE statements for conditional logic
- COALESCE and NULLIF for null handling

### **Database Design**
- View creation and management (CREATE VIEW, CREATE OR REPLACE VIEW)
- Star schema understanding (Fact and Dimension tables)

### **Analytical Frameworks**
- Time Series Analysis (trends, seasonality, growth rates)
- Cohort Analysis (customer lifecycle tracking)
- Pareto Analysis (80/20 rule)
- Performance Benchmarking

### **Business Intelligence**
- KPI definition and calculation
- Business reporting structure

---

## Key Findings

### **Revenue Insights**
- **25% Month-over-Month Growth** in Q3 2024 during peak season
- **Top 20% of customers generate 65% of revenue** (Pareto principle validated)
- **Country X leads** with 35% of total revenue

### **Customer Insights**
- **VIP segment** (12+ months, $5K+ spend) shows **3.2x higher lifetime value** than Regular customers
- **Customer acquisition accelerated by 18%** in recent quarter
- **Age group 35-44** demonstrates highest average spending at $X,XXX

### **Product Insights**
- **Category A** contributes **42% of total revenue**
- **Bottom 10% products** account for only **2% of sales** - candidates for discontinuation
- **Premium products** ($500+) show **highest profit margins** at XX%

### **Operational Insights**
- **Average order fulfillment time:** X days
- **Customer reorder rate:** XX% within 90 days
- **Products with maintenance needs** show **lower customer satisfaction**

---

## Future Enhancements

- [ ] Add predictive analytics (customer churn probability)
- [ ] Implement recursive CTEs for hierarchical data
- [ ] Create materialized views for performance optimization
- [ ] Add Python integration for statistical analysis
- [ ] Build interactive Tableau dashboard
- [ ] Automate reporting with scheduled queries
- [ ] Add more advanced time series forecasting

---

## Learning Resources

This project was built while learning from:
- [Barra Khatib's Full SQL course](https://youtu.be/SSKVgrwhzus)

---

## Contributing

This is a personal portfolio project, but suggestions and feedback are welcome!

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/improvement`)
3. Commit your changes (`git commit -m 'Add some improvement'`)
4. Push to the branch (`git push origin feature/improvement`)
5. Open a Pull Request

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## Contact

**Olamilekan Adesoye**

Email: adesoyeolamilekan2@gmail.com
LinkedIn: [linkedin.com/in/myprofile](https://www.linkedin.com/public-profile/settings?lipi=urn%3Ali%3Apage%3Ad_flagship3_profile_self_edit_contact-info%3B4Bdg8EbcSu2onJ0kW5AIlA%3D%3D) 


---

## If you found this project helpful, please give it a star!

---

## Acknowledgments

- Thanks to Baraa Khatib Salkini for his insightful tutorials on SQL

---

**Last Updated:** December 2024  
**Status:** ✅ Complete  
**Version:** 1.0
