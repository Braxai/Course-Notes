Chicken and the egg problem with secure communication channel and secret key 
- To establish secret key you need secure communication channel
- To establish secure communication channel you need the key

Discrete Logarithm 

Find x such that g<sup>x</sup> = a mod p 
- g : generator
  - 1 < g < p - 1
- p : modulator
  - if p is a large prime then x is unique

Diffie-Hellman Key Exchange
- A : pick random a
- A --> B : g<sup>a</sup> mod p
- B : pick random b
- B --> A : g<sup>b</sup> mod p
- shared key : g<sup>ab</sup> mod p
  - A gets key by doing (g<sup>a</sup> mod p )<sup>b</sup> mod p --> B the inverse
- based on difficulty of discrete logarithm, attacker could compute some of these values
- Secure against Eve but not Mallory
- Public key

Man in the Middle Attack : 
- Active attack
- Mallory intercepts messages between A and B, picks c, sends g<sup>c</sup> to A and B
  - A secret key is g<sup>ac</sup> mod p
  - B secret key is g<sup>bc</sup> mod p
  - Mallory acts as a middle man making A and B think they are communicating with each other
    - A --> M : E<sub>g<sup>ac</sup></sub>(m)
    - M --> B : E<sub>g<sup>bc</sup></sub>(m)

Group of N people wish to communicate pair wise 
- symmetric key encrpytion needs n choose 2 : n(n-1) keys
  - every person has to store n keys (their key and everyone else's key)
- public key encryption system needs n pairs of keys
  - each person creates private/public key pair and publishes the public key
  - A --> B : A encrypts message with Bob's public key so only Bob can decrypt it
