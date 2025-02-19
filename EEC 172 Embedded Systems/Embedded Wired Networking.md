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

I2C message structure/msemantics device specific, not globally defined 

I2C general call addres (000 0000) used for broadcast message 

I2C Electrical Interface 
* open drain device connection
 * active pull down, passive pull up
  * pull down will win (have priority) over pull up
  * addresses closest to 0 have higher priority because they are lower
 * each device can drive or listen on each line

Start / Stop Signaling : SDA transition during clock High indicates Start or Stop 
* Data Transitons : other SDA transitions occur when the clock is low
 * data must be stable when clock high

I2C Arbitration 
* all devices can see the bus, won't send messages if not idle

Clock Synchronization 
* during arbitration, clocks from multiple contending masters will synchronize
 * SCL low is 'wired XOR' so a lagging clock will delay the transition of SCL
 * each master must listen to SCLin to determine end of SCL clock phase, not just consider SCLout
  * Clock Stretching : if slave is not ready to send/receive bit, before clock goes high, slave pulls down SCL to stretch the clock until slave is ready

### Controller Area Network (CAN)
CAN Benefits : more generally drive by wire / electronic control benefits
* Reduces wiring complexity
* reduces cost : trades copper and labor for silicon
* reduces weight
* increases electronics reliabiltiy
 * more noise immunity, error detection/retry

CAN Applications 
* larger geographic distance coverage compared to I2C
* Planes, trains, automobiles, boats, medical, industrial, scientific instruments, elevators...

Basic CAN System Architecture 
* Three layers of OSI model
 * application layer
 * data link layer : including data typing, error control, bit stufing
 * physical layer : convert digital 0s and 1s to/from analog electrical pulses

![image](https://github.com/user-attachments/assets/60064df9-7b84-4e96-8fc8-78e3bfafe437)

CAN Data Flow Model
* CAN mesages includes data and data type, not data destination address
* message can be received by multiple nodes responsible for a given data type (multi-cast)
 * hardware filters un-interesting data types

CAN Message (Frame) Format 
* Start (SOF), Stop (EOF), and ACK similar to I2C
* indentifier indicates data type
* remote transmission request (RTR)
 * RTR = 0 : data of type identifier being sent
 * RTR = 1 : data of type identifier being requested
* data length (DLC) 4 bits
* cyclic redundancy check (CRC), type of checksum

![image](https://github.com/user-attachments/assets/3bbafd37-e4f6-403b-8959-e3ec88817b0b)

CAN Physical Layer
* CAN uses a twisted-wire pair, terminated at each end to eliminate reflections (120 ohm)
 * no common ground
 * processors can fail silent

CAN Electrical Interface
* node input measures differential voltage between CANH and CANL
* node output 1 (recessive bit) by disconnecting from the bus
* node output 0 (dominant bit) by driving current to ensure a ~Vcc voltage drop across R

Bud Data Rate 
* 1 to 0 transition is active, fast
* 0 to 1 transition is limited by RC decay, limits bus speed vs C, which limits bus speed vs length
 * bit rate decreases as bus length increases

EMI Rejection
* twisted pair, differential signal increases immunity to electromagnetic interference (EMI)
 * similar EMI voltage induced in each wire, has little effect on voltage difference between wires
* wires can also be shielded

CAN Clocking 
* bits sent based on timing of sender's local clock
* receiving node phase locks on the data to determine the start/end of each bit time slot
* if there are too many consecutive 0s or 1s the clock phase could drive and result in an error

Bit Stuffing 
* to avoid phase shift problem, after five identical bits, the sender data-link layer stuffs a dummy complement bit in the data stream
* the receiver data-link layer discards the dummy bit receiving a series of five identical bits
* ensures timing of physical layer

Erros 
* Error handling
 * CAN recognizes various types of errors
* Bit Error
 * node that is sending a bit on the bus also monitors the bus
 * when the bit value monitored is different from the bit value being sent, the node interprets the situation as an error
* Stuff error : six consecutive dominant or recessive levels occurs in a mesage field
* CRC error
* Acknowledgement error
