Cipher Block Chaining Problems 
- must run sequentially
- losing a ciphertext block prevents future blocks from being decrypted

One Time Pad can be used in theory if there are infinite keys of arbitrary length 
- sender and receiver could agree on random number generator seed to create a sequence of keys that match

Good block cipher produces ciphertext that is indistinguishable from random permutations 

Combine one time pad with cbc --> INSECURE 
- OTP : xor message with result of encryption to create the ciphertext
- Block Cipher: each block cipher is close to random permutation
- deterministic, every time we run this system it produces the same "random number"
  - attack: give different m1 and m2 in stage 1, give m1 in stage 2
 
Solution : 
- keep state initialized with IV
  - each time we encrypt a message it generates a random IV block and adds IV to each number  
