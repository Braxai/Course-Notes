Message Authentication Code (MAC) : confirm who authored a message 
- Secure hash functions can alert you if there is a modification but don't bind message to author
- MAC is a function T=F(k,m)
  - Function takes key + message and outputs a tag
    - Can't produce a correct tag without a key
  - Verify tag by ensuring it is the same tag that we get when passing the key and message through the function
- Key shared by sender and receiver (symmetric key cryptography)

