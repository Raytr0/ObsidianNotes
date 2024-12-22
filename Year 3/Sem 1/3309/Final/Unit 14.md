### NoSQL
 Traditional RDBMSs encounter challenges in handling Big Data
 NoSQL and NewSQL data stores - alternatives that can handle
this huge volume of data and provide the scalability
 NoSQL – Not Only SQL
 Model data in means other than the tabular relations used in relational
databases.
 NewSQL - bringing to the relational model the benefits of horizontal
scalability and fault tolerance provided by NoSQL solutions.

 Characteristics
◼ Simple and flexible non-relational data models.
◼ Variety of data models such as graph, document, and key-value.
◼ Ability to scale horizontally over many commodity servers. Thus, good at
handling big data.
◼ Provide high availability
◼ Typically, they do not support ACID transactions (NoSQLs are often BASE
systems)

 BASE systems (Basically Available, Soft state, Eventually consistent)
◼ Basically Available - the data store is available all the time whenever it is
accessed, even if parts of it are unavailable
◼ Soft-state - it does not need to be consistent always and can tolerate
inconsistency for a certain time period
◼ Eventually consistent - after a certain time period, the data store comes to a
consistent state

 Replicated networked storage solutions have an important
restriction, which is formalized by the CAP theorem:
	 CAP properties:
	◼ Consistency - equivalent to having a single up-to-date instance of the data.
	Consistency in CAP is not the same as consistency in ACID
	◼ Availability - the data is available to serve requests at the moment it is needed
	◼ Partition Tolerance - the capacity of the networked shared-data system to
	tolerate network partitions.

Relational DB vs NoSQL
 Data Structure
◼ Relational DB: tables
◼ NoSQL: different data models
 Schema Flexibility
◼ Relational DB: table structure is fixed for all rows?
◼ NoSQL: dynamic – Can vary for different records
 Scalability
◼ Relational DB: typically scale vertically
◼ NoSQL: good at scaling horizontally

 Scaling characteristics
◼ Three scaling dimensions:
 scaling read requests,
 scaling write requests,
 or scaling data storage.

 Scaling characteristics:
◼ Partitioning: horizontal (sharding), vertical, and functional
◼ Replication
◼ Consistency (as in CAP theorem)
◼ Concurrency control

 Categories of NoSQL solutions according to their data model:
◼ Key-value stores
◼ Column-family stores
◼ Document stores
◼ Graph databases

 Key-value stores
◼ Uses a hash table in which there exists a unique key and a pointer to a
particular item of data
◼ Good at retrieval on the key
◼ Examples: Redis, Riak, BerkeleyDB...
◼ Some can run as in-memory databased – Redis is an example

 Column-family stores
◼ Still have rows and columns
◼ Rows do not need to have the same
number of columns
◼ Columns can be added to any row at any
time without having to add it to other rows
◼ Good writing data very fast
◼ Examples: Cassandra, Hbase, DynamoDB

 Document stores
 Uses JSON, XML, or BSON (binary JSON)
documents to store data
 Documents can contain varied structure
 Documents can have nested data
 Good at ease of use, mirroring some programming
languages
 Examples: MongoDB, CouchDB, ...

 Graph databases
 Graph structure: A node represents an
entity. A relationship represents how two
nodes are associated
 Good at representing networks such as social
networks
 Example: Neo4J

 Challenges in the NoSQL domain
◼ terminology diversity and inconsistency
◼ limited documentation
◼ sparse comparison and benchmarking criteria
◼ occasional immaturity of solutions and lack of support
◼ non-existence of a standard query language
◼ not as good as relational databases in handling complex queries

 NewSQL solutions aim to bring the relational data model into the
world of NoSQL
 Examples:
◼ VoltDB, Clustrix, NuoDB – a pure relational view of data
◼ Google Spanner - a semi-relational model (mappings from the primary-key
columns to the other columns)

 NewSQL solutions use different data representations internally