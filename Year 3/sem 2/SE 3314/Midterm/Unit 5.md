# Connecting Devices & Command Line Interface
![[Pasted image 20250209235959.png]]
### Console Connection
This uses the router's console port
1. Connect a terminal directly to the router 
2. Connect a PC running terminal emulation software to the console port through the PC’s COM port

### Terminal Setting
use the HyperTerminal program included with Windows to make a console connection with the router.

### Virtual Terminal Connection
allows for you to connect to a router through a network connection without being physically close
You must complete the following configuration tasks before you can make VTY connection:
1. Configure a router interface with an IP address
2. Configure the router VTY line
3. Set the enable secret password 

### Back-to-Back Connections
router must be connected to a device (such as a CSU/DSU or another router) that provides clocking signals.
➢The router providing clocking is known as the **DCE** (data circuit-terminating equipment). 
➢The router not providing clocking is known as the **DTE** (data terminal equipment).
line between two routers will only be up if clocking speed is configured

### Command Line Interface (Cisco IOS)
\> is user
\# is privileged mode


# Routing Protocols
The term routing is used for taking a packet from one device and sending it through the network to another device on a different network.
Static Routing: Admin needs to manually update by hand
Dynamic Routing: Automatically updates the routing tables based on the algorithm used

### Concepts
Each organization that has been assigned a network address from an ISP is considered an Autonomous System (AS).
Can create large network or divide into smaller subnets
Routers are used within AS to segment the networks, and to connect subnets together
❑ Routing protocols can be classified based on whether they are routing traffic within or between
autonomous systems.
	➢ Interior Gateway Protocol (IGP): protocol that routes traffic within the AS, for example, RIP, OSPF, or IGRP
	➢ Exterior Gateway Protocol (EGP): protocol that routes traffic outside of or between ASs, for example, Border Gateway Protocol (BGP)
Administrative Distances, is used to rate the credibility of the routing information received on a router from a neighbor router. is a integer from 0 to 255, where 0 is most trusted.![[Pasted image 20250210022605.png]]
Manually Configuring Routes (summary)
![[Pasted image 20250210022857.png]]
Example with commands in slides check if needed

### Distance Vector Protocols
❑ The distance vector protocols find the best path to a remote network by judging the distance.
❑ Each time a packet goes through a router is counted as one hop
❑ Least number of hops to the destination is determined to be the best route.
❑ RIP and IGRP are distance vector protocols
❑ In the distance vector routing:
	◉Routers send updates only to their neighbor routers
	◉Routers send their entire routing table
	◉Tables are sent at regular intervals (each router is configured to specify
	its own update interval)
	◉Routers modify their tables based on information received from their neighbors 

I stg the rest are mostly examples and commands for cisco, just read the slides