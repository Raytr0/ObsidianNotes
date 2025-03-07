# Memory
### Random-access memory (RAM)
A memory unit stores binary information in groups of bits (0’s and 1’s) called words. 
A group of 8 bits is called a byte. 
Multiples of bytes are used in computer memories: 
	•a 16-bit word → two bytes 
	•a 32-bit word → four bytes
![[Pasted image 20250219163125.png]]
k address lines(address bus) specify the particular word chosen
Read and Write respectively transfers binary data in and out of the memory
The capacity of memory is 2k x n bits.
A binary storage cell must be very small (4 to 6 transistors) in order to pack as many cells as possible in the small area available in Integrated Circuits
![[Pasted image 20250219164640.png]]

Types:
1. Static RAM (SRAM) consists essentially of internal latches that store the binary information. • The stored information remains valid as long as power is applied to the unit (Volatile memory). 
2. Dynamic RAM (DRAM) stores the binary information in the form of electric charges on capacitors provided inside the chip by MOS transistors. • The stored charge on the capacitors tends to discharge with time. • The capacitors must be periodically recharged by refreshing the dynamic memory.

### Read Only Memory (ROM)
binary information is permanently stored, even with no power the information stays. This is non-volatile memory
![[Pasted image 20250219165448.png]]
![[Pasted image 20250219170321.png]]
The intersections are programmable to be open or closed circuit
![[Pasted image 20250219204107.png]]
The truth table gives all the information for programming the ROM
0 means no connection 1 means there is a connection

Types of rom:
1. Mask-programmable ROM (PROM)
	Can be programmed or written only once, usually at the factory during the last fabrication process of the unit.
	No updates are possible
2. Programmable read-only memory (PROM)
	all fuses are intact and is altered by blowing up the fuse using a PROM programmer
	once altered it cannot be adjusted
3. Erasable PROM (EPROM)
	EPROM can be erased and rewritten by placing it in intense ultraviolet (UV) light for a given length of time
	Old tech not used much
4. Electrically erasable PROM (EEPROM)
	programmed with electrical signals
	relatively expensive but long lifetimes
	Flash Memory is similar but is easy to customize and adjust without special programming tools, cheaper than EEPROM because erasing and rewriting is in large blocks, does have a shorter lifetime though

### Memory in Harvard Architecture
![[Pasted image 20250219210714.png]]
### Memory in Von-Neumann Architecture
![[Pasted image 20250219210726.png]]
