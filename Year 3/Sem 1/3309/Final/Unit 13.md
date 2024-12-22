### Privileges
SELECT Retrieve data from a table.
INSERT Insert new rows into a table.
UPDATE Modify rows of data in a table.
DELETE Delete rows of data from a table.
REFERENCES Reference columns of a named table in integrity constraints.
USAGE Use domains
Owner of the table must GRANT other users permission

### GRANT
GRANT {PrivilegeList | ALL PRIVILEGES}
ON ObjectName
TO {AuthorizationIdList | PUBLIC}
[WITH GRANT OPTION]
![[Pasted image 20241217014653.png]]
Examples:
![[Pasted image 20241217014714.png]]
![[Pasted image 20241217014720.png]]

### REVOKE
REVOKE [GRANT OPTION FOR]
{PrivilegeList | ALL PRIVILEGES}
ON ObjectName
FROM {AuthorizationIdList | PUBLIC}
[RESTRICT | CASCADE]
![[Pasted image 20241217014822.png]]

Special Privileges
![[Pasted image 20241217014855.png]]


### Transactions
Basically Github Commits
If you do a bunch of SQL commands and decide you dont like it, you ROLLBACK
if you like the changes and want to execute it, you COMMIT

Transaction Properties - ACID
	 Atomic: All parts of the transaction MUST be executed; it’s either performed in its entirety or not at all
	 Consistency: A transaction must transform the database from one consistent state to another
	 Isolation: Transactions execute independently of one another. Effects of incomplete transactions are not be visible to other transactions
	 Durability: Upon completion of a transaction the database state cannot be lost, even if there is a system failure.
Transactions cannot be nested
Basic Syntax:
	SET TRANSACTION
	[READ ONLY | READ WRITE] |
	[ISOLATION LEVEL READ UNCOMMITTED |
	READ COMMITTED |
	REPEATABLE READ |
	SERIALIZABLE ]

### Isolation level
How much interaction is allowed from other transactions during the transaction
There is a lot of overhead to guaranteeing the ACID properties
◼ Sometimes full isolation (i.e. full serializability) is not required
![[Pasted image 20241217020133.png]]
![[Pasted image 20241217020151.png]]
![[Pasted image 20241217020205.png]]

### Immediate and Deferred Integrity Constraints
 Do not always want constraints to be checked immediately, but instead at
transaction commit.
 Constraint may be defined as INITIALLY IMMEDIATE or INITIALLY
DEFERRED, indicating mode the constraint assumes at start of each transaction.
 In INITIALLY IMMEDIATE, also possible to specify whether mode can be
changed subsequently using qualifier [NOT] DEFERRABLE.
 Default mode is INITIALLY IMMEDIATE.
Syntax:
	SET CONSTRAINTS
	{ALL | constraintName [, . . . ]}
	{DEFERRED | IMMEDIATE}

### Trigger
Triggering events include insertion, deletion and update of rows in a
table.
◼ Can also be set to cover specific named columns of a table (update).

 To define a trigger, you must specify:
◼ Statement type that causes the trigger to fire (Cause)
 INSERT, UPDATE, DELETE
◼ Timing
 BEFORE, AFTER, INSTEAD OF event
➢ BEFORE: trigger is fired before event occurs
➢ AFTER: trigger is fired after event occurs
➢ INSTEAD OF: trigger is fired instead of executing the original SQL statement
◼ Level
 STATEMENT or ROW
➢ FOR EACH ROW: fires once for each row that is affected
➢ FOR EACH STATEMENT: fires once, regardless of how many rows are
affected (default)

Syntax:
	CREATE TRIGGER TriggerName
	BEFORE|AFTER|INSTEAD OF<triggerEvent\> ON <TableName\>
	[REFERENCING <oldOrNewValuesAliasList\>]
	[FOR EACH {ROW|STATEMENT}]
	[WHEN (triggerCondition)]
	<triggerBody\>
<triggerBody\> cannot contain:
	 SQL transaction statements (COMMIT or ROLLBACK)
	 SQL schema definition or manipulation statements (e.g. creation/ deletion
	of tables, user-defined types, other triggers)
REFERENCING <oldOrNewValuesAliasList\>
![[Pasted image 20241217020543.png]]
![[Pasted image 20241217020657.png]]
![[Pasted image 20241217020703.png]]
to create a Trigger
	must have ownership of table
	must have CREATE TRIGGER privilege
	cannot execute COMMIT in trigger (trigger is part of transaction)

 Syntax to drop a trigger:
◼ DROP TRIGGER <trigger_name>;
 Syntax to enable or disable a trigger
◼ ALTER TRIGGER <trigger_name> [ENABLE | DISABLE];