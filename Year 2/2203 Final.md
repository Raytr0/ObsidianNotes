Actor: Interacts with the system but not part of it
	Timer is often an actor
	Always external
	Interacts indirectly
Use Case: Something that the actor wants the system to do
	Function provided by the system
System: Box labeled with the system name, actors outside, use cases inside

<<\include>>: reusable use case interacting with use cases
![[Pasted image 20240426204511.png]]
<<\extend>>:Supplier to Base, may include base under conditions
![[Pasted image 20240426204545.png]]

Class visibility
![[Pasted image 20240426205250.png]]
![[Pasted image 20240426205322.png]]
Class Relationships
![[Pasted image 20240426205338.png]]
![[Pasted image 20240426205357.png]]

Sequence Diagrams
![[Pasted image 20240426205447.png]]
Synchronous Message: Waits for a return
Asynchronous Message: Does not wait for a return before carrying on with the rest
![[Pasted image 20240426205616.png]]
Example
![[Pasted image 20240426205646.png]]
![[Pasted image 20240426205653.png]]
