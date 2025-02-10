Why Distributed Embeded 
* modularity
* low complexity
* faster real-time response
* simplified interconnect
* increased electrical noise immunity
* fault isolation / reliability

Inter-Integrated Circuit Bus (I2C)
* low cost, medium data rate, short distance applications
* Characteristics
  * bit serial
  * multiple masters and slaves
  * fixed-priority arbitration based on address

I2C Physical Layer 
* two wires
  * data
  * clock
* common ground

I2C Transmission : transmission for given master contains one or more messages to one or more slaves 
* delimited by start (S) and stoP (P) bits : S | message 1 | message 2 | P

I2C Message : contains two or more transactions between master and specific slave 
* one address transaction followed by one or more data transactions
  * address transactino indicates which slave will send/receive data
* S | address 1 | data 1 | S | address 2 | data 2.1 | data 2.2 | P

Each transactino includes 9 bits 
* 8 payload bits from sender to receiver
* 1 acknowledge big from receiver to sender
  * AK = 0 terminates transfer
* address transaction payload sent by master
  * 7 bit address of slave involved in transaction
  * 1 direction bit : 0 = wire, 1 = read (WRT master)
* S.1 | Address.7 | R/W.1 | AK.1 | Data.8 | AK.1 | P.1
  * structure.number of bits
  * values show up by different writers through some sort of synchronization
 Examples
* Multi-byte Write : S | Address | 0 | 1 | data | 1 | data | 1 | P
* One-byte Read from Slave : S | Address | 1 | 1 | data | 0 | P
* Write then Read : S | Address | 0 | 1 | data | 1 | S | Address | 1 | 1 | data | 0 | P


