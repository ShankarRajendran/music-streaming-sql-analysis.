-- ============================================================
-- Music Streaming Sales Analysis (Chinook Database)
-- Author: Shankar R
-- Database: MySQL
-- ============================================================


-- ------------------------------------------------------------
-- Query 1: Top 10 best-selling tracks by revenue
-- Business question: Which tracks generate the most revenue?
-- ------------------------------------------------------------
SELECT t.Name, SUM(il.UnitPrice * il.Quantity) AS revenue
FROM InvoiceLine il
JOIN Track t ON il.TrackId = t.TrackId
GROUP BY t.Name
ORDER BY revenue DESC
LIMIT 10;


-- ------------------------------------------------------------
-- Query 2: Revenue by genre
-- Business question: Which music genres bring in the most money?
-- ------------------------------------------------------------
SELECT g.Name, SUM(il.UnitPrice * il.Quantity) AS revenue
FROM Track t
JOIN Genre g ON t.GenreId = g.GenreId
JOIN InvoiceLine il ON t.TrackId = il.TrackId
GROUP BY g.Name
ORDER BY revenue DESC;


-- ------------------------------------------------------------
-- Query 3: Top 5 customers by total spend
-- Business question: Who are our most valuable customers?
-- ------------------------------------------------------------
SELECT c.FirstName, c.LastName, SUM(inv.Total) AS total_spend
FROM Customer c
JOIN Invoice inv ON c.CustomerId = inv.CustomerId
GROUP BY c.FirstName, c.LastName
ORDER BY total_spend DESC
LIMIT 5;


-- ------------------------------------------------------------
-- Query 4: Revenue by employee (sales support agent)
-- Business question: Which employee's assigned customers
-- generated the most revenue?
-- ------------------------------------------------------------
SELECT e.FirstName, e.LastName, SUM(inv.Total) AS revenue
FROM Employee e
JOIN Customer c ON c.SupportRepId = e.EmployeeId
JOIN Invoice inv ON c.CustomerId = inv.CustomerId
GROUP BY e.FirstName, e.LastName
ORDER BY revenue DESC;


-- ------------------------------------------------------------
-- Query 5: Repeat vs one-time customers
-- Business question: What percentage of customers made more
-- than one purchase? (Customer retention indicator)
-- ------------------------------------------------------------
SELECT 
    (SELECT COUNT(DISTINCT CustomerId) FROM Invoice) AS total_customers,
    (SELECT COUNT(*) FROM (
        SELECT CustomerId
        FROM Invoice
        GROUP BY CustomerId
        HAVING COUNT(InvoiceId) > 1
    ) AS repeat_custs) AS repeat_customers;

-- Result: 59 out of 59 customers (100%) made more than one purchase.
-- Insight: Every customer in this dataset is a repeat buyer,
-- suggesting strong retention or a recurring billing pattern
-- in the underlying data.