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



