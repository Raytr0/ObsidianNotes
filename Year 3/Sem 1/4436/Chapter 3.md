# Transport Layer

### Transport Services and Protocols
Provides logical communication between application processes on different hosts
Network Layer: 
	logical communication between hosts
Transport Layer: 
	logical communication between processes
Sender: 
	breaks application messages into ***segments***, passes to network layer (IP)
Receiver: 
	reassembles segments into messages, passes to application layer
TCP and UDP are two transport protocols that are available
TCP: Transmission Control Protocol
	reliable, in-order delivery
	congestion control
	flow control
	connection setup
UDP: User Datagram Protocol
	unreliable, unordered delivery
	no-frills extension of "best-effort" IP

### Multiplexing/Demultiplexing
host uses ***IP addresses & port numbers*** to direct segment to appropriate socket
![[Pasted image 20241118150405.png|300]]
Connectionless Demultiplexing:
?
