### 5.1 Disclaimer: Don't try this at home! 
Cryptography is difficult to implement and has high stakes. Using existing well-vetted cryptographic tools is often best. 

### 5.2 Brief History of Cryptography 
Cryptography : study of how to write secret messages 

Pen and Ink period of simple messages decoded by hand 

Mechanical era result of German project creating a mechanical device called the Enigma machine for encrypting messges in an unbreakable code 

Modern cryptography destinguied by reliance on mathematics and electronic computers 

### 5.3 Definitions 

### 5.4 Definitions: Alice, Bob, Eve, and Mallory 
Alice and Bob wish to communicate securely, Eve is eavesdropping their line of communication and Mallory can tamper with communications in addition to eavesdropping on them. 
- goal for Alice and Bob to communicate without Eve knowing the contents of their communicaiton and Mallory being unable to tamper with the contents 

### 5.5 Definitions: Keys 
Key : secret value that helps secure messages 
- Symmetric key model : Alice and bob know the value of the key
- Asymmetric key model : each person has a secret key and a corresponding public key

### 5.6 Definitions: Confidentiality, Integrity, Authenticity 
Three main security properties 
1. Confidentiality : prevent adversaries from reading our private data
  - use a key to encrypt message that is send and then decrypted by the receiver
    - plaintext : unencrypted message
    - ciphertext : encrypted message 
2. Integrity : prevent adversaries from tampering with private data
3. Authenticity : be able to determine who created a given message

Most cryptographic algorithsm that guarnatee integrity and authentticity work as follows : 
- A generates tag or signature on a message
- A sends message to B
- B receives message and tag, verifies tag is valid and was not modified by attacker 

Deniability Property : no cryptographic proof available to guarantee that A's published message came from B if A wanted to publish a message they received from B

### 5.7 Overview of schemes 
![image](https://github.com/user-attachments/assets/27ac120b-0563-4f12-aee4-92a12d60f69f)

Symmetric-key encryption : A uses key to encrypt message and B uses same key to decrypt

Public-key encryption : B generates a matching public and private key and shares the public key with A, A can encrypt a message under B's public key and B will decrypt with private key 

Message Authentication Codes (MACs) : provide integrity and authenticity in symmetric-key setting
  - A uses shared key to generate MAC on message and B uses secret key to verify MAC is valid

Public-Key Signatures (digital signatures) : provide integrity and authenticity in asymmetric-key setting
  - A generate matching public key and private key, shares public key with V, A computes digital signature of message using private key and appends signature to message, B uses public key to verify message is untampered

Cryptographic Hases : one way digest; enable someone to condense long message into short sequence of what appear to be random bits
  - irreversible, can't go from hash back to original message but can quickly verify a message has a given hash

Pseudo Random Number Generator : process that takes small amount of true randomness and stretches it into a long sequence that should be indistinhuishable from actual random data 

Key Exchange Schemes (Diffie-Hellman key exchange) : allow A and B to use insecure communication channel to agree on a shared random secret key that is subsequently used for symmetric-key encryption 

### 5.8 Definitions: Kerckhoff's Principle 
Cryptosystems should remain secure even when the attacker knows all internal details of the system. The key should be the only thing that must be kept secret and the system is designed to make it easy to change key.

### 5.9 Definitions: Threat models 
Possibilities of how much access eavedropping attacker Eve has to insecure channel : 
1. Cipghertext-only attack : E intercepts single encrypted message and wishes to recover plaintext
2. Plaintext attack : E intercepts encrypted message and already has some partial infromation about the plaintext
3. Replay attack : E capture encrypted message from A to B and sends encrypted message to B again
4. Chosen-plaintext attack : E tricks A to encrypt arbitrary messages of E's choice for which E then observes the resulting ciphertexts. When A encrypts a message unkonwn to E, E intercepts and aims to recover the message given what E has observed from previous encryptions 
5. Chosen-ciphertext attack : E trick B into decrypting ciphertexts to learn decryption of some other ciphertext
6. Chosen-plaintext/ciphertext attack (most serious threat model) : E can trick A into encrypting some messages of E's choosing and trick B into decrypting some ciphertexts of E's choosing. E would like to learn decryption og some other ciphertext sent by A

