USE NorthWind
-- 1.1 -- Correct
SELECT c.CustomerID, c.CompanyName, c.Address, c.City, c.Region, c.PostalCode, c.Country
FROM Customers c
WHERE c.City IN ('London','Paris');

-- 1.2 --Correct
SELECT p.ProductName
FROM Products p
WHERE p.QuantityPerUnit LIKE ('%bottle%')

-- 1.3 --Correct
SELECT p.ProductName, s.CompanyName, s.Country
FROM Products p
LEFT JOIN Suppliers s ON p.SupplierID=s.SupplierID
WHERE p.QuantityPerUnit LIKE ('%bottle%')
    
-- 1.4 -- Correct
SELECT c.CategoryName, COUNT(*) AS "Number of Condiments"
FROM Products p
LEFT JOIN Categories c ON p.CategoryID=c.CategoryID
GROUP BY c.CategoryName
ORDER BY 2 DESC;

-- 1.5 -- Correct
SELECT e.TitleOfCourtesy + ' ' + e.FirstName + ' ' + e.LastName AS "Employee Name",
    e.City
FROM Employees e
WHERE e.Country = 'UK';

-- 1.6 -- Correct
SELECT r.regionDescription, 
    ROUND(SUM(od.UnitPrice * od.Quantity * (1- od.Discount)), 2) AS "Total sales"
FROM [Order Details] od 
INNER JOIN Orders o ON od.OrderID = o.OrderID
INNER JOIN Employees e ON e.EmployeeID = o.EmployeeID
INNER JOIN EmployeeTerritories et ON et.EmployeeID = e.EmployeeID
INNER JOIN Territories t ON et.TerritoryID = t.TerritoryID
INNER JOIN Region r ON r.RegionID = t.RegionID
GROUP BY r.RegionID, r.RegionDescription
HAVING SUM(od.UnitPrice * od.Quantity * (1- od.Discount)) > 1000000

-- 1.7 -- Correct
SELECT COUNT(*) AS "Number of Freight Greater than 100"
FROM Orders o
WHERE o.shipcountry IN ('UK', 'USA') 
    AND o.Freight > 100.00


-- 1.8 -- Correct
SELECT TOP 1 od.orderID, 
    od.unitprice * od.quantity * od.Discount AS "Discount Amount"
FROM [Order Details] od
ORDER BY 2 DESC;

-- 2.1 Sparta database
CREATE DATABASE greg_db
USE greg_db

DROP TABLE IF EXISTS spartans
CREATE TABLE spartans
(
    spartan_id INT IDENTITY PRIMARY KEY,
    title CHAR(2),
    first_name VARCHAR(20),
    last_name VARCHAR(20),
    university VARCHAR(60),
    course VARCHAR(60),
    grade INT,
    favourite_number INT,
    can_drive BIT

)

