# Security Principles
### 1.1 Know your threat Model 
Threat Model : model of who your attack is and what resources they have
- who and why might someone attack?

Common Assumnptions to take into account about attackers
1. can interact with your systems without anyone noticing
2. has general information about system (OS, software vulnerabilities, etc.)
3. is persistent and lucky, will attack as many times as necessary
4. has resources required to undertake attak
5. can coordinate several complex attacks across various sysetms
6. every system is a potential target

### 1.2 Consider human factors 
Security systems must be usable by ordinary people and must take into account usabilitiy 
- fool-proof user-friendly options ideal 

### 1.3 Security is economics
Systems need only need to be protected against a certain level of attacks; expected benefit of paid security defense should be proportional to the expected cost of the attack
- cost benefit analysis

Focus energy on securing weakest links
- Conservative Design : sytems should be evaluated according to the worst security failure that is at all plausible, under assumptions fabvorable to the attacker 

### 1.4 Detect if you can't prevent
If you cannot prevent an attack from happening, you should at least be able to know that the attack has happened and respond accordingly 

Assume bad things will happen, prepare for the worst case outcome, and plan security in a way that lets you get back to some form of a working state

### 1.5 Defense in depth
Multiple types of defenses shuold be layered together so an attacker would have to breach all the defenses to successfully attack a system

ex: Two detectors D<sub>1</sub>, D<sub>2</sub> with false positive rates FP<sub>1</sub>, FP<sub>2</sub> and false negative rates FN<sub>1</sub>, and FN<sub>2</sub> respectively
- Two detectors in parallel (either going off triggers response) increases FP rate and decreases FN rate
- Two detectors in series (both have to alert to trigger response) decreases FP rate and increase FN rate

### 1.6 Least privilege 

### 1.7 Separation of responsibility 

### 1.8 Ensure complete mediation 

### 1.9 Shanon's Maxim 

### 1.10 Use fail-safe defaults 

### 1.11 Design security in from the start 

### 1.12 The Trusted Computing Base (TCB) 

### 1.13 TOCTTOU Vulnerabilities 
