![[Pasted image 20250219025810.png]]
Main differences: Von Neumann is cheap and simple, Harvard allows for concurrent Instruction and Data memory access, allowing it to me more energy efficient and offer higher processing speeds

### Memory
![[Pasted image 20250219031315.png]]
32-bit processor, memory address has 32 bits, max memory location is limited to 4GB (RAM)
### Registers
![[Pasted image 20250219031451.png]]
R13 can be PSP(process stack pointer: regular user programs) or MSP(main stack pointer: privileged access)
R14 is the link register (LR). It holds the memory address of the instruction that needs to run immediately after a subroutine completes.
R15 is the program counter (PC). It holds the memory address of the next instruction(s) that the processor fetches from the instruction memory.

Special Purpose Register
Program Status Register (PSR) holds status bit flags of the program, interrupt and process execution.
Base priority mask register (BASEPRI) defines the priority threshold. The processor disables all interrupts with a higher priority value then the threshold. A lower priority value represents a higher priority or urgency.
Priority mask register (PRIMASK) is used to disable all interrupts excluding hard faults and non-maskable interrupts.
Fault mask interrupts (FAULTMASK) is used to disable all interrupts excluding non-maskable interrupts.
Control Register (CONTROL) is sets the choice of the main stack or process stack and the selection of privileged or unprivileged mode.

# Binary Calculations