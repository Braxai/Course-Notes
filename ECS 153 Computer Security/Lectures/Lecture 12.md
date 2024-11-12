RSA
1. pick large random primes p and q of equal length
2. let n = pq
3. choose e s.t. gcd(e, (p-1)(q-1)) = 1 --> e, (p-1)(q-1) are relatively prime : e is not random and can be deterministic
4. compute d s.t. ed = 1 mod (p-1)(q-1) because e is relatively prime d must exist and it is unique
- Public Key: (n,e) and Private key : d
- E(m) = me mod n
- D(c) = cd mod n

RSA Digital Signatures 
- sign(m) = m<sup>d</sup> mod n 
- verify(m,t)
  - true if t<up>e</sup> = m mod n
  - false otherwise

Mallory wishes to sign m using Alice's key 
- Alice signed m<sub>1</sub> and m<sub>2</sub>
  - m<sub>1</sub> mod n
  - m<sub>2</sub> mod n
- (m<sub>1</sub> * m<sub>2</sub>)<sup>d</sup> = m<sub>1</sub><sup>d</sup> * m<sub>2</sub><sup>d</sup> mod n
Mallory asks Alice to sign m' and m*m'<sup>-1</sup>
- Mallory gets from Alice
  - (m')<sup>d</sup> mod n
  - (m*m'<sup>-1</sup>)<sup>d</sup> mod n
  - (m')<sup>d</sup> (m*m'<sup>-1</sup>)<sup>d</sup> = ((m')<sup>d</sup> * m(m'<sup>-1</sup>( )<sup>d</sup>
    
