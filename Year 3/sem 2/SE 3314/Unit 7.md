# Internet of Things
![[Pasted image 20250409194812.png]]
ANY physical object that contains a microcontroller, sensor, and means of communicating via the internet can be a collection as a network of things
![[Pasted image 20250409194928.png]]
### Components of Io-Enabled Things
A device may have one or more of the other ingredients
➢ Sensors
➢Actuators
➢A microcontroller
➢A means of communication (transceiver)
➢A means of identification
### Sensor
❑ Active mode:
	❑ Sensor sending sensor data to the controller, either periodically or when a defined threshold is crossed
❑ Passive Mode
	❑ Provides data when requested by the controller. 
![[Pasted image 20250409195718.png]]
![[Pasted image 20250409195726.png]]
❑ Accuracy: ➢ Refers to how close a measurement comes to the truth 
❑ Precision: ➢ Refers to how close multiple measurements of the same physical quantity are to each other.
![[Pasted image 20250409195827.png]]
### Actuators
An actuator receives an electronic signal from a controller and responds by interacting with its environment to produce an effect on some parameter of a physical, chemical, or biological entity
![[Pasted image 20250409200243.png]]
### Embedded systems
![[Pasted image 20250409200545.png]]
### Application Processors versus Dedicated Processors
Application processors are defined by the processor’s ability to execute complex operating systems
	➢ Thus, the application processor is general-purpose in nature
	➢ A good example of the use of an embedded application processor is the smartphone
A dedicated processor is dedicated to one or a small number of specific tasks required by the host device 
	➢ Because such an embedded system is dedicated to a specific task or tasks, the processor and associated components can be engineered to reduce size and cost
### Identification
An important requirement in IOT elements
It is the proof of identity for each object in the IOT world
Means of identification:
➢RFID
	Uses radio waves to identify
➢Barcode
➢IP addressing
➢Electronic Product Codes
### IoT Architecture
Given the complexity of IoT, it is useful to have an architecture that specifies the main elements and their interrelationship
### The ITU -IoT Reference model
The IoT is in fact not a network of physical things: it is a network of devices that interact with physical things, together with application platforms, that interact with these devices
![[Pasted image 20250409201908.png]]
![[Pasted image 20250409201924.png]]
![[Pasted image 20250409201948.png]]
![[Pasted image 20250409201933.png]]
### The World Forum Reference Model
❑ A useful complement to the ITU-T model. It is concerned with the broader issue of
developing applications, middleware and support functions of enterprise based IoT.
❑ Simplifies: It helps break down complex systems so that each part is more
understandable.
❑ Clarifies: It provides additional information to precisely identify levels of the IoT and
to establish common terminology.
❑ Identifies: It identifies where specific types of processing is optimized across different
parts of the system.
❑ Standardizes: It provides a first step in enabling vendors to create IoT products that
work with each other.
❑ Organizes: It makes the IoT real and approachable, instead of simply conceptual.
![[Pasted image 20250409202011.png]]
### Fog Computing
![[Pasted image 20250409202026.png]]
![[Pasted image 20250409202032.png]]
### Data Accumulation Level
❑Data moving through a network is referred to as data in motion
✓The rate and organization of the data in motion is determined by the devices generating the data
✓Data generation is event driven, either periodically or by an event in the environment
✓To capture the data and deal with it in some fashion, it is necessary to respond in real time
❑Data at rest is data in some readily accessible storage facility
✓Applications can access the data as needed, on a non-real-time basis
### Data Abstraction Level
❑ The data abstraction level can aggregate and format the data from the data
accumulation level in ways that make access by applications more manageable and
efficient
❑ This could include:
➢ Combining data from multiple sources
➢ Performing necessary conversions to provide consistent semantics of data across sources
➢ Placing formatted data in appropriate database
➢ Alerting higher-level applications that data is complete or had accumulated to a defined threshold
➢ Consolidating data into one place or providing access to multiple data stores through data virtualization
➢ Protecting data with appropriate authentication and authorization
➢ Normalizing or denormalizing and indexing data to provide fast application access
### Application Level
![[Pasted image 20250409202123.png]]
### Collaboration and Processes Level
This level recognizes the fact that people must be able to communicate and collaborate to make an IoT useful This may involve multiple applications and exchange of data and control information across the Internet or an enterprise network
![[Pasted image 20250409202141.png]]
