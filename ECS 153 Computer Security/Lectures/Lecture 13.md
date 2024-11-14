RSA
- sign with thte signer's private key
- verify with the signer's public key
- sign(m) = h(m)<sup>d</sup> mod n
- verify(m,t) true if h(m) = t<sup>e</sup> mod n

Public Key Infrastructer : Tree structure where node signs all certificates that are it's children 

![image](https://github.com/user-attachments/assets/3a3df305-0f4b-48d9-a5a0-c88b98c526f0)

Certificate Errors in Browsers 
- self signed certificates
- invalid signature
- domain name mismatch
- expired certificate 
