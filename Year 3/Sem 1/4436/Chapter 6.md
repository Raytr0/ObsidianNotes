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
***Broadcast (Shared wire or medium)***
single shared broadcast channel
two or more simultaneous transmissions by nodes: interference
	• collision if node receives two or more signals at the same time

Ideal multi access protocol
	transmission rate of R bps
	when multiple nodes want to transmit, should be R/M
	Fully decentralized

MAC Protocols:
channel partitioning
	• divide channel into smaller “pieces” (time slots, frequency, code)
	• allocate piece to node for exclusive use
random access
	• channel not divided, allow collisions
	• “recover” from collisions
“taking turns”
	• nodes take turns, but nodes with more to send can take longer turns

Channel partitioning MAC protocols: TDMA (Time Division Multiple Access)
	Access to channel in rounds
	Each station gets fixed time slot in each round
	unused slots go idle
	![[Pasted image 20241214235001.png]]
Channel partitioning MAC protocols: FDMA (frequency division multiple access)
	Spectrum divided into different frequency bands
	same logic as before but no rounds![[Pasted image 20241214235044.png]]

Random access protocols
MAC specfies
	• how to detect collisions
	• how to recover from collisions (e.g., via delayed retransmissions)
CSMA (carrier sense multiple access)
	Simple CSMA
		• if channel sensed idle: transmit entire frame
		• if channel sensed busy: defer transmission
		Dont interrupt others
	CSMA/CD: CSMA with collision detection
		• collisions detected within short time
		• colliding transmissions aborted, reducing channel wastage
		• collision detection easy in wired, difficult with wireless
		Collisions can still occur just reduces amount of time wasted
		If collision happens, entire packet is dropped
		![[Pasted image 20241214235352.png]] 
		For ethernet:
		check channel
			if idle: start transmission
			if busy: wait until idle then start
		if detects transmission while sending from other, abort
		then start exponetional backoff
		more collisions = longer backoff interval
![[Pasted image 20241214235552.png]]

### LANs
MAC addresses (or Lan or physical or Ethernet)
• function: used “locally” to get frame from one interface to another physically-connected interface (same subnet, in IP-addressing sense)
• 48-bit MAC address (for most LANs) burned in NIC ROM, also sometimes software settable
hexadecimal (base 16) notation (each “numeral” represents 4 bits)
• e.g.: 1A-2F-BB-76-09-AD
each interface on LAN
	§ has unique 48-bit MAC address
	§ has a locally unique 32-bit IP address (as we’ve seen)
MAC address allocation administered by IEEE
manufacture has to buy portions of MAC address space
§ analogy:
	• MAC address: like Social Security Number
	• IP address: like postal address

### ARP: address resolution protocol
![[Pasted image 20241215001627.png]]
Send request to IP
client at IP then sends response with MAC address
client requesting recieves and stores in ARP

But routing to another subnet?
![[Pasted image 20241215001838.png]]
![[Pasted image 20241215001939.png]]
![[Pasted image 20241215001946.png]]![[Pasted image 20241215001953.png]]![[Pasted image 20241215002002.png]]![[Pasted image 20241215002011.png]]
So basically:
Transmission from A contains MAC and IP of A, MAC of Router, and IP of B
Datagram is extracted which contains IP of A(source) and IP of B(destination)
BC the router connects the two nets, it knows the B MAC address when A did not
Datagram is rewrapped with Router MAC(Source), and B MAC(Dest)
Then sent to B where datagram is extracted again to pass to protocol stack IP

### Ethernet switch
Switch is a link-layer device: takes an active role
	Stores or forwards ethernet frames
	selectively forward frame to one-or-more outgoing links when frame is to be forwarded on segment, uses CSMA/CD to access segment
§ transparent: hosts unaware of presence of switches
§ plug-and-play, self-learning
	• switches do not need to be configured

Switch: multiple simultaneous transmissions
§ hosts have dedicated, direct connection to switch
§ switches buffer packets
§ Ethernet protocol used on each incoming link, so:
	• no collisions; full duplex
	• each link is its own collision domain
§ switching: A-to-A’ and B-to-B’ can transmit simultaneously, without collisions

How does it know what to switch?
They have a switch table
this table fills up by itself, its self learning
![[Pasted image 20241215002754.png]]
![[Pasted image 20241215002744.png]]Switches vs. routers
both are store-and-forward:
	§ routers: network-layer devices (examine network-layer headers) 
	§ switches: link-layer devices (examine link-layer headers)
both have forwarding tables: 
	§ routers: compute tables using routing algorithms, IP addresses 
	§ switches: learn forwarding table using flooding, learning, MAC addresses

### Virtual LANs (VLANs)
VLANs solve scaling issues and efficiency, security, privacy, efficiency issues
switch(es) supporting VLAN capabilities can be configured to define multiple virtual LANS over single physical LAN infrastructure
![[Pasted image 20241215004736.png]]
trunk port: carries frames between VLANS defined over multiple physical switches
has to be in 802.1q ![[Pasted image 20241215010441.png]]
![[Pasted image 20241215010401.png]]

### link virtualization: MPLS
Multiprotocol label switching (MPLS)
forwards packets based on label value, does not care for IP address
its much more flexible than IP routing
![[Pasted image 20241215010642.png]]
entry MPLS router uses RSVP-TE signaling protocol to set up MPLS forwarding at downstream routers (R4 in this case)

### Datacenter networks
![[Pasted image 20241215010933.png]]
Datacenter networks: multipath
![[Pasted image 20241215011111.png]]
Datacenter networks: protocol innovations
![[Pasted image 20241215011138.png]]
