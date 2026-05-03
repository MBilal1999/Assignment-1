

Question 1 — SELECT & WHERE
SQL
SELECT first_name, last_name, city, phone
FROM sales.customers
WHERE state = 'CA'
  AND phone IS NOT NULL;


Question 2 — ORDER BY (Multiple Columns)
SQL
SELECT product_id, product_name, model_year, list_price
FROM production.products
ORDER BY model_year DESC, list_price ASC;

 
 Question 3 — TOP N & TOP PERCENT
🔹 Part a
SQL
SELECT TOP 5 product_name, list_price
FROM production.products
ORDER BY list_price DESC;
🔹 Part b
SQL
SELECT TOP 5 PERCENT *
FROM production.products
ORDER BY list_price ASC;

-- Row count depends on total rows
-- Example: If total rows = 100 → returns 5 rows
-- Example: If total rows = 200 → returns 10 rows

Question 4 — OFFSET & FETCH (Pagination)
🔹 Page 1 (Rows 1–10)
SQL
SELECT product_id, product_name, list_price
FROM production.products
ORDER BY list_price DESC
OFFSET 0 ROWS FETCH NEXT 10 ROWS ONLY;
🔹 Page 2 (Rows 11–20)
SQL
SELECT product_id, product_name, list_price
FROM production.products
ORDER BY list_price DESC
OFFSET 10 ROWS FETCH NEXT 10 ROWS ONLY;
🔹 Page 3 (Rows 21–30)
SQL
SELECT product_id, product_name, list_price
FROM production.products
ORDER BY list_price DESC
OFFSET 20 ROWS FETCH NEXT 10 ROWS ONLY;

 
 Question 5 — DISTINCT
🔹 Part a
SQL
SELECT DISTINCT state
FROM sales.customers
ORDER BY state ASC;
🔹 Part b
SQL
SELECT DISTINCT state, city
FROM sales.customers
ORDER BY state ASC, city ASC;
🔹 Part c
SQL
SELECT COUNT(DISTINCT model_year) AS total_model_years
FROM production.products;

Question 6 — Logical Operators (AND / OR)
SQL
SELECT product_id, product_name, brand_id, category_id, list_price
FROM production.products
WHERE list_price BETWEEN 500 AND 1500
  AND (model_year = 2019 OR model_year = 2020)
ORDER BY list_price ASC;