-- 2.2 Insert data
INSERT INTO spartans
VALUES (
    'Mr',
    'Gregory',
    'Spratt',
    'Monsters University',
    'Canister Design',
    21,
    2,
    1
)
INSERT INTO spartans
VALUES (
    'Mr',
    'Ahmed',
    'Rahman',
    'Empire State University',
    'Biophysics',
    43,
    3,
    0
)
INSERT INTO spartans
VALUES (
    'Mr',
    'Alex',
    'Ng',
    'Empire State University',
    'Nuclear Physics',
    56,
    54,
    0
)
INSERT INTO spartans
VALUES (
    'Mr',
    'Andrei',
    'Pavel',
    'Barnett College',
    'Archaeology',
    37,
    3,
    0
)
INSERT INTO spartans
VALUES (
    'Mr',
    'Asakar',
    'Hussain',
    'Sweet Valley University',
    'English',
    3,
    3,
    1
)
INSERT INTO spartans
VALUES (
    'Mr',
    'Ben',
    'Middlehurst',
    'Monsters University',
    'Molecular Pharmacology',
    73,
    65,
    1
)
INSERT INTO spartans
VALUES (
    'Mr',
    'Benjamin',
    'Balls',
    'The Sims 3: University Life',
    'Physics',
    55,
    12,
    0
)
INSERT INTO spartans
VALUES (
    'Mr',
    'Daniel',
    'Alldritt',
    'Monsters University',
    'Physiology',
    24,
    7,
    1
)
INSERT INTO spartans
VALUES (
    'Mr',
    'Ismail',
    'Kadir',
    'Empire State University',
    'Biomechanics',
    65,
    4,
    1
)
INSERT INTO spartans
VALUES (
    'Mr',
    'James',
    'Fletcher',
    'Starfleet Academy',
    'Navagation',
    6,
    32,
    0
)
INSERT INTO spartans
VALUES (
    'Mr',
    'Jamie',
    'Hammond',
    'University of Farmington',
    'Aerospace Engineering',
    66,
    53,
    0
)
INSERT INTO spartans
VALUES (
    'Mr',
    'Josh',
    'Weeden',
    'The Sims 4: Discover University',
    'Chemistry',
    77,
    6,
    0
)
INSERT INTO spartans
VALUES (
    'Mr',
    'Nathan',
    'Johnston',
    'University of Farmington',
    'Wing Mechanics',
    76,
    6,
    0
)
INSERT INTO spartans
VALUES (
    'Mr',
    'Rashawn',
    'Henry',
    'University of Redwood',
    'Anthropology',
    87,
    6,
    0
)
INSERT INTO spartans
VALUES (
    'Mr',
    'Sidhant',
    'Khosla',
    'Monsters University',
    'Cognitive Neuroscience',
    87,
    6,
    1
)
INSERT INTO spartans
VALUES (
    'Mr',
    'Timin',
    'Rickaby',
    'University of Okoboji',
    'Drama',
    98,
    5,
    1
)
INSERT INTO spartans
VALUES (
    'Mr',
    'Yusuf',
    'Uddin',
    'Harmon College',
    'Business',
    54,
    1,
    0
)

SELECT * FROM spartans

USE NorthWind


-- 3.1
SELECT --e.EmployeeID, 
    e.TitleOfCourtesy + ' ' + e.FirstName + ' ' + e.LastName AS "Employee", 
    --e.ReportsTo AS "Reports to ID", 
    em.TitleOfCourtesy + ' ' + em.FirstName + ' ' + em.LastName AS "Employee Reports to"
FROM Employees e
LEFT JOIN Employees em ON e.ReportsTo=em.EmployeeID

-- 3.2
SELECT s.CompanyName, 
    SUM(od.Quantity * od.UnitPrice * (1-od.Discount)) AS "Individual Sale"
FROM Suppliers s
INNER JOIN Products p ON s.SupplierID=p.SupplierID
INNER JOIN [Order Details] od ON p.ProductID=od.ProductID
GROUP BY s.CompanyName
HAVING SUM(od.Quantity * od.UnitPrice * (1-od.Discount)) > 10000
ORDER BY 2 DESC


-- 3.3 
SELECT TOP 10 c.CompanyName, ROUND(SUM((1-od.Discount)*od.Quantity * od.UnitPrice),2) AS "sales"
FROM [Order Details] od
INNER JOIN Orders o
ON o.OrderID = od.OrderID
INNER JOIN Customers c 
ON o.CustomerID = c.CustomerID
GROUP BY c.CompanyName, o.ShippedDate
HAVING o.ShippedDate > '1997-12-31'
ORDER BY sales DESC

-- 3.4
SELECT  YEAR(o.OrderDate) AS "Year", 
        MONTH(o.OrderDate) AS "Month",
        FORMAT(o.OrderDate, 'MMM-yy') AS "Year-Month", 
        AVG(CAST(DATEDIFF(d, o.OrderDate, o.ShippedDate) AS Decimal(4,2))) AS "Average Number of Ship Days" -- Might need to format here as not sure if getting the correct answer with rounding
FROM Orders o
GROUP BY YEAR(o.OrderDate), MONTH(o.OrderDate), FORMAT(o.OrderDate, 'MMM-yy')
ORDER BY 1, 2