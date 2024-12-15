### Routing protocols
determine path from one end to another

Dijkstra's algorithm![[Pasted image 20241214202703.png]]
D(""): shortest path length
p(""): previous node

Bellman-Ford
![[Pasted image 20241214202819.png]]
expands like a web per time through iterative communication

### Scaling Routing
intra-AS:
	routing among within the same network
	 RIP: Routing Information Protocol [RFC 1723]
		• classic DV: DVs exchanged every 30 secs
		• no longer widely used
	EIGRP: Enhanced Interior Gateway Routing Protocol
		• DV based
		• formerly Cisco-proprietary for decades (became open in 2013 [RFC 7868])
	OSPF: Open Shortest Path First [RFC 2328]
		• link-state routing
		• IS-IS protocol (ISO standard, not RFC standard) essentially same as OSPF

inter-AS:
	routing among AS'es![[Pasted image 20241214204057.png]]

### BGP (Border Gateway Protocol): the de facto inter-domain routing protocol
eBGP: obtain subnet reachability information from neighboring ASes
iBGP: propagate reachability information to all AS-internal routers.
determine “good” routes to other networks based on reachability information
and policy

![[Pasted image 20241214210233.png]]![[Pasted image 20241214210243.png]]![[Pasted image 20241214210251.png]]
• OPEN: opens TCP connection to remote BGP peer and authenticates sending BGP peer
• UPDATE: advertises new path (or withdraws old)
• KEEPALIVE: keeps connection alive in absence of UPDATES; also ACKs OPEN request
• NOTIFICATION: reports errors in previous msg; also used to close connection
![[Pasted image 20241214210329.png]]

### SDN Control Plane
![[Pasted image 20241214230239.png]]![[Pasted image 20241214230251.png]]
Essentially, compared to traditional algorithms, calculating how to divert traffic is near impossible
by using SDN Control Planes, we are much more able to handle traffic on the fly