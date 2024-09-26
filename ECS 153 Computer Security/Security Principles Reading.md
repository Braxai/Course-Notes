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
Give a program the set of access privileges that it legeitimately needs to do its job and nothing more
- minimize how much privilege each program and system component get

Doesn't reduce probability of failure but reduces the expected cost of failures

### 1.7 Separation of responsibility 
Split of privilege so no one person or program has complete power
Require more than one party to approve before access is granted

### 1.8 Ensure complete mediation 
When enforcing access control policies, check every access to every object
Reference Monitor : single point through which all access must occur (ensures all access is monitored and protected)

### 1.9 Shanon's Maxim 
Shanon's Maxim : attacker knows the system that they are attacking

"Security through obscurity" : systems that rely on the secrecy of their design, algorithms, or source code to be secure. 
- brittle and difficult to keep system design a secret
- never rely on sobscurity as part of security

Kerckhoff's Principle : crytopgrahic systems shuold remain secure even when the attacker knows all internal details of the system
- secret key is only thing that must be kept secret and the system should be designed to make it easy to change leaked keys

### 1.10 Use fail-safe defaults 
Fail safe default settings balance security with usability when a system goes down
- if security mechanisms fail or crash they should default to secure behavior

### 1.11 Design security in from the start 
Editing an existing application after it has been spec'ed, designed, and implemented is very difficult. Avoid getting stuck with insecure architecture by contemplating security through development. 

### 1.12 The Trusted Computing Base (TCB) 
The Trusted Computing Base (TCB) is that portion of the system that must operate correctly in order for the security goals of the system to be assured. 
- Have to rely on every component in the TCB to work correctly, anything outside the TCB isn't relied upon in any way
- Made as small as possible

TCB Design Principles
- Unbypassable (completeness) : no way to breach system security by bypassing the TCB
- Tamper-resistant (security) : TCB protected from tampering by anyone else; other parts of the system outside the TCB should not be able to modify the TCB's code or state
- Verifiable (correctness) : should be possible to verify correctness of the TCB; TCB as simple as possible

Keep It Stimple, Stupid (KISS) : TCB simple and small, less code has less opportunities for mistakes; move as much as possible outside the TCB 

### 1.13 TOCTTOU Vulnerabilities 
Time of Check to Time of Use (TOCTTOU) vulnerability usually arises when enforcing access control policies such as when using a reference monitor
Between check and use of whatever state was checked the state changed causing a TOCTTOU vulnerability
