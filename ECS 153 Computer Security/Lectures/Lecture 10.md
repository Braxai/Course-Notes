Message Authentication Code (MAC) : confirm who authored a message 
- Secure hash functions can alert you if there is a modification but don't bind message to author
- MAC is a function T=F(k,m)
  - Function takes key + message and outputs a tag
    - Can't produce a correct tag without a key
  - Verify tag by ensuring it is the same tag that we get when passing the key and message through the function
- Encryption is an incorrect method for implementing a MAC

HMAC implement MAC function with secure hash functions
- H(k'⊕opad||H(k'⊕ipad||m))
  - opad and ipad purpose to make two different keys from one key
    - o = outside and i = inside
  - k' same length as ipad/opad
    - if k is longer than ipad/opad we hash k to get k'
    - if k is shorter than ipad/opad we pad k to get k'

MAC guarantees authenticity and integrity but not confidentiality 

Confidentiality and Integrity 
- MAC and encrypt : Esub>k</sub>((m), MAC<sub>k</sub>(m))
