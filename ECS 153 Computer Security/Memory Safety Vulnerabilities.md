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
printf example : 
- if printf asks for three arguments using %d but is only given two the C compiler will not catch this mistake
- in the case of a mismatch printf will fetch data from that stack that doesn't belong to the function call

- %d → Print value located at the expected address
- %s → Treat the argument as an address and print the string at that address up until the first null byte
- %n → Treat the argument as an address and write the number of characters that have been printed so far to that address
- %c → Treat the argument as a value and print it out as a character
- %x → Look at the stack and read the first variable after the format string
- %[b]u → Print out [b] bytes starting from the argument

If a program has a format string vulnerability, assume the attacker can learn any value stored in memory and can take control of the program

### 3.4 Integer conversion vulnerabilities
``` 
char buf[8];
void vulnerable() {
    int len = read_int_from_network();
    char *p = read_string_from_network();
    if (len > 8) {
        error("length too large: bad dog, no cookie for you!");
        return;
    }
    memcpy(buf, p, len);
}
```
function definitions for memcpy() and sizez_t are
```
void *memcpy(void *dest, const void *src, size_t n);
typedef unsigned int size_t;
```
if the attacker provides a negative value for len, the if statement won't notice anything wrong and memcpy() will be executed with a negative third argument. C will cast the negative value to an unsigned int and it will become a very large positive integer meaning memcpy() will copy a huge amount of memory into buf and overflow the buffer.

```
void vulnerable() {
    size_t len;
    char *buf;

    len = read_int_from_network();
    buf = malloc(len+5);
    read(fd, buf, len);
    ...
}
```
len+5 can wrap around if len is too large
- if len = 0xFFFFFFFF then value of len+5 is 4 (on 32-bit platform), allocates 4-byte buffer and then writes a lot more into it

### 3.5 Off-by-one vulnerabilities
<= instead of <, loop starting at i=0 instead of i=0 etc. 

Consider buffer with bound checks off by one. We cn write n+1 bytes into buffer of size n, overflowing the byte immediately after the buffer but that is enough to execute instructions at an arbitrary address in memory

![image](https://github.com/user-attachments/assets/8970a385-20a2-4621-b5b2-9e5ad576e018)
1. normal execution
2. overwrite all of buff plus byte immediately after buff (least significant byte of sfp), change sfp so that sfp points to somewhere inside buff. After function executes it calls move, pop, and pop according to the next 3 steps
3. mov %ebp, %esp: esp now points where ebp is pointing, which is the forged sfp
4. pop %ebp: Take the next value on the stack, the forged sfp, and place it in the ebp register. Now ebp is pointing inside the buffer
5. pop %eip: Take the next value on the stack, the rip, and place it in the eip register. Since we didn’t maliciously change the rip, the old eip is correctly restored.

![image](https://github.com/user-attachments/assets/a3c51576-ba81-48c9-85e7-959264888947)

ebp now point sinside the buffer, if a second function return happens, it allows the execution of the instructions at an arbitrary location

6. mov %ebp, %esp: esp now points where ebp is pointing, which is inside the buffer.
7. pop %ebp: Take the next value on the stack (which the program thinks is the sfp, but is actually some attacker-controlled value inside the buffer), and place it in the ebp register.
8. pop %eip: Take the next value on the stack (which the program thinks is the rip, but is actually some attacker-controlled value inside the buffer), and place it in the eip register.

### 3.6 Other memory safety vulnerabilities
