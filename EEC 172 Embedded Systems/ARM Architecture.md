### ARM Architecture 
RISC : Less complexity, let compiler handle complex operaitons 

ARM is close to a RISC processor but addes some CISC features to support more functionality without paying the cost that CISC does

ARM Overview
* 32/64 bit RISC load-store architecture
* focus : power, code size, performance
  * more complex than MIPS, much smaller code size
  * much less complex than x86, a bit smaller code size
* different variations target different markets
  * performance (smarphones) : Cortex-A
    * 2.5GHz
  * realtime (automotive) : Cortex-R
    * 600 Mhz
  * microcontroller : Cortex-M
    * 200 Mhz

ARM Registers
* 16 registers R0 - R15
* 13 general purpose registers R0 - R12
  * R0 not hardwired to zero like in MIPS
* R13 stack pointer by software convention
* R14 link register
* R15 program counter

Bit Banding : allows direct access to an individul bit with a single instruction 

Address Modes
* ARM has more addressing modes
  * reduces code size and power
  * increases hardare complexity, may increase clock cycle time (CCT)
* Basic mode : immediate offset (only mode in MIPS)
* Immediate Post Indexed
* Register Offset
* Scaled Register Offset
 
Condition Code Flags : ALU instructions can set condition code flags in a status register
* N : NEgative result from ALU flag
* Z : Zero result from ALU flag 
* C : ALU operatopin Carried out
* V : ALU operation oVerflowed

Conditional Execution : faster, smaller code, less energy 

Load/Store Multiple : allows multiple registers to be loaded/stored using a single LDM call

Combined Shift and Op Instructions : can do ALU op with a shifted operand 

ALU Instruciton Format 

![image](https://github.com/user-attachments/assets/cdc2724f-3798-427e-8b75-9f4045879e6d)

Thumb Instruction Set 
* allows 16 bit instructions
 * regions of code either 32 bit (performance) or 16 bit (smaller code)
 * requires mode switch instructions
* Thumb-2 allows intermix of 32 and 16 bit instructions

