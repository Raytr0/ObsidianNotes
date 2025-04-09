# Software-Defined Networking
## 4.1 The limitations of the traditional network architectures
Network requirements are evolving due to the needs around us.
Demand, Supply, and Traffic Patterns being the most important categories of influence.
Traditional Network Architectures are simply inadequate to keep up with the demands.
The **Open Networking Foundation (ONF)** cites four general limitations of traditional network architectures: 
	➢ Static, complex architecture 
	➢ Inconsistent policies 
	➢ Inability to scale 
	➢ Vendor dependence

## 4.2 The key requirements for an SDN architecture
Principal requirements for a modern networking:
	Adaptability
	Automation
	Maintainability
	Model management
	Mobility
	Integrated security
	On-demand scaling

To provide adaptability and scalability, two key technologies are being developed.
SDN and NFV
Software-Defined Networking (SDN) 
	✓Discussed in the subsequent slides 
➢ Network Functions Virtualization (NFV) 
	✓Will be covered in SE4455

### Software-Defined Networking (SDN) 
![[Pasted image 20250408164522.png]]
Two elements are involved in this, 
The Control Function which determines the route and priority
The Data Function which forwards data based on the control function
![[Pasted image 20250408165108.png|500]]
![[Pasted image 20250408165137.png|500]]
Application Plane:
	A variety of applications that may use an abstract view of the network for their decision making goals, these requirements are then communicated to SDN controllers via a northbound API.
		Examples: energy-efficient networking, security monitoring, access control, and network management.
Control Plane:
	SDN controllers can be implemented directly on a server or on a virtual server.
	OpenFlow or other API's are used to control the switches in the data plane.
	SDN controllers also expose northbound APIs, which allow developers and network managers to deploy a wide range of off-the-shelf and custom-built network applications. 
	A number of vendors offer a Representational State Transfer (REST)-based API to provide a programmable interface to their SDN controller.
Data Plane:
	Consists of Physical and Virtual switches responsible for forwarding packets.
	implementation of buffers should be **uniform and open** to SDN controllers.
	OpenFlow is the most prominent example. 

### Characteristics of SDN
Data Plane devices are simple packet forwarding devices since control plane is seperated.
The control plane has a centralized view of the networks under its control.
The controller is portable software that can run on servers and is capable of programming the forwarding devices based on the view of the network.
The network is programmable by applications running in the application plane.

### Standards-Developing Organizations
SDN and NFV do not currently have well defined standards unlike WIFI, the following are the organizations and what they are currently up to regarding developing standards for SDN and NFV
![[Pasted image 20250408171845.png]]

### OpenDaylight
An open source software activity under the guidance of the Linux foundation.
Its member companies provide resources to develop an SDN controller for a wide range of applications
Also supports network programmability via southbound protocols, a bunch of programmable network services, a collection of northbound APIs, and a set of applications

### OpenStack
An open source software project that aims to produce an open source cloud operating system
Provides multitenant Infrastructure as a Service (IaaS) and aims to meet the needs of public and private clouds regardless of size, by being simple to implement and massively scalable
SDN technology is expected to contribute to its networking part, and to make the cloud operating system more efficient, flexible, and reliable

## 4.3 The functions of the SDN data plane
Referred to as the **resource layer** or as the **infrastructure layer**, where network forwarding devices perform the transport and processing of data according to decisions made by the SDN control plane.
These devices preform a simple forwarding function, without embedded software.
the devices are also called data plane network elements, or switches.

![[Pasted image 20250408173315.png]]
**Control support function:** Interacts with the SDN control layer to support programmability via resource control interfaces. The switch communicates with the controller and the controller manages the switch via the **OpenFlow switch protocol.**
**Data forwarding function:** Accepts incoming data flows from other network devices and forwards them along the data forwarding paths that have been computed and established by the **SDN controller** according to the rules defined by the **SDN applications.**

