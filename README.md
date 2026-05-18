# SQL-Analysis-of-Apex-Global-Warehouse-Quarterly-Inventory-Review-

# Project Overview
As a Junior Data Analyst at Apex Global Warehouse, I executed a strategic Quarterly Inventory Review designed to provide the CEO with actionable intelligence on the distribution center's high-value product lines and stalled inventory. The primary objective was to distinguish between "Premium" assets designated for promotion and "Budget" stock targeted for liquidation. This analysis serves as the data-driven foundation for optimizing warehouse turnover and protecting profit margins across multiple product tiers.
# Data Challenges & Constraints
The amazon_products dataset contained several technical hurdles that required rigorous SQL-based remediation to maintain the integrity of the executive report:
Data Corruption: A synchronization error caused several customer ratings to be overwritten by pipe characters ('|'), which threatened to break numerical aggregation models.
String Complexity: Product classifications were stored as concatenated strings (e.g., Electronics|HomeAudio|Accessories), necessitating the use of pattern matching to isolate specific revenue-driving categories.
Data Volume: With thousands of rows of inventory data, manual auditing was impossible, requiring a programmatic approach to identify outliers and trends.
Data Integrity: Critical fields such as rating_count contained missing values (NULL). An exhaustive audit was required to ensure the CEO did not base promotional strategies on incomplete or skewed popularity metrics.
Technical Stack & Methodology
The analysis was conducted within the Google BigQuery environment to leverage its high-performance processing capabilities for large datasets.
# SQL Implementation
The technical workflow utilized a sophisticated array of SQL commands, including: SELECT, AS (Aliasing), WHERE, HAVING, GROUP BY, ORDER BY (specifically for sorting high-savings items), CASE WHEN, LIKE, and IS NULL.
# Key Technical Solutions
Cleaning Corrupted Data: Implemented CASE WHEN logic to intercept the corrupted '|' rating values and transform them into a standardized numerical value of 0.0, preserving the dataset's computational viability.
Pattern Matching: Employed the LIKE operator with wildcards (%) to parse complex category strings, allowing for precise filtering of product lines like "Electronics" within a single string.
Integrity Auditing: Used IS NULL to isolate products with missing stock and rating metadata. Identifying these gaps prevented the inclusion of incomplete data in high-stakes executive summaries.
Prioritization Logic: Utilized ORDER BY in conjunction with calculated fields to rank inventory by the most significant discount opportunities, ensuring the highest-impact items were addressed first.
# Strategic Business Insights
This analysis transformed raw data into a cohesive inventory strategy through the following insights:
Inventory Value & Pricing Brackets: I segmented the warehouse into three distinct tiers: Budget (<500), Mid-Range (500–2,000), and Premium (>2,000). This classification enabled high-velocity liquidation strategies for Budget items while protecting the margins of Premium luxury stock.
Discount & Savings Impact: By identifying high-value items where the actual_price exceeded 5,000 and calculating total_savings (actual_price minus discounted_price), I isolated the most effective discount strategies. Sorting these by the largest savings allowed management to prioritize products with the highest consumer incentive.
Category Performance & Competitiveness: Using GROUP BY and HAVING clauses, I filtered the warehouse data to identify top-performing categories. This required filtering aggregated data for an average rating above 4.0 and an inventory density greater than 5 products, effectively separating high-performing niche categories from underperforming ones.
Premium Promotion Strategy (Customer Favorites): I isolated "Customer Favorites"—items boasting a rating above 4.5 and a rating_count exceeding 10,000. These high-volume, high-reputation products were flagged for immediate "Premium" promotion to maximize quarterly revenue.
# Repository Structure
amazon.csv: The raw data source containing product, pricing, and rating schema.
inventory_analysis.sql: The complete repository of SQL scripts, including logic for data cleaning, pricing segmentation, and competitive category auditing.
