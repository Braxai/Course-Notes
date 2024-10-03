```
fn foo() {
  char buf[8];
  gets(buf);
}
int main() {
  foo();
}
```
if 8 characters entered on standard input when gets is called it will overflow buf (9 characters counting terminating character)

Return Instruction Pointer (rip) pushed on to stack when foo() called
Stack Frame Pointer (sfp) pushed on to stack 
Allocate space for buf (local variables)
Move esp to below buf
Push buf pointer on to stack because buf is used as argument in gets
  char buf[8] equivalent to char *buf (it's a pointer)
rip and sfp for get() pushed 
pop values back up the stack

- Attacker can put malicious code in buf and the address of buf in place of foo() rip
`- As a result of this type of attack, we now enforce "no executable stacks"


### Return-to-libc Attack
foo.c -- cpp --> foo.i -- as (assembler) --> foo.s -- ld --> a.out
- cpp expands macros (#include x)
- as assembler converts to machine language
- ld combine assembly instruction with library
  - links glibc.a or glibc.so
    - dangerous functions in glibc
      - execv(cmd, ...) --> execute new executable in current process
        - dangerous because you can execute programs in hard drive and not in memory
          - can run shell to get access to running commands
buffer overflow used to put address in stack that will lead to calling execv and opening shell
shellcode : common name for malicious payload

Stack Guard
- prevent return-to-libc by marking end of buf (canary), we can validate that the canary is still valid before returning
  - if not then we know there was a buffer overflow attack
  - mark should be placed below rip so the attacker must override the mark to override rip
    - callee places and checks canary (ensures below rip and checked before returning/running malicious code)
    - compiler generates code to create and place canary