## 4.4 The OpenFlow logical architecture and network protocol
![[Pasted image 20250408174312.png]]
OpenFlow is both a protocol between SDN controllers and network devices and a specification of the logical structure of the network switch functionality.
![[Pasted image 20250408174430.png]]

### The OpenFlow
SDN controller communicates with OpenFlow-compatible switches using the OpenFlow protocol running over Transport Layer Security (TLS).
Each switch connects to other OpenFlow switches and, possibly, to end-user devices that are the sources and destinations of packet flows.
On the switch side, the interface is known as an OpenFlow channel. These connections are via OpenFlow ports. An OpenFlow port also connects the switch to the SDN controller
### OpenFlow Switch Ports
➢ Physical port: Corresponds to a hardware interface of the switch. For example, an Ethernet switch. 
➢ Logical port: Does not correspond directly to a hardware interface of the switch. May be defined in the switch using non-OpenFlow methods (for example, link aggregation groups, tunnels, loopback interfaces) and may map to various physical ports. 
➢ Reserved port: It specifies generic forwarding actions such as sending to and receiving from the controller, flooding, or forwarding using non-OpenFlow methods, such as “normal” switch processing.
### OpenFlow Tables
➢ A flow table: matches incoming packets to a particular flow and specifies what functions are to be performed on the packets. There may be multiple flow tables that operate in a pipeline fashion, as explained subsequently. 
➢ A Group table: a flow table may direct a flow to a group table, which may trigger a variety of actions that affect one or more flows. 
➢ A meter table: consists of meter entries that can trigger a variety of performance-related actions on a flow.
Using the OpenFlow switch protocol, the controller can add, update, and delete flow entries in tables, both **reactively** (in response to packets) and **proactively**.
![[Pasted image 20250408185414.png]]
![[Pasted image 20250408185442.png]]
For Match Fields: ![[Pasted image 20250408185501.png]]
For Counters: ![[Pasted image 20250408185539.png]]
### Packet Flow
If as switch includes more than one tables, they are organized as a pipeline, with the table numbers increasing from 0. The pipeline process allows for much needed flexibility. 
![[Pasted image 20250408185700.png]]
Ingress Processing always happens, beginning with table 0. If there is only one table in the process, then there is no Egress Processing.
Egress processing is the processing that happens after the determination of the output port. It happens in the context of the output port. This stage is optional. If it occurs, it may involve one or more tables.
![[Pasted image 20250408185844.png]]
### Ingress Processing
Cannot forward to another table when process reaches the final table.
When a packet is finally directed to output port, the accumulated action set is executed and then the packet is queued for output.
![[Pasted image 20250408190021.png]]
### Egress Processing
If egress processing is associated with a particular output port, then after a packet is directed to an output port in the ingress process, the packet is directed to the first flow table of the egress pipeline 
There is no group table processing at the end of the egress pipeline.
![[Pasted image 20250408190122.png]]
### The use of multiple tables
The use of multiple tables enables the breaking down of a single flow into a number of parallel subflows.
![[Pasted image 20250408191655.png]]
This simplifies the processing in both the SDN controller and the OpenFlow switch.
Actions such as next hop that apply to the aggregate flow can be defined once by the controller and examined and performed once by the switch. The addition of new subflows at any level involves less setup.
This increases the efficiency of network operations, provides granular control and allows the network to react to real time changes.
### The Group Tables
Group identifier: A 32-bit unsigned integer uniquely identifying the group. A group is defined as an entry in the group table. 
Group type: Determines group semantics, explained in the next slide. 
Counters: Updated when packets are processed by a group. 
Action buckets: An ordered list of action buckets, where each action bucket contains a set of actions to execute.
![[Pasted image 20250408203255.png]]
The action list is executed in sequence and generally ends with the Output action, which forwards the packet to a specified port. 
The action list may also end with the Group action, which sends the packet to another group.

### Group Types
A group is designated as all, select, fast Failover, or indirect

