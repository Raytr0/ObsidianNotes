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

### Buffer Management
Dropping packets:
	Tail Drop: drop arriving packet
	Priority: drop/remove on priority basis

### Packet Scheduling
First Come, First Served
Priority:
	queued by class, header fields can be used for classification
Round Robin:
	Same queued by class, sorted into different classes, and sends one complete packet from each class in order
Weighted Fair Queueing
	![[Pasted image 20241214190552.png]]

### IP addressing
IP address: 
	32 bit identifier assigned to each host or router ***interface***
interface:
	connection between host/router and physical link
CIDR: Classless InterDomain Routing
subnet portion of address of arbitrary length
![[Pasted image 20241214191620.png]]

How to get an IP?
Host:
	host ip is hard-coded by sysadmin config file
	or
	DHCP: Dynamic Host Configuration Protocol
	dynamically gets address from server when it "joins" network
	
Network:
	gets allocated portion of its provider ISP’s address space![[Pasted image 20241214192429.png]]
ISP:
	ICANN: Internet Corporation for Assigned Names and Numbers http://www.icann.org/
	• allocates IP addresses, through 5 regional registries (RRs) (who may then allocate to local registries)
	• manages DNS root zone, including delegation of individual TLD (.com, .edu , …) management 
Ran out what now:
ICANN ran out of IPv4 in 2011, now use IPv6 which is 128-bit
### Subnets
Device interfaces that can reach each other without passing thru a router
same subnet: high order bits
host part: remaining low order bits
Each isolated network is a subnet

![[Pasted image 20241214192641.png]]

### IPv6
Datagram format:
![[Pasted image 20241214192708.png]]
Transition from IPv4 to IPv6:
Not all routers can be upg to IPv6
use tunneling: IPv6 datagram carried as payload in IPv4 datagram among IPv4 routers
![[Pasted image 20241214192821.png]]
![[Pasted image 20241214192923.png]]

### Generalized forwarding
each router contains a forwarding table, aka flow table
match arriving bits (headers field values), and do action accordingly
	• match: pattern values in packet header fields
	• actions: for matched packet: drop, forward, modify, matched packet or send matched packet to controller
	• priority: disambiguate overlapping patterns
	• counters: #bytes and #packets

### OpenFlow
![[Pasted image 20241214193248.png]]
![[Pasted image 20241214193257.png]]
Possible that most other things we dont care about so we can just use a wildcard for it