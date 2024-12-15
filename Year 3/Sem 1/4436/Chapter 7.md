Wireless link characteristics
	▪ decreased signal strength: radio signal attenuates as it propagates through matter (path loss)
	▪ interference from other sources: wireless network frequencies (e.g., 2.4 GHz) shared by many devices (e.g., WiFi, cellular, motors): interference
	▪ multipath propagation: radio signal reflects off objects ground, arriving at destination at slightly different times
	▪ SNR: signal-to-noise ratio 
		• larger SNR – easier to extract signal from noise (a “good thing”)
	▪ SNR versus BER tradeoffs 
		• given physical layer: increase power -> increase SNR->decrease BER 
		• given SNR: choose physical layer that meets BER requirement, giving highest throughput
	![[Pasted image 20241215013623.png]]

### IEEE 802.11 Wireless LAN
![[Pasted image 20241215013659.png]]
![[Pasted image 20241215022507.png]]
Active and Passive Scanning:
![[Pasted image 20241215022635.png]]

802.11 has no collision detection, needs to rely on CSMA/CA which avoid collisions
first transmist small RTS packet to BS using CSMA (very short)
BS broadcasts clear to send CTS in response to RTS
CTS is heard by all nodes and initial requester gets to send packets and other nodes standby

![[Pasted image 20241215023435.png]]

### 802.11: advanced capabilities
Rate Adaptation
power management

### Bluetooth
▪ less than 10 m diameter
▪ replacement for cables (mouse, keyboard, headphones)
▪ ad hoc: no infrastructure
▪ 2.4-2.5 GHz ISM radio band, up to 3 Mbps
▪ master controller / clients devices:
• master polls clients, grants requests for client transmissions
▪ TDM, 625 sec sec. slot
▪ FDM: sender uses 79 frequency channels in known, pseudo-random order slot-to-slot (spread spectrum)
• other devices/equipment not in piconet only interfere in some slots
▪ parked mode: clients can “go to sleep” (park) and later wakeup (to preserve battery)
▪ bootstrapping: nodes self-assemble (plug and play) into piconet
