Alice and Bob share a secret key that is not known to anyone else

### 6.1 IND-CPA Security
Formal definition of confidentiality : the ciphertext C should give the attacker no additional information about the message M

Indistinguishabiltiy Under Chose Plaintext Attack (IND-CPA) : Even if E tricks A into encrypting some messages she still cannot distinguish whether A sent M0 or M1.

IND-CPA game works as follows : 
- E chooses two different messages M0 and M1 and sends them to A
- A flips a coin to determine which to encrypt before sending the encrypted message to E
- E can ask A for encryptions of messages of E's choosing, send plaintext to A, and A will send back the encryption of the message
- E must guess if M0 or M1 is encrypted
If E can guess which is encrypted with pro bability greter than 0.5 they win because they learned some information about which message was sent so the scheme is not IND-CPA secture
Some additional conditions : 
- M0 and M1 must be the same length
- E limited to practical number of encryption requests
- E only wins if she has non-negligible advantage 

### 6.2 XOR review
![image](https://github.com/user-attachments/assets/040ace97-453f-4a95-aec5-105f942e9d23)

Properties 

![image](https://github.com/user-attachments/assets/7819de4c-cf25-4a20-af4b-da89e2ddd93a)

### 6.3 One Time Pad
One-Time Pad (OTP) : simple and idealized encryption scheme that helps illustrate some important concepts 
- A and B share n-bit secret key with bits picked uniformly at random
Desired properties of encyption scheme
1. scramble message, map it to a ciphertext C
2. given knowledge of secret key K it shuold be easy to recover M from C
3. E should get no infromation about M

cj = mj xor kj : bitwise xor of message and key 

![image](https://github.com/user-attachments/assets/fa83ed23-9c92-4450-a3d1-c917e0b53813)

Drawback : Key cannot be reused
- not secure if the key is used to encrypt more than one message

### 6.4 Block Ciphers
Block Cipher : transforms a fixed-length, n bit input intoa fixed-length n bit output 
Two operations : 
1. encryption takes in an n-bit plaintext and a k-bit key as input and outputs an n-bit ciphertext
2. decryption takes in an n-bit ciphertext and k-bit key as input and outputs an n-bit plaintext

Must be deterministic 

### 6.5 Block Cipher Security
Block ciphers not IND-CPA secure on their own becuase they are deterministic 

Block cipher is Computationally Indistinguishable from a random permutation
- given practical amount of coputation power E cannot guess with probabiltiy greater than 0.5
- attacker without a key cannot learn anything about the original message 

### 6.6 Block Cipher Modes of Operation
Electronic Code Book (ECB Mode) : plaintext M broken into n bit blocks and each block is encoded using the block cipher
- flawed because any redundancy in the blocks will show through and allow the eavesdropper to deduce information about the plaintext

Cipher Block Chaining (CBC Mode) : sender picks random n bit string called initial vector or IV for each message, defines C0 - IV, the ith cipher block is given by ![image](https://github.com/user-attachments/assets/4d0b26ce-f358-4545-8969-2633b5308ce8) and the ciphertext is the concatenation of the initial vector and these individual blocks ![image](https://github.com/user-attachments/assets/b8de9dc9-74fe-49ed-9080-2d67b16fdf4a)
- provides strong security guarantees on the privacy of the plaintext message 

Ciphertext Feedback (CFB Mode) : C0 is the IV, the ith ciphertext block given by ![image](https://github.com/user-attachments/assets/2d4fc4e9-f468-4a39-84fb-62be6ca962ee)

Output Feedback (OFB Mode) : IV repeatedly encrypted ot obtain a set of values Z that are used as though they were the key for a one-time pad so ![image](https://github.com/user-attachments/assets/244be4ba-8544-4cc1-9f3c-7b68a8a9d557)

Coutner (CTR Mode) : coutner initialized to IV and repeatedly incremented and encrypted to obtain a sequence that can now be used as though they were the keys ofr a one-time pad, namely ![image](https://github.com/user-attachments/assets/2ccaa84c-5c68-48ce-becd-a9885053da38) and ![image](https://github.com/user-attachments/assets/6c459010-af2a-4d33-beec-22d54c0988ac)

### 6.7 Parallelization
In some modes, successive blocks must be encrypted or decrypted sequentially. 
- CBC mode decryption
- CTR mode encryption and decryption 

### 6.8 Padding
Add padding to the plaintext until it is a multiple of the block size 

### 6.9 Reusing IVs is insecure
Encrypting the same plaintext twice always results in the same output and this causes information leaks. Modes must introduce a random initialization vector IV that is different on every encryption in order to ensure that encrypting the same plaintext twice with the same key results in a different output
