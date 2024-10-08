### Malicious Code Injection Prevention 
- Non executable stacks ( W ^ X ) prevent attacker from writing and executing code in one place
  - Return-to-libc attack : circumvents W^X by attacker using exec function family from standard C library to invoke the shell
- Return-to-libc prevented by placing a canary below rip to detect if malicious code has been injected
- Address Space Layout Randomization ( ASLR ) : when program runs randomize the beginning section of memory to make it harder for attackers to predict or determine addresses in memory
  - Can only be done for code section with compiler support
    - when code compiled into assembly binary code will call a function via it's location
      - can't move code around if using absolute addresses 
    - can't move self referencing data structures around ( pointer will point to wrong address after being moved )
  - Position Independent Code ( PIC ) : code designed so that it can call functions even if they were moved by storing and determining the offset of a function
    - Compiler initiates offset and linker needs to be aware of it
  - Code block kept together but it starts at a random location
  - Randomization should be large so it takes more attempts from attacker to identify changes
    - want to create as much entropy as possible 
Absolute Address : address in virtual memory system you can jump directly too

### Return Oriented Programming
Can return-to-libc be prevented by not giving programs access to standard c libraries if they don't need them?
  - for long time it was assumed this prevented return-to-libc
Attacker has assembly instructions they want to run
  - As attack sequence grows it is more difficult to find exact sequence in program
EX : 
  Attack : x; y;

  Victim Program : x; ret; ... y; ret;
  
  Attacker can overflow buffer and replace rip with location of x, it will then return to that location. Location of the next instruciton ( y ) is placed just above the location of the other so after x returns, esp is popped and points to the value just above x that we want to return to next
  - ret implemented as pop %eax; jmp %eax;

If we have a1, a2, a3, a4 in the victim program which are all a sequence of desired instructions followed by ret attacker will put a1 at rip, then a2 above it, a3 above that and so on
  - Gadget : part of desired attack that are found in victim program and chained together to complete the attack 

Are gadgets hard to find? x86 properties that influence it : 
  - x86 is dense
  - x86 instructions variable length (different instructions have different number of bytes)
    - Alternative Sequence of Instructions : if processor starts in middle of instruction it will reinterpret the instruction sequence
  - x86 data mixed with instructions
    - immediate numbers like jmp destination contain data
      - if you jump into the middle of some data the processor will interpret it as instructions
These properties make it easy to find the desired gadgets
- ROP compilers are able to do this process automatically

In ROP each gadget is analagous to an instruction in a normal program
