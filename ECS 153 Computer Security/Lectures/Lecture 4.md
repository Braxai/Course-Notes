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

Absolute Address : address in virtual memory system you can jump directly too

