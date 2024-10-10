```
for a[n];
for( i = 0; i <= n; i++) {
  a[i] = 0;
}
```
Off by one error 

C compiler can inject code to check if it is out of bounds by converting a[i]=0 to 
```
if( i<0 || i >= n) {
  throws Exception
}
a[i] = 0;
```
- Java compiler uses this method
- Overhead applied to every index operation

```
for i,v in a.iter().enumerate() {
  *v = 0
}
```
take mutable pointer to a and iterate over all elements of a 
- denies programmer access to index so they can't make errors
Same efficiency as orignial for loop, both generate same binary code, but no need for bounds checking in compiler

```
array[1]
for v in array:
  print(v)
  array.append(_)
```
Infinite loop
- java detects modifying a collection while iterating over it and throws exception
  - java detects at runtime
```
let mut array = vec![10];
let v in &mut array {
  array.push(_)
}
```
v and array.push try to borrow (take reference) from array causing race condition
- Rust solution : A value may be borrowed by at most one reference mutably or many references immutably 
  - can't have a mix of immutable and mutable references to a value
Borrow Checker : part of Rust compiler that enforces these rules 

Use After Free ( UAF ) : use after freeing from memory 
- attacker can insert values into the space that was freed before it is used again
- java solution : programmer can't free at all
  - more overhead, java implements garbage collection that decides when to free memory
  - stop the world : no threads can move forward before garbage collection finishes running  

Resource Allocation Is Initialization ( RAII ) : Disallow free but let compiler determine when to free it 
- compiler will free variables when they go out of scope because the program can no longer access them
- implemented in C++

```
int *f() {
  int a;
  return &a;
}
int *g=f();
```
Dangling pointer --> no explicit free but implicit free 

Rust solution
```
fn f()-->&'a U32 {
  let v = 1;
  &  v;
}
```
Each value has lifetime
- lifetime of v is lifetime of the function
- U32 is a pointer with lifetime of caller
  - pointer outlives value it points to causing a dangling pointer 
Rust Solution : a reference must not outlive the value it refers to

Rust has thread safety : compiler eliminates most race conditions 
