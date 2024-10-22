Keystroke Inferece 
- different keys on average take a different amount of time to click
- identifying which sent packets have keystrokes in them gives attacker ability to infer which keys were used

Symmetric key encryption believed to be secure but can't be proved to be secure
- they haven't been broken after many years

Asymmetric key encryption is slower than symmetric 

Symmetric Key Encryption 
- sender and receiver share key --> key must be kept confidential
- prevent Eve from decrypting messages
  - if seeing ciphertext gives Eve an advantage over randomly guessing than the encryption failed
- length of ciphertext should be consistent regardless of
  - to not worry about length we could pad --> increases cost and decreases efficiency
    - in real life encrpytion doesn't protect length of message, if length is critical to application it pads itself
      - may pad a little, say 1K or 4K, to make it indistinguishable

Game to determine if the symmetric key encryption works

Indestinguishability Under Chosen Plaintext Attack ( IND-CPA ) 
- E<sub>k</sub> : encryption primitive
  - k : key
    - fix k and put it in blackbox with a switch and two inputs
      - switch determines which message gets encrypted
  - typically encrypt a block at a time
- attacker gives two messages to the box
  - m<sub>1</sub> and m<sub>2</sub> of same length 
- produces ciphertext C
- Attacker given E<sub>k</sub> encryption scheme and can give multiple plaintexts
  - attacker has to determine the position of the switch --> if m<sub>1</sub> or m<sub>2</sub> was encrypted into C

Encryption scheme must be nondeterministic so the same message won't be encrypted the same every time 

Step 1: attacker given blackbox and passes two messages in to create C 

Step 2: remove encryption scheme and let attacker send as many messages as they want 

Step 3: attacker guesses where switch is 

If attacker can not win with probability > 0.5 than the encryption scheme works 

One Time Pad --> key can be used once 
- E<sub>k</sub> = m ^ k 
- D<sub>k</sub> = c ^ k
Information-theoretic secure

Block Cipher
- E: {0,1}<sup>n</sup> x {0,1}<sup>k</sup> --> {0,1}<sup>n</sup>
  - plaintext x key --> ciphertext
- if fixed key
  - bijective : each unique plaintext must have unique ciphertext
    - domain and codomain are the same --> E<sub>k</sub>: permutation
- Permutation small change in input should have dramatic change in output
  - Random Permutation secure but not practical 
  - number of permutations over block of size n {0,1}<sup>n</sup> : 2<sup>n</sup>!
    - Very expensive to have a massive lookup table to store all the random permutation
      - Lookup table is size 2<sup>n</sup>
- Pseudo Random implemntation : AES has n=128 and randomly chooses from 2<sup>128</sup> possibilities, no ! to reduce security but increase practical implementation
Block Cipher Problems
- AES (block ciphers) don't pass IND-CPA because it's permutation, every plaintext has deterministic ciphertext block
- Encrypting messages of arbitrary length
ECB : Electronic Code Book (easy to break) 
- encrypt each fixed size block using the same key
CBC : Ciphertext Block Chaining (secure)
- XOR ciphertext of previous block with plaintext of current block
  - use initialization vector (random block) to XOR with first plaintext
CBC Problems :
- must run sequentially
- if you lose a ciphertext block on the network you can't decrypt anything after that
