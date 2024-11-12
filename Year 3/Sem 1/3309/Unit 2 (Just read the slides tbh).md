### File based systems
Collection of application programs that perform services for the end users (e.g. Production of reports).
File-based systems store data in files and directories.
Each program defines and manages its own data.
![[Pasted image 20240917145513.png|500]]
Limitations:
	Definition of data was embedded in application programs, rather than being stored separately and independently.
	No control over access and manipulation of data beyond that imposed by application programs.
	Limited data integrity as there's no central control over data. This often leads to inconsistencies.
	Data retrieval and manipulation require custom programming.
Solution?
	Database Management System (DBMS)

### DBMS
DBMS bridges the users application programs with the database, it is a system that enables users to define, create, and maintain the database and that provides controlled access to the DB

DBMS facilities:
	Data Definition Language (DDL):
		Permits specification of data types, structures and any data constraints. 
		All specifications are stored in the database.
	Data manipulation language (DML):
		General enquiry facility (query language) of the data.
		Used for selecting, inserting, deleting and updating data in a database.

Database:
	Shared collection of logically related data
System Catalog/ Data Dictionary/Metadata:
	Provides description of data to enable program
![[Pasted image 20240918102914.png|500]]
Insulation between data and programs:
	program-data independence
	allows for changing data storage structures and operations without changing DBMS access programs
Data abstraction:
	a data model is used to hide storage details

