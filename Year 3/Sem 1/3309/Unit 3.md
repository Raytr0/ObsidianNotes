# Entity-Relationship Modeling
![[Pasted image 20240918113846.png]]
### ER Model
ER diagram:
	a graphical representation of the logical structure of a database.
	illustrates the relationship between entities
ER diagram notations:
	Chen
	Crow's Foot
	**UML DATABASE NOTATION**
	Others

# Concepts of the ER Model
### Entity Type
Entity Type:
	Group of objects with same properties, identified by enterprise as having an independent existence.
Entity occurrence:
	Uniquely identifiable object of an entity type.
### Relationship Types
Relationships may be given role names to indicate purpose for the participating entity type
![[Pasted image 20240918120205.png|300]]
Relationship Type:
	Set of meaningful associations among entity types
Relationship occurrence:
	Uniquely identifiable association, which includes one occurrence from each participating entity type.
Recursive Relationship:
	where the **same** entity type participates more than once in **different** roles
	Example: **Staff (supervisor)** supervises **staff (supervisee)**
### Degree of a relationship
The number of participating entities in a relationship
two is binary
	Example: **Private Owner** owns **Property for Rent**
three is ternary
	Example: **Staff** registers a **Client** at a **Branch**
four is quaternary
	Example: A **Solicitor** arranges a **Bid** on behalf of a **Buyer** supported by a **Financial Institution**
	
### Attributes
Attribute:
	Property of an entity or a relationship type.
Attribute Domain:
	Set of allowable values for one or more attributes.
Simple Attribute: 
	Attribute composed of a single component with an independent existence.
Composite Attribute: 
	Attribute composed of multiple components, each with an independent existence.
Single-valued Attribute:
	Attribute that holds a single value for each occurrence of an entity type.
Multi-valued Attribute:
	Attribute that holds multiple values for each occurrence of an entity type.
Derived Attribute:
	Attribute that represents a value that is derivable from value of a related attribute, or set of attributes, not necessarily in the same entity type.
### Keys
Candidate Key:
	Minimal set of attributes that uniquely identifies each occurrence of an entity type.
Primary Key:
	Candidate key selected to uniquely identify each occurrence of an entity type.
Composite Key:
	A candidate key that consists of two or more attributes.
![[Pasted image 20240918125451.png]]
### Entity Type
Strong Entity Type: 
	Entity type that is not existence-dependent on some other entity type.
Weak Entity Type:
	Entity type that is existence-dependent on some other entity type.
![[Pasted image 20240918125751.png|500]]
### Structural Constraints
Constraints represent restrictions in the real world. 
Main type of constraint on relationships is called multiplicity. 
Multiplicity: 
	number (or range) of possible occurrences of an entity type that may relate to a single occurrence of an associated entity type through a particular relationship. 
Represents policies (called business rules) established by the user or company.
Look at slides for visual representation of relations below
![[Pasted image 20240918125917.png]]
Multiplicity is made up of two types of restrictions on relationships:
	Cardinality: 
		Describes the maximum number of possible relationship occurrences for an entity participating in a given relationship type.
	Participation: 
		Determines whether all or only some entity occurrences participate in a relationship.
### Problem with ER Models
Fan Trap: 
	Where a model represents a relationship between entity types, but pathway between certain entity occurrences is ambiguous. 
Chasm Trap: 
	Where a model suggests the existence of a relationship between entity types, but pathway does not exist between certain entity occurrences.
Slides again