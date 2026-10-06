# Music Streaming Sales Analysis (SQL)

A SQL portfolio project analyzing sales, customer, and revenue data from a music streaming/store database (Chinook dataset) using MySQL.

## Overview

This project explores customer purchasing behavior, revenue trends, and employee sales performance using the **Chinook database** — a sample dataset modeled after a digital music store, containing customers, invoices, tracks, albums, artists, genres, and employees.

The goal was to answer real business questions using SQL, covering multi-table joins, aggregation, filtering, and subqueries.

## Tools Used

- **Database:** MySQL
- **Dataset:** [Chinook Database](https://github.com/lerocha/chinook-database)

## Business Questions & Key Insights

**1. Which tracks generate the most revenue?**
Identified the top 10 best-selling tracks by total revenue (price × quantity sold).

**2. Which music genres bring in the most money?**
Grouped revenue by genre to find which categories perform best commercially.

**3. Who are our most valuable customers?**
Ranked customers by total lifetime spend to identify top 5 highest-value customers.

**4. Which employee's customers generated the most revenue?**
Measured sales performance per employee based on the customers assigned to them.

**5. What percentage of customers are repeat buyers?**
Found that **100% of customers (59/59)** made more than one purchase — indicating strong retention or a recurring billing pattern in the dataset.

## Skills Demonstrated

- Multi-table JOINs (up to 4 tables)
- Aggregate functions (SUM, COUNT, AVG, MAX)
- GROUP BY and HAVING
- Subqueries (including nested subqueries)
- Writing business-oriented, readable SQL

## Files

- [`queries.sql`](./queries.sql) — All 5 queries with comments explaining each business question

## Author

**Shankar R**
[LinkedIn](https://www.linkedin.com/in/sankar-rajendran) 