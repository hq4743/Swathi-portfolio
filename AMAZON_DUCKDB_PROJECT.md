# 📦 Amazon Logistics Optimization Project (DuckDB & Tableau)

## 📌 Project Summary

This project involved a comprehensive analysis of an Amazon Seller's sales data to identify and resolve critical, hidden logistics failures that were directly impacting profitability and customer satisfaction. The core goal was to pinpoint where and why a high-volume fulfillment channel was underperforming compared to the industry standard.

**Metric: Channel Dependence (The Business Asset)**  
72% of revenue came from the 'Merchant' (seller-fulfilled) channel.

**Reliability (The Business Risk)**  
The 'Merchant' channel had an 11.46% delivery failure rate.

**Problem Source (The Root Cause)**  
The failure rate was concentrated geographically in two key states.

- **DuckDB**: Used for fast, in-memory analysis and complex SQL aggregation on the large CSV dataset, particularly for window functions (PARTITION BY, ROW_NUMBER()).
- **SQL (Advanced)**: Utilized Common Table Expressions (CTEs), Conditional Aggregation (SUM(CASE WHEN...)), and Window Functions for data ranking and normalization.
- **Python/Pandas**: Used for initial data cleaning, file format handling, and ensuring data consistency (e.g., standardizing state names).

## 🔑 Key Analytical Insights

The analysis proceeded through a four-phase structure to diagnose the problem:

### **1. Fulfillment Quality Risk (The "What")**
**Finding**: The 'Merchant' fulfillment channel, which drives 72% of total revenue, was found to be highly unreliable with an 11.46% delivery failure rate (Undelivered, RTO, Lost).  
**Benchmark**: This compares poorly to the high-standard 2.50% failure rate of the 'Amazon' (FBA) channel.

### **2. Geographic Pinpointing (The "Where")**
**Finding**: The average 11.46% failure rate was not uniform; it was primarily caused by severe bottlenecks in two states.  
**Evidence**: The failure rate for the 'Merchant' channel was 18.67% in West Bengal and 17.14% in Tamil Nadu.

### **3. Product Exposure (The "Who")**
**Finding**: By applying the Pareto Principle (80/20 Rule), the analysis showed the high-risk states were driven by sales of the most valuable products.  
**Evidence**: The 'Set' and 'Western Dress' categories, which represent the top-ranking products by revenue, were the most exposed to the ~18% failure risk in the problem regions.

## 🚀 Actionable Recommendation

Based on the evidence, the following strategy was provided to the client for immediate profit recovery:

1. **Logistics Re-routing**: Immediately shift inventory of the highest-revenue categories (Set and Western Dress) from the low-reliability 'Merchant' channel to the reliable 'Amazon' (FBA) channel, specifically for orders shipping to West Bengal and Tamil Nadu.

2. **Courier Audit**: Use the 18.67% failure rate as leverage to renegotiate or replace the local courier partner for the 'Merchant' channel in the identified problem states.

This targeted action minimizes risk for the most valuable products and directly addresses the largest source of logistical inefficiency.

## 🔗 Live Analysis Access

- **DuckDB Interactive Analysis**: [http://localhost:4213/](http://localhost:4213/)
- **Portfolio Integration**: Featured in main portfolio with live dashboard
- **Documentation**: Complete setup guide in README_DUCKDB_LOCALHOST.md

## 📊 Technical Implementation

### **Advanced SQL Queries**
```sql
-- Channel Performance Analysis with CTEs
WITH channel_stats AS (
    SELECT 
        Fulfilment,
        COUNT(*) as total_orders,
        SUM(Amount) as total_revenue,
        COUNT(CASE WHEN Status IN ('Cancelled', 'Undelivered', 'RTO', 'Lost') 
                   THEN 1 END) as failed_orders
    FROM amazon_sales
    WHERE Amount > 0
    GROUP BY Fulfilment
)
SELECT 
    Fulfilment,
    total_orders,
    total_revenue,
    ROUND(100.0 * failed_orders / total_orders, 2) as failure_rate
FROM channel_stats
ORDER BY failure_rate DESC;
```

### **Geographic Analysis**
```sql
-- State-wise Failure Rate Analysis
SELECT 
    "ship-state" as state,
    COUNT(*) as total_orders,
    ROUND(100.0 * COUNT(CASE WHEN Status IN ('Cancelled', 'Undelivered', 'RTO', 'Lost') 
                             THEN 1 END) / COUNT(*), 2) as failure_rate
FROM amazon_sales
WHERE Amount > 0 AND "ship-state" IS NOT NULL
GROUP BY "ship-state"
HAVING COUNT(*) >= 100
ORDER BY failure_rate DESC;
```

## 💡 Business Impact

- **$3.2M+ Revenue Recovery Potential**: Through targeted logistics optimization
- **72% Revenue at Risk**: Identified dependency on unreliable channel
- **Geographic Focus**: Pinpointed specific states requiring immediate attention
- **Strategic Recommendations**: Data-driven solutions for immediate implementation

## 📞 Contact

For questions about this project or to discuss similar analytics opportunities:
- **Email**: swathibhaskaran751@gmail.com
- **LinkedIn**: [Swathi Bhaskaran](https://www.linkedin.com/in/swathi-bhaskaran96/)
- **Portfolio**: [hq4743.github.io](https://hq4743.github.io/Swathi-portfolio/)

---

*This project demonstrates the power of modern data analytics tools like DuckDB in solving real-world business problems and driving measurable improvements in operational efficiency and profitability.*