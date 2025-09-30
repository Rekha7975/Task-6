-- Create database
CREATE DATABASE online_sales;

-- Orders table
CREATE TABLE orders (
    order_id     INT,
    order_date   DATE,
    product_id   INT,
    amount       DECIMAL(10,2)
);

INSERT INTO orders (order_id, order_date, product_id, amount) VALUES
(1, '2024-01-15', 101, 250.00),
(2, '2024-01-20', 102, 500.00),
(3, '2024-02-05', 103, 120.00),
(4, '2024-02-17', 104, 450.00),
(5, '2024-02-20', 101, 300.00),
(6, '2024-03-01', 105, 700.00),
(7, '2024-03-12', 106, 150.00),
(8, '2024-03-20', 102, 400.00),
(9, '2024-03-25', 107, 600.00),
(10, '2024-04-02', 108, 1000.00);

SELECT 
    EXTRACT(YEAR FROM order_date) AS year,
    EXTRACT(MONTH FROM order_date) AS month,
    SUM(amount) AS total_revenue,
    COUNT(DISTINCT order_id) AS total_orders
FROM orders
GROUP BY year, month
ORDER BY year, month;

SELECT 
    YEAR(order_date) AS year,
    MONTH(order_date) AS month,
    SUM(amount) AS total_revenue,
    COUNT(DISTINCT order_id) AS total_orders
FROM orders
GROUP BY year, month
ORDER BY year, month;

SELECT 
    strftime('%Y', order_date) AS year,
    strftime('%m', order_date) AS month,
    SUM(amount) AS total_revenue,
    COUNT(DISTINCT order_id) AS total_orders
FROM orders
GROUP BY year, month
ORDER BY year, month;

