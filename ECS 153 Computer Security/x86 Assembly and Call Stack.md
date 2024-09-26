### 2.1 Number representation 
- 1 nibble = 4 bits
- 1 byte = 8 bits
- 1 word = 32 bits (on 32-bit architectures)
word : size of a pointer that depends on CPU architecture
Binary	Hexadecimal	Binary	Hexadecimal
0000	  0	          1000	  8
0001	  1	          1001	  9
0010	  2	          1010	  A
0011	  3	          1011	  B
0100	  4	          1100	  C
0101	  5	          1101	  D
0110	  6	          1110	  E
0111  	7	          1111	  F
0b before binary strings
0x before hexadecimal strings

### 2.2 Compiler, Assembler, Linker, Loader (CALL)
Four steps to run a C program
1. compiler translates C into assembly
2. assembler translates assembly into machine code
3. linker resolves dependencies on external libraries and outputs a binary executable of the program
4. loader sets up address space in memory and runs machine code instructions in executable when the user runs it

### 2.3 C memory layout 
OS gives program address space to store any state necessary for program execution at runtime
- 32 bit system has memory addreses 32 bits long so the address space has 2<sup>32</sup> bytes of memory
  - leftmost element has address 0x00000000
  - rightmost element has address 0xFFFFFFFF
![image](https://github.com/user-attachments/assets/33d58e0d-2b27-4f73-a418-1e331456f7f6)

Address space divided into four sections (from low to high address) when program is being run
1. code section : executable instructions of the program
2. static section : constants and static variables
3. heap : dynamically allocated data
4. stack : local variables and other information associated with function calls
![image](https://github.com/user-attachments/assets/8ae92336-12f4-4a8b-a437-92424577eceb)

### 2.4 Little-endian words
little-endian : when storing a word in memory, the least significant byte is stored at the lowest address and the most significant at the highest address
- ex: storing 0x44332211 in memory ![image](https://github.com/user-attachments/assets/a59ade3d-ea99-4c2d-8d66-effb56b7d71e)
big-endian : least signifcant byte at highest address (networking protocols often big-endian)

using words on diagrams lets us abstract away little-endianness when working with memor diagrams but bytes are still being stored in little-endian

### 2.5 Registers
Registers : store memory directly on CPU
- each register stores one word
- no addresses, referred to using names
  - eip : instruction pointer stores address of machine instruction currently being executed
  - ebp : base pointer stores address of the top of the current stack frame
  - esp : stack pointer stores address of the bottom of the current stack frame
  - six other registers : eax, ebx, ecx, edx, esi and edi

### 2.6 Stack: Pushing and popping 
Push: add value to stack by decrementing esp then storing value in the newly allocated space

Pop: remove value from stack by incrementing esp, copies popped value into a register 
- value is not wiped away from memory but esp is incremented so the value is now in undefined memory 

### 2.7 x86 calling convention 
Instructions composed of an opcode and zero or more operands
addl $0x8, %ebx --> pseudocode EBX = EBX + 0x8
- opcode : addl
- operands : $0x8 (source) and %ebx (destination)
registers preceded with %
immediates preceded with $
memory references use () and can have immediate offsets
- 12(%esp) dereferences memory 12 bytes above the addres contained in ESP

### 2.8 x86 function calls 

### 2.9 x86 function call in assembly 

