### 4.1 Use a memory-safe language 
Some modern languages are designed to be intrinsically memory-safe using a combination of compile-time and runtime checks that prevent memory errors from occuring. 
- existance of legacy code in memory-unsafe langauges such as C causes problems

### 4.2 Writing memory-safe code
Carefully reason about memory access in code
- define pre and post conditions for every function
  - use invariants to prove these conditions are satisfied 
  - painstakingly tedious, rarely used in practice
Utilize defensive programming and safe libraries 
  
### 4.3 Building secure software 
Use tools to analyze and patch insecure code 
- run-time checks to do automatic bound-checking
- hire someone to look over code for memory safety errors (expensive but beneficial)
- probe system for vulnerabilities through testing

### 4.4 Exploit mitigations 
Compile and run code with code hardening defneses to make common exploits more difficult 
Mitigations : try to make common exploits harder and cause exploits to crash instead of succeeding (not foolproof) 
- combination of multiple mitigations forces an attacker to discover multiple vulnerabilities in target program 

### 4.5 Mitigation: Non-executable pages 
Write XOR Execute, Data Execution Prevention (DEP), NX bit (no-execute bit) : making some portions of memory non-executable helps defend against buffer overflow exploits 
Each page set to writable or executable but not both
- stops stack smashing

### 4.6 Subverting non-executable pages: Return into libc
Attacker overwrites rip of legitamte function with address of a C library function 
- execv lets attacker start executing instructions of some other executable
  - argument not being run as code so non-executable pages don't stop this attack 

### 4.7 Subverting non-executable pages: Return-oriented programming 
Return-oriented programming : technique that overwrites a chain of return addresses starting at the RIP in order to execute a series of "ROP gadgets" which are equivalent to desired malicious code. 
- constructing custom shellcode using code that already exists in memory
General strategy for executing ROPs is to write a chain of return addresses at the RIP to achieve the desired behavior
- Each return address points to a gadget (small set of assembly instructions that exist in memory and usually end in ret), gadget executes instructions and ret tells code to jump to next address on the stack allowing a jump to the next gadget
ROP so common that non-executable pages are no longer a huge issue for attackers

### 4.8 Mitigation: Stack canaries
Stack Canary : known dummy value placed on stack when a function is called
- when function returns compiler checks that the canary value has not been changed
  - if canary has changed it is evidence an attack is happening and the program will crash before further damage is done
- random value generated at runtime, 1 word long
  - usually contain null byte as first byte to defend against string-based memory safety expoits
- placed directly above local variables and directly below saved registers (sfp and rip)
![image](https://github.com/user-attachments/assets/d34c34ea-f909-4041-9943-496b029c4091)

attacker must overwrite canaray to overwrite rip because they must write to consecutive increasing addresses in memory

### 4.9 Subverting stack canaries 
Stack canaries cant defend against attacks outside of the stack 
Stack canaries don't stop an attacker from overwriting other local variables 
Some exploits write to non-consecutive parts of memory

Techniques to defeat a stack canary
1. Guess the canary
  - time dependent, 64-bit architecture effectively immune to this
2. Leak the canary
  - utilize another vulnerability to leak the value of the canary and utilize it when needed

### 4.10 Mitigation: Pointer authentication 
Pointer Authentication takes advantage of the fact that many addresses are unused in 64-bit architecture 
- CPU replaces unused bits of address on stack with pointer authentication code (PAC), when CPU reads address off stack it checks PAC is unchanged, if it is not the CPU will crash the program
  - attacker needs to know PAC to overwriet rip, if they use an incorrect value the CPU will detect it
  - strengthen this defense by using a different PAC for every pointer stored on the stack
    - deterministic function f(KEY,ADDRESS) takes key and address and outputs a PAC
  
### 4.11 Mitigation: Address Space Layout Randomization (ASLR)
ASLR is a mitigation that tries to make predicting addresses in memory more difficult 
ASLR : each time a progrum runs, the beginning section of memory is randomly chosen
- if the program imports libraries we randomize the starting address of each library's source code 
ASLR causes absolute addresses of variables, saved registers (sfp and rip), and code isntructions to be different each time the program is run
- attacker can no longer overwrite some part of memory with a constant address
Randomizing stack/heap prevents attacker from placing shellcode on the stack/heap without knowing the address of the stack/heap
Randomizing code meansattacker cannot construct an ROP chain or return-to-libc attack without knowing the address of the code

Constraint: segments need to start at page bounrary (starting address of each section will be multiple of page size)

Modern systems can implement ASLR with minimal overhead because they dynamically link libraries at runtime which requires each segment of memory to be relocated

### 4.12 Subverting ASLR
Two methods to subvert ASLR
1. Guess the address
  - less of a problem on 64-bit systems
  - depends on how long each guess takes
2. Leak the address
  - determine the absolute address
  - leaking the absolute address of the sfp enables deducing the address of the rip because the rip will still be 4 bytes above the sfp

### 4.13 Combining Mitigations 
Synergistic Portection: use multiple mitigations together to force the attacker to find multiple vulnerabilities to exploit the program
