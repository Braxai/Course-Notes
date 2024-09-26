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

### 2.5 Registers

### 2.6 Stack: Pushing and popping 

### 2.7 x86 calling convention 

### 2.8 x86 function calls 

### 2.9 x86 function call in assembly 

