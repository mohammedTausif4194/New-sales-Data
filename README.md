# New-sales-Data
Q1

SELECT 
    DATE_FORMAT(order_date, '%Y-%m') AS month,
    SUM(quantity * price) AS total_sales
FROM 
    orders
JOIN 
    order_items USING(order_id)
GROUP BY 
    DATE_FORMAT(order_date, '%Y-%m')
ORDER BY 
    total_sales DESC
LIMIT 1;

Q2
SELECT 
    city,
    SUM(quantity * price) AS total_sales
FROM 
    orders
JOIN 
    order_items USING(order_id)
GROUP BY 
    city
ORDER BY 
    total_sales DESC
LIMIT 1;

Q3
SELECT 
    HOUR(order_date) AS hour,
    COUNT(*) AS num_orders
FROM 
    orders
GROUP BY 
    HOUR(order_date)
ORDER BY 
    num_orders DESC
LIMIT 1;

Q4
SELECT 
    oi1.product_id AS product_1,
    oi2.product_id AS product_2,
    COUNT(*) AS times_sold_together
FROM 
    order_items oi1
JOIN 
    order_items oi2 
    ON oi1.order_id = oi2.order_id AND oi1.product_id < oi2.product_id
GROUP BY 
    oi1.product_id, oi2.product_id
ORDER BY 
    times_sold_together DESC
LIMIT 1;

Q5
SELECT 
    p.product_name,
    SUM(oi.quantity) AS total_quantity_sold
FROM 
    order_items oi
JOIN 
    products p ON oi.product_id = p.product_id
GROUP BY 
    p.product_name
ORDER BY 
    total_quantity_sold DESC
LIMIT 1;


