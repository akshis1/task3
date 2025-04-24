📁 SQL Data Analysis – Products Table
🧠 Overview
This project demonstrates foundational and intermediate SQL techniques for analyzing structured data using a simulated eCommerce products table. The dataset includes product-level details such as category, description length, weight, dimensions, and photo quantity.

🗂️ Table: products

Column Name	Type	Description
product_id	VARCHAR(50)	Unique product identifier
product_category_name	VARCHAR(100)	Name of the product category
product_name_length	INT	Length of the product's name (characters)
product_description_length	INT	Length of the product description
product_photos_qty	INT	Number of product photos
product_weight_g	INT	Product weight in grams
product_length_cm	INT	Product length in centimeters
product_height_cm	INT	Product height in centimeters
product_width_cm	INT	Product width in centimeters
🔍 SQL Queries & Their Purpose
1. Products with More Than 3 Photos
SELECT product_id, product_category_name, product_photos_qty
FROM products
WHERE product_photos_qty > 3
ORDER BY product_photos_qty DESC;
Purpose: Identify visually rich products — useful for frontend design or marketing decisions.

2. Average Weight by Category
SELECT product_category_name, AVG(product_weight_g) AS avg_weight
FROM products
GROUP BY product_category_name
ORDER BY avg_weight DESC;
Purpose: Understand category-level logistics and storage needs.

3. Categories with Above-Average Photo Counts
SELECT product_category_name
FROM products
GROUP BY product_category_name
HAVING AVG(product_photos_qty) > (
    SELECT AVG(product_photos_qty) FROM products
);
Purpose: Pinpoint which categories are more media-intensive than average.

4. View: category_summary
CREATE VIEW category_summary AS
SELECT 
    product_category_name,
    COUNT(*) AS product_count,
    AVG(product_weight_g) AS avg_weight,
    AVG(product_length_cm) AS avg_length
FROM products
GROUP BY product_category_name;
Purpose: Provide a reusable summary of key metrics by product category.

5. Index for Performance
CREATE INDEX idx_category ON products(product_category_name);
Purpose: Improve query performance on category-based filters and aggregations.

📌 Outcome
Learned to apply SQL operations including SELECT, GROUP BY, HAVING, ORDER BY, and subqueries.

