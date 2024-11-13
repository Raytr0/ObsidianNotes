### System Design
Transformation of an analysis model into a system design model.
Activities:
	Identify design goals and **prioritize** the qualities of the system they should optimize
	Design initial subsystem decomposition
		Break system into smaller parts based on use case and analysis models
		Developers use **standard architectural styles** as a starting point
	Refine and redesign until all goals are satisfied

Example of redesigning a residential house here (slides 9 - 13)
### Subsystems
To reduce complexity of the solution domain, decompose it into subsystems
Subsystems: A **replaceable** part of the system with well-defined **interfaces** that encapsulate the state and behavior of its classes
![[Pasted image 20241113010858.png]]

### Services and Interfaces
A service is a set of related operations that share a common purpose.
A subsystem is characterized by the services it provides to other subsystems.
The subsystem interface includes the name of the operations, their parameters, their types, and their return values
System Design: Focuses on defining services provided from each subsystem
Object Design: Focuses on API

### Component Interfaces
Provided and required interfaces can be depicted in UML with assembly connectors, also called ball-and-socket connectors.
![[Pasted image 20241113095804.png]]

### Coupling
Number of dependencies between two subsystems
Loosely Coupled: Relatively independent, any changes to either side will not impact as much
Strongly Coupled: changes on either side will likely have an impact on another
Loosely coupled as reasonable designs are desirable 
**An objective of a good design is to minimize the coupling**

### Cohesion
The number of dependencies within a **subsystem**
High Cohesion: Subsystem contains objects related to each other and preform similar tasks
Low Cohesion: Subsystem contains number of unrelated objects