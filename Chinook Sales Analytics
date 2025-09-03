# For this project, I performed analytics on a sales database downloaded from the internet using SQL. 

#1. Show Customers (their full names, customer ID, and country) who are not in the US. 
SELECT 
   CustomerID, FirstName, LastName, Country
   FROM customers 
WHERE Country <> 'USA';

#2. Show only the Customers from Brazil.
SELECT 
   CustomerID, FirstName, LastName, Country
   FROM customers 
WHERE Country = 'Brazil';

#3. Find the Invoices of customers who are from Brazil. The resulting table should show the customer's full name, Invoice ID, Date of the invoice, and billing country.
SELECT 
   Cust.FirstName, Cust.LastName, Inv.InvoiceId, Inv.InvoiceDate, Inv.BillingCountry
   FROM customers Cust
JOIN Invoices Inv
ON Cust.CustomerID=Inv.CustomerID
WHERE Inv.BillingCountry = 'Brazil';

#4. Show the Employees who are Sales Agents.
SELECT EmployeeId, LastName, FirstName, Title 
FROM employees 
WHERE Title LIKE '%sales%agent%';

#5. Find a unique/distinct list of billing countries from the Invoice table.
SELECT DISTINCT BillingCountry AS Country
FROM Invoices
GROUP BY Country 
;

#6. Provide a query that shows the invoices associated with each sales agent. The resulting table should include the Sales Agent's full name.
SELECT Inv.InvoiceId, Emp.FirstName, Emp.LastName
FROM employees Emp 
LEFT JOIN customers Cust
ON Emp.EmployeeId=Cust.SupportRepId
JOIN Invoices Inv
ON Cust.CustomerId=Inv.CustomerId
ORDER BY Inv.InvoiceId;

#7. Show the Invoice Total, Customer name, Country, and Sales Agent name for all invoices and customers.
SELECT Inv.Total AS InvoiceTotal, 
   Cust.FirstName AS Cust_FirstName,
   Cust.LastName AS Cust_LastName,
   Cust.Country AS Cust_Country,
   Emp.FirstName AS Emp_FirstName, 
   Emp.LastName AS Emp_LastName
FROM Invoices Inv
LEFT JOIN customers Cust 
ON Cust.CustomerId=Inv.CustomerId
LEFT JOIN employees Emp 
ON Emp.EmployeeId=Cust.SupportRepId 
ORDER BY Cust_Country;

#8. How many Invoices were there in 2009?
SELECT COUNT(InvoiceDate) 
FROM invoices
WHERE InvoiceDate LIKE '2009%';

#9. What are the total sales for 2009?
SELECT SUM(Total) 
FROM invoices
WHERE InvoiceDate LIKE '2009%';

#10. Write a query that includes the purchased track name with each invoice line ID.
SELECT InvIt.InvoiceLineId, Tr.Name
FROM invoice_items InvIt
  JOIN invoices Inv
    ON InvIt.InvoiceId=Inv.InvoiceId
  JOIN tracks Tr
    ON Tr.TrackId=InvIt.TrackId
ORDER BY invIt.InvoiceLineId      
;

#12. Write a query that includes the purchased track name AND artist name with each invoice line ID.
SELECT InvIt.InvoiceLineId, Tr.Name Track, Art.Name Artist
FROM invoice_items InvIt
  JOIN invoices Inv
    ON InvIt.InvoiceId=Inv.InvoiceId
  JOIN tracks Tr
    ON Tr.TrackId=InvIt.TrackId
  JOIN Albums Alb
    ON Tr.AlbumId =Alb.AlbumId
 JOIN artists Art
    ON Alb.ArtistId =Art.ArtistId     
ORDER BY invIt.InvoiceLineId  
;    

#13. Provide a query that shows all the Tracks, and include the Album name, Media type, and Genre.
SELECT Tr.Name Track, Alb.Title Album, Mt.Name MediaType, Gen.Name Genre
FROM tracks Tr
  LEFT JOIN albums Alb
    ON  Tr.AlbumId=Alb.AlbumId
LEFT JOIN media_types Mt
    ON Mt.MediaTypeId=Tr.MediaTypeId     
  LEFT JOIN genres Gen
    ON Gen.GenreId=Tr.GenreId 
ORDER BY Album  
;  

#14. Show the total sales made by each sales agent.
SELECT SUM(Inv.Total) AS TotalSales, 
   Emp.FirstName AS Emp_FirstName, 
   Emp.LastName AS Emp_LastName
FROM Invoices Inv
LEFT JOIN customers Cust 
ON Cust.CustomerId=Inv.CustomerId
LEFT JOIN employees Emp 
ON Emp.EmployeeId=Cust.SupportRepId 
GROUP BY Emp.LastName
ORDER BY TotalSales DESC;

#15. Which sales agent made the most dollars in sales in 2009?
SELECT SUM(Inv.Total) AS TotalSales, 
   Emp.FirstName AS Emp_FirstName, 
   Emp.LastName AS Emp_LastName
FROM Invoices Inv
LEFT JOIN customers Cust 
ON Cust.CustomerId=Inv.CustomerId
LEFT JOIN employees Emp 
ON Emp.EmployeeId=Cust.SupportRepId 
WHERE Inv.InvoiceDate LIKE '2009%'
GROUP BY Emp.LastName
ORDER BY TotalSales DESC
LIMIT 1;

#16. what are the top 3 mos popular genres?
SELECT Gen.Name Genre
FROM invoice_items InvIt
  JOIN invoices Inv
    ON InvIt.InvoiceId=Inv.InvoiceId
  JOIN tracks Tr
    ON Tr.TrackId=InvIt.TrackId
 JOIN genres Gen
    ON Gen.GenreId=Tr.GenreId     
GROUP BY Genre
ORDER BY Count(Gen.Name) DESC 
LIMIT 3;    

#17. Which customer spent the most money? Note the first and last name of the customer as well as the total spent. 
SELECT Cust.FirstName, Cust.LastName, SUM(Inv.Total) AS TotalSpent
FROM invoices Inv
   JOIN Customers as Cust
      ON Cust.CustomerId=Inv.CustomerId
  GROUP BY Cust.LastName
  ORDER BY TotalSpent DESC
LIMIT 1  
;

#18. In Which Country do we have the most customers?
SELECT BillingCountry, COUNT(BillingCountry)
FROM invoices
GROUP BY BillingCountry
ORDER BY COUNT(BillingCountry) DESC
LIMIT 1
;
