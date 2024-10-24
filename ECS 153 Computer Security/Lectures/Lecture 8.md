Cipher Block Chaining Problems 
- must run sequentially
- losing a ciphertext block prevents future blocks from being decrypted

One Time Pad can be used in theory if there are infinite keys of arbitrary length 
- sender and receiver could agree on random number generator seed to create a sequence of keys that match

Good block cipher produces ciphertext that is indistinguishable from random permutations 


### Scheme to solve CBC problems ###
Combine one time pad with cbc --> INSECURE 
- OTP : xor message with result of encryption to create the ciphertext
- Block Cipher: each block cipher is close to random permutation
- deterministic, every time we run this system it produces the same "random number"
  - attack: give different m1 and m2 in stage 1, give m1 in stage 2
 
Solution : 
- keep state initialized with IV
  - each time we encrypt a message it generates a random IV block and adds IV to each number  

This new scheme is CTR (Counter Mode) : secure if block cipher is secure 
- all block ciphers can be run at same time
  - once we have IV we can determine what goes into each block cipher and run in parallel
- losing a block doesn't mean we can't decrypt future blocks
  - the counter is encrypted and the result is xor with the message
    - will always have the counter and message for each block

CTR mode is good for video streaming where it's ok to drop packets and we value timeliness of the broadcast 

CTR Decryption 
- determine m by encrypted counter and xor with c
  - to get m1 from c1 we encrypt IV + 1 again and then xor c1 with that

CBC and CTR secure as long as IV is random, otherwise the encryption for messages will be deterministic 
- Cryptographically secure random number generator : most cryptographic mode need a good random number generator
