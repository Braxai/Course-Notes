Providers allow downloading through mirrors to protect server efficiency 
- user downloads hash code from provider
- computer hash value locally and compare with what they downloaded from the mirror
  - if there is inconcistency then the mirror provided something other than what the user expected

Hash Function to have distinct output for each input (surjective)
- the codomain >= domain
  - pigeonhole principle
  - defeats purpose of hash because downloading hash is same as downloading original image and our goal is to reduce bandwidth from the server : codomain needs to be much smaller than domain

How to benefit from hash function without security risks? 
Hash Function : k : {0 : 1}<sup>m</sup> --> {0 : 1}<sup>n</sup> 
- 2<sup>m-n</sup> collisions : inputs with same hash value
  - many collisions exist but there are still so many input possibilities it's not feasible for attacker to find them

One Way Property : given y, hard to find an x such that h(x) = y

Second Preimage Resistant Property : given x, hard to find x' != x and h(x) = h(x')
- x is an ubuntu image and x' is a second preimage
- stronger guarnatee than collision resistant property 

Collision Resistant Property : hard to find x<sub>1</sub> != x<sub>2</sub> such that h(x<sub>1</sub>)=h(x<sub>2</sub>)

