![[Pasted image 20250209185523.png]]
End user: PC, laptop, tablet, smartphon
Network access facilities: DSL, cable modems, wifi, WiMAX
Network provider: connects directly to internet, wifi networks, cellular networks
Application service providers: servers that have content, email servers, stuff like that


### The modern networking ecosystem
Data center networking: large number of interconnected servers, only 20% is external networking to reach users
IoT or fog networking: millions of devices, usually machine to machine data transfer than to user

![[Pasted image 20250209191328.png]]

IP Backbone: Consists of Core(high speed interconnected routers), Edge(connects to external networks and users), and Aggregation(connect number of router and switches to external resources) Routers


# Ethernet
Ethernet: wired local-area network technology, supports up to 100Gbps from meters to kilometers.
Two extensions of Ethernet technology have enhanced and extended the use of Ethernet in the home:
	➢ Powerline carrier (PLC) - use the power wire as a communication channel to transmit Ethernet packets on top of the power signal 
	➢ Power over Ethernet (PoE) - uses the existing Ethernet cables to distribute power to devices on the network.
Also dominant in office spaces, had some competitors but simplicity and wide availability made ethernet winner
![[Pasted image 20250209195452.png]]Ethernet in data centers: widely used due to frequent large data transfers
	Co-located servers and storage units 
	➢ high-speed Ethernet fiber links and switches provided the needed networking infrastructure
	Backplane Ethernet 
	➢ Runs over copper jumper cables that can provide up to 800 Gbps over very short distances 
	➢ This technology is ideal for the Blade servers - Multiple server modules housed in a single chassis

Standards
❑ 10Base2: 10 = 10mbps
❑ 10Base5: base = baseband signalling
❑ 10BaseT: 5 = 500m, 2 = 185m, T = twisted pair 100m
❑ 100BaseT: 100 mbps 
❑ Gigabit: 1000 mbps 
❑ 10 GBase-?: 10 gbps 
❑ 100 GBase-?: 100 gbps
❑ CSMA/CD: Carrier Sense Multiple Access with a collision detection facility
❑ Addressing: MAC address
❑ Framing: 802.3
![[Pasted image 20250209195847.png]]
![[Pasted image 20250209200145.png]]
![[Pasted image 20250209200208.png]]![[Pasted image 20250209200216.png]]![[Pasted image 20250209200223.png]]

### Ethernet (CSMA/CD)
Carrier Sense, Multiple Access/Collision Detection.
![[Pasted image 20250209202105.png]]
### Ethernet (Frame Structure)
![[Pasted image 20250209202122.png]]
1 byte is 8 bits
physical layer is not formally part of the frame, since its added at the physical layer
Preamble alerts system to receive incoming frame
SFD signals beginning of frame, also gives station last chance to synchronize
Destination address contains the physical address of the next station
Source address contains the physical address of the sender
❑ Length/type, has one of two meanings. 
	➢ If the value of the field is less than 1518. it is a length field and defines the length of the data field that follows. 
	➢ If the value of this field is greater than 1536. it defines the upper layer protocol that uses the services of the Internet
Data and padding field contains information encapsulated from the upper layer protocols min of 46 and max of 1500 bytes
CRC is the last field in the 802.3 frame, contains error detection information which is checked at receiver
![[Pasted image 20250209202632.png]]
![[Pasted image 20250209202639.png]]

# Wifi
Standardized by IEEE 802.11
Enterprises have also transitioned to use more Wifi due to the employee preferences of using mobile devices
### Standards
Interoperability is guaranteed by: 
	➢ IEEE 802.11 wireless LAN committee develops the protocol and signaling standards 
	➢ The Wi-Fi Alliance creates test suites to clarify interoperability for commercial products that conform to various IEEE 802.11 standards 
	➢ The term Wi-Fi (wireless fidelity) is used for products certified by the Alliance
![[Pasted image 20250209205058.png]]
![[Pasted image 20250209210129.png]]

# Cloud Computing
➢ Broad network access ✓ the capabilities to access the network through heterogeneous platforms (mobile phones, laptops, PDAs, etc.) 
➢ Rapid elasticity ✓ enables users to expand and reduce resources according to their specific service requirement. 
➢ Measured service ✓ Resource usage can be monitored, controlled, and reported 
➢ On-demand self service 
➢ Resource pooling
![[Pasted image 20250209210203.png]]

# Cloud Storage
subset of cloud computing
allows smaller businesses and operations to access database applications without the need of buying, creating, and maintaining their own physical system

# Internet Of Things
interconnection of smart devices
A massive system that consists of 5 layers:
➢ Sensors and actuators
	✓ These are the “things”
	✓ Sensors observe their environment and report back quantitative measurements
	✓ Actuators operate on their environment
➢ Connectivity
	✓ A device may connect via either a wireless or wired link into a network to send collected data to the appropriate data center (sensor) or receive operational commands from a controller site (actuator)
➢ Capacity
	✓ The network supporting the devices must be able to handle a potentially huge flow of data
➢ Storage
	✓ There needs to be a large storage facility to store and maintain backups of all the collected data
➢ Data analytics
	✓ For large collections of devices, “big data” is generated, requiring a data analytics capability to process the data flow
![[Pasted image 20250209210421.png]]

# Network Convergence
Refers to the merger of previously distinct telephony and information technologies and markets
Merging multiple things into one service
Benefits
✓ Cost Savings:
	• Converging legacy networks onto a single IP network enables better use of existing resources, and
	implementation of centralized capacity planning, asset management, and policy management.
✓ Effectiveness:
	• The converged environment has the potential to provide users with great flexibility, irrespective of
	where they are. IP convergence allows companies to create a more mobile workforce.
✓ Transformation:
	• Because they are modifiable and interoperable, converged IP networks can easily adapt to new
	functions and features as they become available through technological advancements without having
	to install new infrastructure.

# Unified Communications (UC)
Benefits
✓Personal Productivity Gains:
	• Presence information helps employees find each other and choose the most effective way
	to communicate in real time. Less time is wasted.
✓Workgroup Performance Gains:
	• UC systems support real-time collaboration among team members, which facilitates
	workgroup performance improvements
✓Enterprise-level process improvements:
	• IP convergence enables UC to be integrated with enterprise-wide and departmental-level
	applications, business processes and workflows. 