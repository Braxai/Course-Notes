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
- E<sub>k</sub> : encryption primitive
  - k : key
    - fix k and put it in blackbox with a switch and two inputs
      - switch determines which message gets encrypted
  - typically encrypt a block at a time
- attacker gives two messages to the box
  - m<sub>1</sub> and m<sub>2</sub>
- produces ciphertext C
  - attacker has to determine if m<sub>1</sub> or m<sub>2</sub> was encrypted into C



