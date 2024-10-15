Cryptography : communication in the presence of adversaries
- Alice + Bob : parties that want to communication  
- Mallory : active attacker can observe, block, delete, insert, and alter messages 
- Eve : eavesdropping, passive attacker can only observe

Properties
1. Confidentiality : no one else can read the message 
2. Integrity : content of message unmodified 
3. Authenticity : determine who wrote the original message

Plaintext : original message 

Ciphertext : encrypted message 

One Time Pad : can be used once without security concerns, simple encryption scheme
- E<sub>k</sub>(m) = m XOR k
- D<sub>k</sub>(c) = c XOR k
This algorithm has n bit strings m and k where k is a random key used once
- guarantees confidentiality but not integrity

![image](https://github.com/user-attachments/assets/345f59b6-8636-4fa0-b2f2-8df5c33accaa)

Symmetric : Alice and Bob share same key 
- confidentiality ensured through block ciphers
- integrity ensured through message authentication code (MAC)

Asymmetric : encryption and decryption key are different (one private key and one public key everyone has access to) 
- confidentiality ensured through public key encryption 
- integrity ensured through digital signatures

Secure Hash Functions : given a key that can be put through a hash function to confirm it is valid 

Pseudo Random Number 

Confidentiality Attack Threat Model 
- known ciphertext attack : attacker can observe ciphertext 
- known plaintext attack : attacker can observe patterns between pairs of ciphertext and plaintext
  - both cases attacker is passive (Eve) and can't choose what is encrypted
- chosen plaintext attack : attacker asks sender to encrypt a message and see the resulting ciphertext
- chosen ciphertext attack : attacker asks receiver to decrypt a message and see the resulting plaintext

OTP 
- known plaintext attack and chosen plaintext attack can determine key so it must not be reused

