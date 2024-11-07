Chicken and the egg problem with secure communication channel and secret key 
- To establish secret key you need secure communication channel
- To establish secure communication channel you need the key

Discrete Logarithm 

Find x such that g<sup>x</sup> = a mod p 
- g : generator
  - 1 to p - 1
- p : modulator
  - if p is a large prime then x is unique

Diffie-Hellman Key Exchange
- A : pick random a
- A --> B : g<sup>a</up> mod p
- B : pick random b
- B --> A : g<sup>b</sup> mod p
- shared key : g<sup>ab</sup> mod p
  - A gets key by doing (g<sup>a</sup> mod p )<sup>b</sup> mod p --> B the inverse
- based on difficulty of discrete logarithm, attacker could compute some of these values