All:
	Executes all buckets in a group
	Packet is effectively cloned and put into multiple buckets which each have a different output port.
	![[Pasted image 20250408203417.png]]
Select:
	Executes one bucket in the group, based on a switch-computed selection algorithm.
	The selection algorithm should implement equal load sharing or, optionally, load sharing based on bucket weights assigned by the SDN controller.
	![[Pasted image 20250408203510.png]]
Fast Failover:
	Executes the first live bucket.
	Buckets are evaluated in order and the first live bucket is selected.
	Allows switch to change without needing a round trip to the controller.
	![[Pasted image 20250408203654.png]]
Indirect:
	Allows multiple packet flows (that is, multiple flow table entries) to point to a common group identifier.
	Allows for more efficient management by the controller in certain situations.
	![[Pasted image 20250408203737.png]]

### OpenFlow Protocol
The OpenFlow protocol describes message exchanges that take place between an OpenFlow controller and an OpenFlow switch.
This is typically preformed on top of TLS, providing a secure OpenFlow channel.
This enables the controller to preform add, update, and delete actions to the flow entries in the flow tables.
It supports 3 types of messages: Controller to switch, Asynchronous, Symmetric.
![[Pasted image 20250408205345.png]]
## 4.5 The functions of the SDN control plane
### SDN control plane architecture
The SDN control layer maps application layer service requests into specific commands and directives to data plane switches and supplies applications with information about data plane topology and activity.
The control layer is implemented as a **server** or cooperating **set of servers** known as SDN controllers.
![[Pasted image 20250408205741.png]]
### SDN controller functions
Shortest path forwarding: Uses routing information collected from switches to establish preferred routes.
Notification manager: Receives, processes, and forwards an application events, such as alarm notifications, security alerts, and state changes.
Security mechanisms: Provides isolation and security enforcement between applications and services.
Topology manager: Builds and maintains switch interconnection topology information. 
Statistics manager: Collects data on traffic through the switches.
Device manager: Configures switch parameters and attributes and manages flow tables entries
### Network Operating System (NOS)
The functionality provided by the SDN controller can be viewed as a network operating system (NOS)
The functions of an SDN NOS enable developers to define network policies and manage networks without concern for the details of the network device characteristics
**Northbound interfaces** enable developers to create software that is independent not only of data plane details but to a variety of SDN controller servers.
### SDN controller implementations
❑ OpenDaylight: An open source platform for network programmability to enable SDN, written in Java. OpenDaylight was founded by Cisco and IBM.
❑ Floodlight: An open source package developed by Big Switch Networks. Both a web-based and Java based GUI are available and most of its functionality is exposed through a REST API.
❑ Open Network Operating System (ONOS): An open source SDN NOS, a nonprofit effort funded and developed by a number of carriers, such as AT&T and NTT, and other service providers and supported by the Open Networking Foundation.
❑ Ryu: An open source component-based SDN framework developed by NTT Labs. Developed in python.
❑ POX: An open source OpenFlow controller that has been implemented by a number of SDN developers and engineers. POX has a well written API and documentation. It also provides a web-based graphical user interface (GUI) and is written in Python.
❑ Beacon: An open source package developed at Stanford. Written in Java. Beacon was the first controller that made it possible for beginner programmers to work with and create a working SDN environment.
❑ Onix: Commercially available SDN controller, developed by VMWare, Google, and NTT. 
### SDN Controller Interfaces
The **southbound interface** provides the logical connection between the SDN controller and the data plane switches.
The most commonly implemented southbound API is OpenFlow.
The southbound interfaces include:
	Open vSwitch Database Management Protocol (OVSDB): an open source software project which implements virtual switching.
	Forwarding and Control Element Separation (ForCES): An IETF effort that standardizes the interface between the control plane and the data plane for IP routers.

