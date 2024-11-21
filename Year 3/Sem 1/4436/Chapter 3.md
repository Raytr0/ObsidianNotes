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

Connection-oriented demultiplexing:
TCP socket identified by 4-tuple: 
	• source IP address 
	• source port number 
	• dest IP address 
	• dest port number
Server may support many TCP simultaneously
demux: receiver uses all 4 values to direct segment

![[Pasted image 20241119125809.png|500]]

UDP: demultiplexing using destination port number (only) 
TCP: demultiplexing using 4-tuple: source and destination IP addresses, and port numbers

### Connectionless transport: UDP
UDP is "best effort", segments may be lost or delivered out-of-order
connectionless: no handshaking between UDP sender, receiver
![[Pasted image 20241119151451.png|300]]
UDP Sender Actions: is passed an application-layer message -> determines UDP segment header fields values -> creates UDP segment -> passes to IP
UDP receiver actions: receives segment from IP -> checks UDP checksum header value -> extracts application-layer message -> demultiplexes message up to application via socket
![[Pasted image 20241119222919.png|300]]
UDP checksum: compute checksum of received segment, if not equal then error, if equal then ok
there are edge cases to this
![[Pasted image 20241119223116.png|500]]

### Principles of reliable data transfer(rdt)
![[Pasted image 20241120000551.png|500]]
rdt1.0: reliable transfer over a reliable channel
	no bit errors
	no packet loss
	***Seperate*** FSMs for sender and receiver
![[Pasted image 20241120000830.png]]
rdt2.0: channel with bit errors
	underlying channel may flip bits in packet, use checksum to detect bit errors
	How to fix errors?
		Acknowledgements (ACKs): receiver explicitly tells sender that ptk received OK
		Negative ACKs (NAKs): receiver explicitly tells sender that pkt had errors
	sender retransmits pkt on receipt of NAK
	stop and wait, sender sends 1 packet, waits for reciever response
![[Pasted image 20241120001123.png]]
rdt2.1: handling garbled ACK/NAKs
	Sender:
	![[Pasted image 20241120001311.png|500]]
	Receiver:
	![[Pasted image 20241120001327.png|500]]
rdt2.2: NAK-free protocol
	Same thing as 2.1 but only ACKs
	receiver sends ACK for last pkt received OK
		Must explicitly include seq # of pkt being ACKed
	duplicate ACK at sender results in same action as NAK, retransmit current pkt
	![[Pasted image 20241120001623.png]]
rdt3.0: channels with errors and loss
	New channel assumption: underlying channel can also lose packets
	Basically includes a time to wait a reasonable time to wait for ACK
	and does previous ver actions if time expires
	![[Pasted image 20241120001820.png]]![[Pasted image 20241120001827.png]]
	Performance:![[Pasted image 20241120011529.png]]![[Pasted image 20241120011540.png]]
	pipelined protocols operation can be used to improve performance, allowing for multiple "in-flight" packets
	![[Pasted image 20241120011650.png]]
Go-Back-N:
![[Pasted image 20241120012014.png]]
Selective repeat:![[Pasted image 20241120012027.png]]

### Connection-oriented transport: TCP
TCP segment structure![[Pasted image 20241120012118.png]]
![[Pasted image 20241120012209.png]]
How to set TCP timeout value?
	longer than RTT, but RTT varies, too short causes premature timeout, too long means slow reaction to segment loss
How to estimate RTT?
	SampleRTT: measured time from segment transmission until ACK rexeipt
	Want the average of several recent measurements, not just one
TCP round trip time, timeout
	**EstimatedRTT = (1- a)\*EstimatedRTT + a\*SampleRTT (where a = 0.125)**
	**TimeoutInterval = EstimatedRTT + 4\*DevRTT (Where DevRTT is a "safety margin")**
	**DevRTT = (1-b)\*DevRTT + b\*|SampleRTT-EstimatedRTT| (Where b = 0.25)**

TCP Sender:
	event: data received from application
		create segment with seq #, which is the byte-stream number of first data byte in segment
		start timer
	event: timeout
		retransmit segment that caused timeout and restart timer
	event: ACK received
		if ACK acknowledges previously unACKed segments
		update known ACKed
		start timer if unACKed segments'
Retransmission scenarios:
![[Pasted image 20241120013116.png|500]]![[Pasted image 20241120013136.png]]![[Pasted image 20241120015450.png]]

TCP flow control:
sender too fast for receiver
	receiver controls sender, so sender won’t overflow receiver’s buffer by transmitting too much, too fast
	Receiver advertises free buffer space in rwnd field in TCP header
		RcvBuffer size default is 4096 bytes
		many OS autoadjust RcvBuffer
	Sender limits amount of unACKed data to received rwnd
	guarantees no overflow

Closing TCP Connection:
client, server each close their side of connection 
	send TCP segment with FIN bit = 1 
respond to received FIN with ACK 
	on receiving FIN, ACK can be combined with own FIN 
simultaneous FIN exchanges can be handled

### Principles of congestion control
too many senders, sending too fast
Scenario 1:
![[Pasted image 20241120020436.png]]
Scenario 2:
Same setup, but finite buffers
buffer now fills up and packets are lost
![[Pasted image 20241120020538.png]]
Scenario 3:
![[Pasted image 20241120020637.png]]
dropped packet: any upstream transmission capacity and buffering used for packet is wasted 
![[Pasted image 20241120020742.png]]

### TCP congestion control: AIMD
senders increase sending rate until packet loss occurs, then decrease sending rate on loss![[Pasted image 20241120020858.png]]
![[Pasted image 20241120022928.png]]
TCP slow start:
Exponential increase until rate loss event occurs
initial cwnd = 1, double cwnd every RTT

TCP CUBIC:
![[Pasted image 20241120113810.png]]
Initiall reaches Wmax faster, but approaches Wmax more slowly
Default in Linux, most popular for TCP and Web servers

There is going to exist a congested bottleneck for TCP
### Delay-based TCP congestion control
congestion control without inducing/forcing loss
![[Pasted image 20241120114744.png]]

TCP fairness:
