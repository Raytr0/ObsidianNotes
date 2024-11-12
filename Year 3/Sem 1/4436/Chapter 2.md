Client-Server paradigm
Peer-peer architecture
Process communicating
Sockets
Addressing processes
	Ip address is an identifier + port number

## Application Layer Protocol
	![[Pasted image 20240923125546.png||400]]
## Application Transport Service Requirements
Data Integrity
	File transfer apps
Timing
	Low ping
Throughput
	bandwidth basically
Security
	encryption
![[Pasted image 20240923125746.png|400]]
## Internet Transport Protocol Services
	TCP Service:
		Provides:
			Reliable Transport
			Flow Control
			Congestion Control
			Connection Oriented
		Does not provide:
			Timing 
			Minimum throughput guarantee
			Security
	UDP Service:
		Unreliable Data Transfer
		does not provide: reliability, flow control, congestion control, timing, throughput guarantee, security, or connection setup.
	![[Pasted image 20240923130207.png|400]]
## Securing TCP
Vanilla TCP & UDP sockets:
	No encryption
	everything is in cleartext
Transport Layer Security:
	Encrypted TCP connections
	end-point auth

## Web and HTTP
Overview:
	HTTP: hypertext transfer protocol
	HTTP request and response
	Uses TCP:
		Client starts TCP connection to server, port 80
		Server accepts TCP connection
		HTTP messages exchanged
		TCP connection closed
	HTTP is stateless, does not maintain information about past client requests
HTTP connections:
	Non-persistent HTTP:
		TCP connection opened
		At most sends one object
		TCP connection closed
		(Every time a file needs to be sent, entire process is replicated depending on how many objects)
		![[Pasted image 20240923131646.png|400]]
		Flaws:
		Requires 2 RTT per object
		OS overhead for each TCP connection
		HTTP 1.1 fixes these issues
	Persistent HTTP(HTTP 1.1):
		TCP connection opened
		multiple objects sent over single TCP connection
		TCP connection closed
		Improvements:
			Server leaves connection open after sending response
			HTTP messages can continuously be sent over same connection
			Client sends requests as soon as it encounters a referenced object 
			As little as one RTT for all the referenced objects (cutting response time in half)
HTTP Request Message:
	ASCII (Human readable):![[Pasted image 20240923132239.png]]![[Pasted image 20240923132303.png|400]]
Other Request Message Types:
	POST:
	GET:
	HEAD:
	PUT:
Status Codes:
	200 OK
	301 Moved Permanently
	400 Bad Request
	404 Not Found
	505 HTTP Version Not Supported

## Cookies
Steps:
	1) cookie header line of HTTP response message 
	2) cookie header line in next HTTP request message 
	3) cookie file kept on user’s host, managed by user’s browser 
	4) back-end database at Web site
## Web Caches
Proxys
![[Pasted image 20240924224836.png|500]]
![[Pasted image 20240924224852.png|500]]
![[Pasted image 20240924224909.png|500]]


## HTTP/2
improved from HTTP 1.1
![[Pasted image 20240924225226.png|500]]
![[Pasted image 20240924225238.png|500]]
	
## Email
Mail Servers:
	Mailbox
	Message queue
	SMTP Protocol:
		Client: sending mail server
		"Server": receiving mail server
Uses TCP to reliably transfer email messages, uses port 25
Messages must be in 7-bit ASCII

SMTP vs HTTP:
HTTP: Pull
SMTP: Push
	SMTP uses persistent connections
	SMTP requires message (header & body) to be in 7-bit ASCII
	SMTP server uses CRLF.CRLF to determine end of message

## DNS (Domain Name System)
DNS services:
	hostname to IP address translation
	host aliasing:
		canonical, alias names
	mail server aliasing
	load distribution:
		replicated Web servers: many IP addresses correspond to one name
	![[Pasted image 20240923135553.png]]
Root Name Servers:
Official, contact-of-last-resort by name servers that can not resolve name
Critical infrastructure!
![[Pasted image 20240923135700.png|400]]
TLD authoritative servers:
	Top-Level Domain Servers:
		responsible for .com, .org, .net, .edu, .aero, .jobs, .museums, and all top-level country domains, e.g.: .cn, .uk, .fr, .ca, .jp
	Authoritative DNS Servers:
		Organization's own DNS servers
Local DNS name servers:
	Doesnt strictly belong in hierarchy
	each ISP has one
	when host makes DNS query, it is sent to local DNS server
![[Pasted image 20240923135950.png|500]]
![[Pasted image 20240923140233.png|500]]
## P2P Applications
Architecture:
	no always-on server
	arbitrary end systems directly communicate
File distribution:
	Q: how much time to distribute file (size F) from one server to N peers?
	![[Pasted image 20240924123838.png|500]]
	![[Pasted image 20240924124344.png|500]]
	![[Pasted image 20240924125116.png|500]]
Bit torrent explanation slides:

## Video Streaming and CDNs
Video:
	sequence of images displayed in a constant rate (fps)
	pixels represented by bits
	use redundancy within and between images to decrease # bits used to encode image:
		spatial (within image)
		temporal (from one image to next)