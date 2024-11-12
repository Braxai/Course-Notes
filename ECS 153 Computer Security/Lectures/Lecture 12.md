RSA
1. pick large random primes p and q of equal length
2. let n = pq
3. choose e s.t. gcd(e, (p-1)(q-1)) = 1 --> e, (p-1)(q-1) are relatively prime : e is not random and can be deterministic
4. compute d s.t. ed = 1 mod (p-1)(q-1) because e is relatively prime d must exist and it is unique
- Public Key: (n,e) and Private key : d
- E(m) = me mod n
- D(c) = cd mod n

RSA Digital Signatures 
sign(m) = m<sup>d</sup> mod n 
verify(m,t)
