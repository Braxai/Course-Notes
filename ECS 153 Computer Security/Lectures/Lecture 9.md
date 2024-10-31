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

SHA 1 : 160 bits --> 40 hexadecimal charcters
SHA 256 

Version Control Systems Problems 
- difficult to understand
- takes a lot of space
- branching (concurrent development) creates opportunity for mistakes and makes it hard to track which version is based on what
- collaborative team project ideally gives everyone a copy of the files but two people could get different copies
  - hard to determine who has authentic version

Revision Control System (RCS)

Control Version System (CVS)
- RCS and CVS are not ditributed, to share you have to send entire repository

Subversion : CVS but running on network, distributed 
- server contains massive copy of CVS
- everyone has client that can checkout and checkin
  - before checking in you have to ensure no one else is doing an update (difficult for teams)

Version Control System Properties 
- keep track of history (branching)
- know parent(s) of snapshot
- detect unauthorized revsion anywhere in history (attacks or disk failure)
  - achieved through hash function (database could be very large so hash decreases its size)
    - even the smallest modifications will be detected

Content Addressing Sysem : Git names file by it's SHA-1
- can determine validity of content by the name of the file 
File object
- foo.c : SHA-1
- bar.c : SHA-1

40 characters in SHA, first 2 are name of directory, last 38 are name of file
- name 0123...F --> 01 / 23...F

Tree Object : directory structure containing file name, permissions, and SHA-1
- foo.c, rwxrw_rw_ SHA-1

Miracle Tree : Tree of hash values where the root hash depends on all children, any change proliferates up to the root

Git stores objects fully but uses compression to minimize space

Git history tracking 
- commit object :
  - pointers (SHA-1) 
    - parent commits (can be multiple for merge)
    - current tree
    - description
