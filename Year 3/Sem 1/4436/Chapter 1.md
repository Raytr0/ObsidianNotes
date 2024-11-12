 Host sends packets
		Recieves a application message and breaks into small data called packets, of length ***L*** bits
		Transmits at transmission rate ***R*** .aka bandwidth
	packet transmission delay = time needed to transmit L-bit packet into link = L/R 
	-------------------------------------------------------------------------------------------
	Links: Physical Media
	![[Pasted image 20240910124222.png]]
	![[Pasted image 20240910124233.png]]
	Wireless Radio:
		signal carried in electromagnetc spectrum
		easily obstructed by environmental effects
	Radio Link Types:
		Terrestrial Microwave
			up to 45Mbps
		Wireless LAN(Wifi)
			Up to 100 Mbps
		Wide-area (cellular)
			4G cellular: 10Mbps
		Satellite
			45Mbps per channel
			270ms delay
			geosynchronous vs low-earth-orbit
	---------------------------------------------------------------------------------------------------
	The Network Core
		mesh of interconnected routers
	Packet Switching
		hosts break application layer messages into packets
	Transmission delay
		L/R seconds to transmit L-bit packet to link at R bps
	Store and forward
		entire packet must arrive at router before transmitted to next link
	End-end delay
		L/R, assuming zero propagation delay
	Packet Switching: queuing delay and loss
		If arrival rate > transmission rate:
			packets will queue
			packets will drop if memory fills up
	Network Core functions
		Forwarding:
			local action: moves arriving packets from input link to appropriate output link
		Routing:
			global action: determine source-destination paths taken by packets (routing algorthims)
	Circuit Switching
		![[Pasted image 20240917125319.png|300]]
		dedicated resources: 
			no sharing circuits, guaranteed preformance
			commonly used in traditional telephones
		FDM(Frequency Division Multiplexing):
			optical, electromagnetic frequencies divided into (narrow) frequency bands 
			each call allocated its own band, can transmit at max rate of that narrow band
			![[Pasted image 20240917125916.png|500]]
		TDM(Time Division Multiplexing):
			time divided into slots
			each call allocated periodic slot(s), can transmit at maximum rate of (wider) frequency band, but only during its time slot(s)
			![[Pasted image 20240917125958.png|500]]
		Packet switching vs Circuit switching
			Packet switching allows for more users to use the network
			Packet switching is not the overall winner
				it is great for "bursty" data, when sometimes data is sent and sometimes its idle
				packet delay and loss due to buffer overflow risks exist
		Internet Structure:
		![[Pasted image 20240917130721.png|500]]
		At “center”: small # of well-connected large networks
		“tier-1” commercial ISPs (e.g., Level 3, Sprint, AT&T, NTT), national & international coverage 
		content provider networks (e.g., Google, Facebook): private network that connects its data centers to Internet, often bypassing tier-1, regional ISPs

Read rest of slides 