### 3.1 Buffer overflow vulnerabilities 
Buffer overflow (buffer overrun) : programmer fails to perform adequate bound checks, triggering an out-of-bounds memory access that write beyond the bounds of some memory region.
```
char buf[8];
void vulnerable() {
    gets(buf);
}
```
-gets() reads as many butes of input as the user suplies and stores them in buf[]
- if the input contains more than 8 bytes of data gets() writes past the end of buf, overwriting another part of memory

Malicious code injection attack : attack finds a way to execute malicious machine instructions allowing them to seize control of the program

### 3.2 Stack smashing
Stack smashing exploits x86 function call convention
```
void vulnerable() {
    char buf[8];
    gets(buf);
}
```
when vulnerable() called, a stack frame is pushed onto the stack

![image](https://github.com/user-attachments/assets/2a37c355-5a19-49dc-8ff0-fa39e1ab1586)

Stack Smashing: if input too long, code will write past buf, overwrite sfp and rip
- used for malicious code injection
  1. attacker arranges to inject malicious code sequence somewhere in the program's address space
  2. attacker provides carefully-chosen input
     - garbage bytes to overwrite whatever is necessary, next bytes to overwrite rip (whatever we overwrite with is the instruction that will be executed next)
  3. when vulnerable returns the proram executes malicious code at address in rip

  ![image](https://github.com/user-attachments/assets/c1687127-2efe-45a8-8f44-d6e4786bed30)

Shellcode : malicious code injected during the stack smashing attack (often written to spawn interctive shell for attacker to perform actions)
- placing shellcode in memory during attack : [shellcode] + [4 bytes of garbage] + [address of buf]

![image](https://github.com/user-attachments/assets/131eb087-5e92-4de8-82f0-d48058a8e9eb)

long shellcode stored as such : [12 bytes of garbage] + [address of rip + 4] + [shellcode]

![image](https://github.com/user-attachments/assets/a6b518f3-baed-43ce-ae65-a314467fe4aa)

Assume every buffer overflow bug is explotable and an attacker can take control of the program.

### 3.3 Format string vulnerabilities

### 3.4 Integer conversion vulnerabilities

### 3.5 Off-by-one vulnerabilities

### 3.6 Other memory safety vulnerabilities
