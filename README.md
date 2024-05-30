# Music Store Analysis
## Overview

This project involves analyzing a music store database using SQL queries to gain insights into various aspects of the store's operations, including sales, customer behavior, and inventory management.
## Introduction
The Music Store Analysis project aims to provide detailed insights into the operations of a music store. By leveraging SQL queries, we can extract meaningful information regarding sales performance, customer preferences, and inventory status. This analysis can help in making data-driven decisions to improve the store's operations and profitability.

## Dataset
The dataset used for this analysis includes various tables that store information about customers, invoices, tracks, albums, artists, and more. The main tables include:

### album
### album2
### artist
### customer
### employee 
### genre
### invoice
### invoice_line
### media_type
### playlist
### playlist_type
### track
# Queries
The SQL queries used in this project are designed to answer specific business questions. Here are some examples of the queries included in this project:

### Total Sales by Genre:

SELECT g.name AS genre, SUM(ii.unit_price * ii.quantity) AS total_sales
FROM invoice_items ii
JOIN tracks t ON ii.track_id = t.track_id
JOIN genres g ON t.genre_id = g.genre_id
GROUP BY g.name
ORDER BY total_sales DESC;

### Top 10 Customers by Sales:
SELECT c.first_name, c.last_name, SUM(i.total) AS total_spent
FROM customers c
JOIN invoices i ON c.customer_id = i.customer_id
GROUP BY c.first_name, c.last_name
ORDER BY total_spent DESC
LIMIT 10;

### Monthly Sales Trend:
SELECT strftime('%Y-%m', i.invoice_date) AS month, SUM(i.total) AS total_sales
FROM invoices i
GROUP BY month
ORDER BY month;
