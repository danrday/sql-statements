# sql-statements

1. Provide a query showing Customers (just their full names, customer ID and country) who are not in the US.

## SELECT FirstName || " " || LastName, CustomerId, Country FROM Customer
## WHERE Customer.Country != "USA";

2. Provide a query only showing the Customers from Brazil.

## SELECT FirstName || " " || LastName, CustomerId, Country FROM Customer
## WHERE Customer.Country = "Brazil";


3. Provide a query showing the Invoices of customers who are from Brazil. The resultant table should show the customer's full name, Invoice ID, Date of the invoice and billing country.

## SELECT FirstName || ' ' || LastName AS "FullName", Customer.CustomerId, Customer.Country, Invoice.InvoiceId, Invoice.InvoiceDate, Invoice.BillingCountry FROM Customer
## JOIN Invoice ON Customer.CustomerId = Invoice.CustomerId
## WHERE Customer.Country = "Brazil";


4. Provide a query showing only the Employees who are Sales Agents.

## SELECT FirstName || ' ' || LastName AS "FullName" FROM Employee
## WHERE Employee.Title = "Sales Support Agent";

5. Provide a query showing a unique list of billing countries from the Invoice table.

## SELECT BillingCountry FROM Invoice
## GROUP BY BillingCountry
## ORDER BY BillingCountry ASC;


6. Provide a query showing the invoices of customers who are from Brazil.

## SELECT FirstName || ' ' || LastName AS "FullName", Invoice.* FROM Customer
## JOIN Invoice ON Customer.CustomerId = Invoice.CustomerId

7. Provide a query that shows the invoices associated with each sales agent. The resultant table should include the Sales Agent's full name.

## SELECT Employee.FirstName || ' ' || Employee.LastName AS "FullName", Invoice.* FROM Employee
## JOIN Customer ON Employee.EmployeeId = Customer.SupportRepId
## JOIN Invoice ON Customer.CustomerId = Invoice.CustomerId
## WHERE Employee.Title = "Sales Support Agent"


8. Provide a query that shows the Invoice Total, Customer name, Country and Sale Agent name for all invoices and customers.

## SELECT Invoice.Total, Invoice.BillingCountry, Customer.FirstName || ' ' || Customer.LastName AS "CustomerName", Employee.FirstName || ' ' || Employee.LastName AS "SalesAgent" FROM Invoice, Customer
## JOIN Employee ON Customer.SupportRepId = EmployeeId

9. How many Invoices were there in 2009 and 2011? What are the respective total sales for each of those years?

a. SELECT sum(Invoice.Total), Invoice.InvoiceDate FROM Invoice
WHERE Invoice.InvoiceDate < '2010-01-01 00:00:00'

##83

b.

SELECT sum(Invoice.Total), Invoice.InvoiceDate FROM Invoice
WHERE Invoice.InvoiceDate > '2011-01-01 00:00:00'
AND Invoice.InvoiceDate > '2012-01-01 00:00:00'

##163


10. Looking at the InvoiceLine table, provide a query that COUNTs the number of line items for Invoice ID 37.

## SELECT InvoiceLine.InvoiceId, sum(InvoiceLine.Quantity) AS "Total Items" from InvoiceLine
WHERE InvoiceLine.InvoiceId = 37

11. Looking at the InvoiceLine table, provide a query that COUNTs the number of line items for each Invoice. HINT: [GROUP BY](http://www.sqlite.org/lang_select.html#resultset)

## SELECT InvoiceLine.InvoiceId, sum(InvoiceLine.Quantity) AS "Total Items" from InvoiceLine
## GROUP BY InvoiceLine.InvoiceId

12. Provide a query that includes the track name with each invoice line item.

## SELECT InvoiceLine.InvoiceLineId, Track.Name from InvoiceLine, Track

13. Provide a query that includes the purchased track name AND artist name with each invoice line item.

## SELECT InvoiceLine.InvoiceLineId, Track.Name, Artist.Name from InvoiceLine, Track
## JOIN Album ON Track.AlbumId = Album.AlbumId
## JOIN Artist ON Album.ArtistId = Artist.ArtistId


14. Provide a query that shows the # of invoices per country. HINT: [GROUP BY](http://www.sqlite.org/lang_select.html#resultset)

## SELECT COUNT(Invoice.BillingCountry) AS "Total Invoices", Invoice.BillingCountry FROM Invoice
## GROUP BY(Invoice.BillingCountry)

15. Provide a query that shows the total number of tracks in each playlist. The Playlist name should be include on the resultant table.

16. Provide a query that shows all the Tracks, but displays no IDs. The resultant table should include the Album name, Media type and Genre.

17. Provide a query that shows all Invoices but includes the # of invoice line items.

18. Provide a query that shows total sales made by each sales agent.

19. Which sales agent made the most in sales in 2009?

20. Which sales agent made the most in sales in 2010?

21. Which sales agent made the most in sales over all?

22. Provide a query that shows the # of customers assigned to each sales agent.

23. Provide a query that shows the total sales per country. Which country's customers spent the most?

24. Provide a query that shows the most purchased track of 2013.

25. Provide a query that shows the top 5 most purchased tracks over all.

26. Provide a query that shows the top 3 best selling artists.

27. Provide a query that shows the most purchased Media Type.
