x86 Overview
```
int g = 0;
int foo(int a, int b) {
  int c;
  char*p=malloc(...);
  bar(a,b,c,p);
}
```
compile-time = static-time : run-time = dynamic-time

Memory linear array of byes from 0x0...0 to 0xF...F
- 1 row = 1 word = 4 bytes
- can't store all variables one on top of the other because different kindsof variables have different lifetimes
  - global, local, dynamically allocated must be stored at different times
    - global can be stored at compile time
    - local will be present at different times in run-time (recursion prevents us from knowing exactly how much space is needed)
    - dynamically allocated can break if it involves user input or is in a loop

dynamic vs local characteristics that cause them to be stored in different parts of memory 
- dynamic occurs on malloc and leaves on free
  - occur and disappear in arbitrary order throughout program
- local occurs on function entry and leaves when function finished
  - can not be time when local variables of callee exist but the caller's do not
    - caller local variable lifetime > callee local variable lifetime

size of memory no longer an issue
Organization : 
- code stored at the lowest address space
  - kernel stored below the code
- data stored above the code
  - constants and static variables above code
  - heap : dynamically allocated data stored from above static section moving up
  - stack : local variables and function call information from top of address space down
    - LIFO works perfect for the caller callee local function variable conditions
    - stack never has holes in it whereas heap can (memory fragmentation : still a problem)
 