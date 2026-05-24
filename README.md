# Online Store Database System

## Project Overview
This project is a SQL-based relational database system designed for an Online Store. The database manages customers, products, orders, payments, and shipping addresses while following proper normalization principles to improve data integrity and reduce redundancy.

The project demonstrates database design, ER modeling, normalization, SQL querying, and real-world business problem solving.

---

## Features
- Customer Management
- Product Inventory Management
- Order Processing System
- Payment Tracking
- Multiple Shipping Addresses
- Business Analytics Queries
- Normalized Database Design (1NF, 2NF, 3NF)

---

## Database Design
The database was designed using normalization techniques:

### First Normal Form (1NF)
- Removed repeating product groups
- Ensured atomic values

### Second Normal Form (2NF)
- Removed partial dependencies
- Created separate product-related tables

### Third Normal Form (3NF)
- Eliminated transitive dependencies
- Separated customer, payment, and address information

---

## Technologies Used
- SQL
- SQLite
- Database Normalization
- ER Diagrams

---

## Database Tables
- Customers
- Addresses
- Products
- Orders
- Order_Items
- Payments

---

## Business Use Cases
The project includes SQL queries for solving business problems such as:

1. Customer purchase history
2. Average customer spending per order
3. Top-selling products by revenue
4. Pending and unpaid orders analysis

---

## Example SQL Query
```sql
SELECT 
    p.product_id,
    p.name AS product_name,
    SUM(oi.quantity) AS total_units_sold,
    SUM(oi.quantity * oi.unit_price) AS total_revenue
FROM Products p
JOIN Order_Items oi ON oi.product_id = p.product_id
JOIN Orders o ON o.order_id = oi.order_id
WHERE o.status <> 'Cancelled'
GROUP BY p.product_id, product_name
ORDER BY total_revenue DESC;
