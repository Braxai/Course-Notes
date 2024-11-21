Password has p bits, System has n users 
- targeted attack : 2<sup>p</sup>
- untargeted attack : 2<sup>p</sup>/n
Salting
- username, salt, h(password||salt)
- untargeted attack : 2<sup>p</sup>
Bitcoin/block chain

Use digital signature to sign transactions
- A --> B --> C
- B : data || h(A)
- C : data || h(b)
- Proof of Work 

Block : data || h(parent) || random number

Three main ideas of Block Chain
1. use private key to represent unique users 
2. use hash functions to validate integrity of block 
3. use secure hash functions to show proof of work