The **northbound interface** enables applications to access control plane functions and services without needing to know the details of the underlying network switches.
The northbound interface is more viewed as a software API rather than a protocol.
	➢ Base controller function APIs: These APIs expose the basic functions of the controller and are used by developers to create network services.
	➢ Network service APIs: These APIs expose network services to the north. For example, Firewalls, Routings, and Optimizations.
	➢ Northbound interface application APIs: These APIs expose application-related services that are built on top of network services. For Example, security-related services.
![[Pasted image 20250408214401.png]]
### SDN Controller - Routing
Traditionally, the routing function is distributed among the routers in a network.
In an SDN-controlled network, the controller provides a centralized routing that can develop a consistent view of the network state to calculate shortest paths
❑ Link discovery
	➢ The routing function needs to be aware of links between data plane switches
	➢ Must be performed between a router and a host system and between a router in the domain of this and a router in a neighboring domain
	➢ Discovery is triggered by unknown traffic entering the controller’s network domain either from an attached host or from a neighboring router
❑ Topology manager
	➢ Maintains the topology information for the network and calculates routes in the network
	➢ Route calculation involves determining the shortest path between two data plane nodes or between a data plane node and a host
## 4.6 An overview of OpenDaylight and REST APIs
The high-level SDN architecture
![[Pasted image 20250408220331.png]]
The OpenDaylight architecture
![[Pasted image 20250408220341.png]]
Service Abstraction Layer Model
![[Pasted image 20250408220426.png]]
### OpenDaylight - the Helium release
❑ The controller platform (exclusive of applications, which may also run on the controller) consists of a growing collection of
dynamically pluggable modules, each of which performs one or more SDN-related functions and services.
❑ Five modules are considered base network service functions:
➢ Topology manager: A service for learning the network layout by subscribing to events of node addition and removal and their interconnection. Applications requiring network view can use this service.
➢ Statistics manager: Collects switch-related statistics, including flow statistics, node connector, and queue occupancy.
➢ Switch manager: Holds the details of the data plane devices. As a switch is discovered, its attributes (for example, what switch/router it is, software version, capabilities) are stored in a database by the switch manager.
➢ Forwarding rules manager: Installs routes and tracks next-hop information. Works in conjunction with switch manager and topology manager to register and maintain network flow state. Applications using this need not have visibility of network device specifics.
➢ Host tracker: Tracks and maintains information about connected hosts.
### REpresentational State Transfer (REST)
Become a standard way of contructing northbound APIs for SDN controller
![[Pasted image 20250408221246.png]]
### 1. Client-Server
This dictates that the interaction between client-server is request/response type
This separation allows client and server components to evolve independently and supports the portability of server-side functions to multiple platforms
### 2. Stateless
Dictates that each request from a client to a server must contain all the information necessary to understand the request and cannot take advantage of any stored context on the server
Similarly, each response from the server must contain all the desired information for that request
REST typically runs over Hypertext Transfer Protocol (HTTP), which is a stateless protocol
### 3. Cache
Requires that the data within a response to a request be implicitly or explicitly labeled as cacheable or non-cacheable.
### 4. Uniform interface
To obtain a uniform interface, REST defines four interface constraints:
➢ Identification of resources
➢ Manipulation of resources through representations
➢ Self-descriptive messages
➢ Hypermedia as the engine of the application state
When the interface is uniform, different applications can invoke the same controller service via REST APIs
### 5. Layered System
A given function is organized in layers, with each layer only having direct interaction with the layers immediately above and below
This is just standard architecture approach
### 6. Code on demand
REST allows client functionality to be extended by downloading and executing code in the form of applets or scripts.
This simplifies clients by reducing the number of features required to be preimplemented. 
Allowing features to be downloaded after deployment improves system extensibility.
### API functions for switches
![[Pasted image 20250408221942.png]]
![[Pasted image 20250408222016.png]]
## 4.7 An overview of the SDN application plane architecture
![[Pasted image 20250408222107.png]]
### Northbound Interface
Enables applications to access control plane functions and services without needing to know the details of the underlying network switches, this provides an abstract view of network resources controlled by the software in the SDN control plane

# Read the rest of slides too much images.