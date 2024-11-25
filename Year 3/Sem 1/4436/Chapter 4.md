# Network Layer
Sender: encapsulates segments into datagrams, passes to link layer 
Receiver: delivers segments to transport layer protocol
### Functions
Forwarding: Move packet from input link to router output link
Routing: Relies on algorithms to determine packet route

### Data, Control Plane
Data plane: 
	local, per-router function
	Determines how datagram arriving on router input port is forwarded to router output port
Control plane: 
	network-wide logic
	Determines how datagram is routed among routers
		traditional routing algorithms implemented in routers
		software-defined networking implemented in remote servers

### Service Model
![[Pasted image 20241125132026.png]]
Why is best effort used widely?
Simplicity of mechanism, sufficient provisioning bandwidth, replicated application-layer distributed services

### Router
![[Pasted image 20241125133318.png]]
### Input Port
![[Pasted image 20241125133911.png]]
Destination-based forwarding: 
![[Pasted image 20241125134025.png]]
Input will go to the link interface that has the most amount of matches

### Switching Fabrics
transfer packet from input to appropriate output link
switching rate: rate at which packets can move from input to output
![[Pasted image 20241125134353.png]]
three major types of switching fabrics:![[Pasted image 20241125134610.png]]

Input port queuing: if switch fabric is slower than input ports combined, queuing may occur at input queues
Output port queuing:
	Buffering is required when datagrams arrive from fabric faster than link transmission rate
		Drop policy: what datagrams to drop if no free buffers
		Tail drop: drop arriving packet
		Priority drop: drop/remove on priority basis
	Scheduling discipline chooses among queued datagrams for transmission
		Priority scheduling - who gets best performance
### How much buffering?
![[Pasted image 20241125145155.png]]
