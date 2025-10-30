--Total Amount = unit_price * transaction_qty 
SELECT product_category, store_location,
    SUM(unit_price * transaction_qty) AS total_revenue,
--Total units sold by product type or detail
   SUM( transaction_qty) AS total_units_sold,
--Grouping by 30-minute time intervals 
CASE 
     WHEN transaction_time BETWEEN '07:30:00' AND '11:59:00' THEN 'Morning'
     WHEN transaction_time BETWEEN '12:00:00' AND '16:59:00' THEN 'Afternoon'
     WHEN transaction_time >='17:00:00' THEN 'Evening'
     END AS day_time,
CASE
      WHEN SUM(unit_price* transaction_qty) > total_units_sold THEN 'high performing'
      WHEN  SUM(unit_price* transaction_qty) < total_units_sold  THEN 'low performing'
END AS performance_category,
HOUR(transaction_time) AS working_hours,
MONTHNAME(transaction_date) AS month_name
FROM bright.coffe.shop_db
GROUP BY ALL
ORDER BY total_revenue DESC;
