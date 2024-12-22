◼ Upper-case letters represent reserved words.
◼ Lower-case letters represent user-defined words.
◼ | indicates a choice among alternatives.
◼ Curly braces indicate a required element.
◼ Square brackets indicate an optional element.
◼ (…) indicates optional repetition (0 or more). 
SQL is case insenstive, unless its a name

### SELECT Statement
**SELECT** Specifies which columns are to appear in the output.
	**DISTINCT** Specifies to eliminate duplicates
	**ALL** 
**AS** Extracts specified column and renames it accordingly
**FROM** Specifies table(s) to be used.
**WHERE** Filters rows.
	salary >= 20000 AND salary <= 30000;
	position = ' Manager ' OR position = ' Supervisor ‘;
	Can be used in numeric and non-numeric fields:
		**COUNT** returns number of values in specified column.
		**MIN** returns smallest value in specified column.
		**MAX** returns largest value in specified column.
	Numeric fields only:
		**SUM** returns sum of values in specified column.
		**AVG** returns average of values in specified column.
**GROUP BY** [columnList]Forms groups of rows with same column value.
**HAVING** Filters groups subject to some condition.
**ORDER BY** [columnList]Specifies the order of the output.
	By default is Ascending
	specify **DESC** 

SELECT [DISTINCT | ALL]
{* | [columnExpression [AS newName]] [,...] }
FROM TableName [alias] [, ...]
[WHERE condition]
[GROUP BY columnList]
[HAVING condition]
[ORDER BY columnList]

### Subqueries
Equality (=):
![[Pasted image 20241216164702.png]]
Aggregates:

### Nested Subquery
ANY/ALL:
	SELECT column_name(s)
	FROM table_name
	WHERE column_name operator ALL/ANY
	  (SELECT column_name
	  FROM table_name
	  WHERE condition);


### SQL Datatypes
![[Pasted image 20241216170546.png]]
Character:
	CHAR: Fixed in length
	VARCHAR: Not fixed, can be any length between nothing and specified length
	example: address VARCHAR(30)

Exact Numeric:
	NUMERIC [ precision [, scale] ]
	DECIMAL [ precision [, scale] ] (or DEC)
	INTEGER (or INT)
	SMALLINT
	BIGINT

Approximate numeric:
	FLOAT [precision]
	REAL
	DOUBLE PRECISION

Datetime:
	DATE
	TIME [timePrecision] (xx:xx:xx format)
	TIMESTAMP [timePrecision (# of decimal points in time)] (Has timezone)

# Integrity Enhancement Feature (IEF)
### 1. **Required Data**
Something like a NOT NULL constraint
position VARCHAR(10) NOT NULL
### 2. **Domain Constraints**
In the CREATE and ALTER table:
CHECK (searchCondition)
for example:
	gender CHAR(1) NOT NULL
	CHECK(gender IN('M','F','O'))
	This only allows M, F, O to be added
CREATE DOMAIN DomainName [AS] dataType
[DEFAULT defaultOption]
[CHECK (searchCondition)]
	![[Pasted image 20241216213541.png]]
Can be removed using DROP DOMAIN:
	DROP DOMAIN DomainName
	[RESTRICT | CASCADE]
	RESTRICT will only work when domain is not in use
	CASCADE drops too much stuff so avoid to use, very messy results if not clear
### 3. Entity Integrity
Primary key of a table must be unique, non-null
![[Pasted image 20241216214030.png]]
### 4. Referential Integrity
Referential integrity means that, if FK contains a value, that value must refer to
existing row in a parent table.
Any INSERT/UPDATE that attempts to create FK value in child table without matching candidate key value in parent is rejected
◼ CASCADE
	Delete the row from the parent and delete the matching rows in the child, and so on in cascading manner.
◼ SET NULL
	Delete row from parent and set FK columns in child to NULL
◼ SET DEFAULT
	Delete row from parent and set FK in child to specified default, only valid if DEFAULT specified for FK.
◼ NO ACTION
	Reject delete. Default Setting.
Example:
![[Pasted image 20241216214753.png]]
### 5. General Constraints
CHECK/UNIQUE in CREATE and ALTER TABLE.
Also have:
	CREATE ASSERTION AssertionName
	CHECK (searchCondition)
ASSERTION very similar to CHECK but better to use when constraint involves more than one table
	CREATE ASSERTION StaffNotHandlingTooMuch
	CHECK (NOT EXISTS (SELECT staffNo
					FROM PropertyForRent
					GROUP BY staffNo
					HAVING COUNT(*) > 100))


### Data Definition
SQL DLL statements:
	CREATE SCHEMA, DROP SCHEMA
	CREATE/ALTER DOMAIN, DROP DOMAIN
	CREATE/ALTER TABLE, DROP TABLE
	CREATE VIEW, DROP VIEW
![[Pasted image 20241216215656.png]]

### Create Schema
CREATE SCHEMA [Name | AUTHORIZATION CreatorId ]

CREATE SCHEMA sqlTest AUTHORIZATION Smith;

DROP SCHEMA Name [RESTRICT | CASCADE ]
### Create Table
![[Pasted image 20241216230329.png]]
### Alter Table
ALTER TABLE TableName
[ADD [COLUMN] columName dataType [NOT NULL|UNIQUE]
[DEFAULT defaultOption] [CHECK (searchCondition)]]
[DROP [COLUMN] columnName [RESTRICT | CASCADE]]
[ADD [CONSTRAINT [constraintName]] tableConstraintDefinition]
[DROP CONSTRAINT constraintName [RESTRICT | CASCADE]]
[ALTER [COLUMN] columName SET DEFAULT defaultOption]
[ALTER [COLUMN] columName DROP DEFAULT]
### Drop Table
DROP TABLE TableName [RESTRICT | CASCADE]
RESCTRICT will not allow the drop if other tables are using it
CASCADE drops everything
DELETE just deletes rows and keeps table

