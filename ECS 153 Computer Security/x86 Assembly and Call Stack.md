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
- ex: storing 0x44332211 in memory
![image](https://github.com/user-attachments/assets/a59ade3d-ea99-4c2d-8d66-effb56b7d71e)

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
When function called, stack allocates extra space to store local variables nad other information relevant to the function 
- stack grows down so the space is at lower addresses in memory
- once funciotn returns, the space on the stack is freed up for future function calls
function caller calls callee, program execution starts in caller, moves to callee, and then returns to caller
- eip changed to point to instrucitons of callee
- ebp and esp updated to point to top and bottom of the new stack frame
  - save old values when function called so we can restore after function returns 

11 steps to calling an x86 function and returning
1. push arguments onto the stack ( pushed in reverse order )
2. push old eip (rip : return instruction pointer) on the stack
3. move eip to point to instructions of callee function
4. push old ebp (sfp : saved frame pointer) on stack
5. move ebp down
  - point to top of new stack frame
6. move esp down
  - allocate space for new stack frame, amount determined by complexity of the function
7. execute the function
  - local variables and any other necessary data saved in new stack frame
8. move esp up ( function ready to return )
9. restore old ebp (sfp)
10. restore old eip (rip)
11. remove arugments from the stack (increment esp)
    - no need to save old esp because it automatically moves to the bottom of the stack as we push values and returns to its old position as we remove values from the stack

### 2.9 x86 function call in assembly 
```
int main(void) {
    foo(1, 2);
}
void foo(int a, int b) {
    int bar[4];
}
```

becomes 

```
main:
    # Step 1. Push arguments on the stack in reverse order
    push $2
    push $1

    # Steps 2-3. Save old eip (rip) on the stack and change eip
    call foo

    # Execution changes to foo now. After returning from foo:

    # Step 11: Remove arguments from stack
    add $8, %esp

foo:
    # Step 4. Push old ebp (sfp) on the stack
    push %ebp

    # Step 5. Move ebp down to esp
    mov %esp, %ebp

    # Step 6. Move esp down
    sub $16, %esp

    # Step 7. Execute the function (omitted here)

    # Step 8. Move esp
    mov %ebp, %esp

    # Step 9. Restore old ebp (sfp)
    pop %ebp

    # Step 10. Restore old eip (rip)
    pop %eip
```

steps 8/9 can be abbreviated as leave instruciton 
step 10 can be abbreviated as ret instruction 
- can write "leave ret" for each function

4-6 called function prologue
8-10 called funciton epilogue
