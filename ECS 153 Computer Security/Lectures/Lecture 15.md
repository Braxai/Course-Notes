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

Web Security

![image](https://github.com/user-attachments/assets/96e566e4-4220-4879-8b35-315485b7028c)

Same Origin Policy ( SOP ) : Java script coming from a website can only talk to the same website of the same origin 

Considered same origin if they have the same 
- protocol
- domain name
- port 
