Levels of Abstraction
* application software
  * data structures
* system software
  * virtual memory, heap/stack
* architecture
  * cache, main memory
* circuits
  * DRM, SRAM, ROM/RAM, volatile/non-volatile
* devices
  * charge, spin, crystal formation
 
Faster access / density of disk 

Logical Memory Types
* logically memory divided into instruction and data memory
  * embedded systems often have much more instruction memory than data memory
  
Physical Memory Types
* for embedded systems code generally executed from non-volatile memory and data are accessed from volatile memory
* non-volatile memory is usually Read-Only Memory (ROM) and/or Flash

General Memory Structure
* memory is an array of cells accessed in two dimensions

Mask Read Only Memory (ROM)
* ROM contents are programmed at the factory by masking connections in the finla metal layer

MASK ROM 
* advantages
  * high density
  * low production cost per device due to small area
  * high performance
  * high reliability
* disadvantages
  * cannot be reprogrammed
  * mask costs implies high volume needed to amoritze cost
 
Flash Memory
* flash memory cell is modified MOSFET transistor
* floating gate (FG) is added between the control gate (CG) and channel
* FG surrounded by insulators
* FG traps electrons
* CG is same as MOSFET gate
* charged FG alters inversion layer in channel

Flash Logic Levels
* flash cell with little or no trapped charge (erased) is a logic level ‘1’
* A flash cell with lots of trapped charge (programmed) is a logic level ‘0’

NOR and NAND flash addressing 
* less contacts --> more compact
* NOR 10x endurance, fast read, user for code
* NAND smaller code size, slow read, used for data files

Flash vs ROM
* advantages
  * reprogrammable
  * cost effective for low volume systems
  * faster time to market
* disadvantages
  * higher unit cost per bit due to more complex cells
  * less reliable (leaks, but retention may be 20 years)
 
Dynamic RAM
* uses one transistor and a trench capacitor to store a bit
* advantages
  * read/write
  * better density/lower cost than Static RAM
* disadvantages
  * slow relative to SRAM
    * reads are destructive, must re-write data
  * charge leaks off of the cap in about 10 ms
    * must be refreshed
  * relatively unreliable
  * susceptible to single event upsets (Transient faults) from alpha particles, electro-magnetic interference
  * problematic for safety critical applications w/o ECC (error correcting codes)

Static RAM
* six transistors (relatively expensive)
* feedback loop ensure stable (static) value
* fast, active output
  * active circuit always consuming energy
  * volatile memory
* relatively immune to faults
* typically used for caches, regsiter files, etc





