### Link Layer
Context:
![[Pasted image 20241214232213.png]]

Services:
framing, link access
reliable delivery between adjacent nodes
flow control
error detection
	fix or drop
error correction
half-duplex and full-duplex:
	with half duplex, nodes at both ends of link can transmit, but not at same time

Implementation:
Every host has it
link layer implemented in network interface card (NIC) or on a chip
![[Pasted image 20241214233132.png]]

### Error detection
not 100% reliable
Parity Checking:
![[Pasted image 20241214233218.png]]
Cyclic Redundancy Check (CRC):
more powerful 
![[Pasted image 20241214233552.png]]
![[Pasted image 20241214233605.png]]

### Multi Access Protocols
point-to-point
***Broadcast***