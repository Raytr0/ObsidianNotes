### Simple Join
![[Pasted image 20241216232831.png]]![[Pasted image 20241216232837.png]]

FROM Client c JOIN Viewing v ON c.clientNo = v.clientNo
	This is the most common syntax
FROM Client JOIN Viewing USING clientNo
	This only works if both tables column names are the exact same
FROM Client NATURAL JOIN Viewing
	joins ALL columns with the same name

### Sorting Join
SELECT s.branchNO, s.staffNO, fName, lName, propertyNO
FROM Staff s, PropertyForRent p
WHERE s.staffNo = p.staffNo
ORDER BY s.branchNO, s.staffNO, propertyNO
Just has an order by

### Multi Table Join
For each ***branch***, list ***staff*** who manage properties, including city in which
branch is located and the ***properties*** they manage.
This join is using WHERE 
	SELECT b.branchNo, b.city, s.staffNo, fName, lName, propertyNo
	FROM Branch b, Staff s, PropertyForRent p
	WHERE b.branchNo = s.branchNo
		AND s.staffNo = p.staffNo
	ORDER BY b.branchNo, s.staffNo, propertyNo;

This join is using the JOIN syntax
	FROM Branch b
	JOIN Staff s ON b.branchNo=s. branchNo
	JOIN PropertyForRent p ON p.staffNo = s.staffNO

### Multiple Grouping Columns
![[Pasted image 20241217001540.png]]

### Outer Joins
Inner join only displays the rows that satisfy the conditions
Outer joins show the rows that did not satisfy those conditions but as NULL values

Left Outer Join:
Left outer join references the table right after FROM
![[Pasted image 20241217001737.png]]
This causes B004 Bristol to still show up, but PropertyForRent1 will have NULL for that row![[Pasted image 20241217001806.png]]

Right Outer Join:
Right outer join references the table right after JOIN
![[Pasted image 20241217002001.png]]
![[Pasted image 20241217002008.png]]

Full Outer Join:
![[Pasted image 20241217002036.png]]
NULLs B004 and PA14 in different rows
![[Pasted image 20241217002104.png]]


### EXISTS and NOT EXISTS
if you can use a join to get the same results, it is recommended to use join instead
Yes or no
![[Pasted image 20241217002715.png]]
![[Pasted image 20241217002721.png]]

### Union, Intersect, and Difference (Except)
![[Pasted image 20241217002833.png]]
UNION:
![[Pasted image 20241217003002.png]]
or
(SELECT *
FROM Branch
WHERE city IS NOT NULL)
UNION CORRESPONDING BY city
(SELECT *
FROM PropertyForRent
WHERE city IS NOT NULL);

this results in result tables from both queries and merges both tables together, with
duplicate rows removed. since ALL was not specified 

INTERSECT:
![[Pasted image 20241217003110.png]]
Or
(SELECT * FROM Branch)
INTERSECT CORRESPONDING BY city
(SELECT * FROM PropertyForRent);
![[Pasted image 20241217003125.png]]
Is possible without using INTERSECT
![[Pasted image 20241217003155.png]]

EXCEPT:

List of all cities where there is a branch office but no properties.
	(SELECT city FROM Branch)
	EXCEPT
	(SELECT city FROM PropertyForRent);
	or
	(SELECT * FROM Branch)
	EXCEPT CORRESPONDING BY city
	(SELECT * FROM PropertyForRent);

Could rewrite this query without EXCEPT:
	SELECT DISTINCT city FROM Branch
	WHERE city NOT IN
	(SELECT city FROM PropertyForRent);
	or
	SELECT DISTINCT city FROM Branch b
	WHERE NOT EXISTS
	(SELECT * FROM PropertyForRent p
	WHERE p.city = b.city);

INSERT:
INSERT INTO Staff
VALUES (‘SG16’, ‘Alan’, ‘Brown’, ‘Assistant’, ‘M’, Date‘1957-05-25’, 8300, ‘B003’);
Order of values matter and are case sensetive, if no values are provided, write NULL

INSERT ... SELECT:
allows multiple rows to be copied from one or more tables to another:
INSERT INTO TableName [ (columnList) ]
SELECT ...
![[Pasted image 20241217004328.png]]

UPDATE:
UPDATE TableName
SET columnName1 = dataValue1
[, columnName2 = dataValue2...]
[WHERE searchCondition]

DELETE:
will delete all rows, so you have to be very specfic with conditions if you dont want that
DELETE FROM TableName
[WHERE searchCondition]