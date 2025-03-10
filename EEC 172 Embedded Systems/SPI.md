Serial Peripheral Interface : communication hardware designed to interconnect integrated circuits to a MCU belonging to the same board 
* Designed for point to point communication

SPI is master-slave interface 
* Master : head of communication and in general a MCU
* Slave : all the other devices which respond tomaster solicitations

4 point to point unidirectional wires 
* SCK : master to slave, serial clock generated by master
* MOSI : master to slave, master out slave in, serial data transmitted by the master and sent to a slave
* MISO : slave to master, master in slave out, serial data transmitted by a slave and sent to the master
* SS : slave to master, slave select, logic signal that is used to wake up and select a slave device

SPI transaction started by master setting SS line to logic 0
* master then starts generating clock signal in SCK line
* at each clock tick
  * master puts data bit in MOSI
  * slave puts dat abit in MISO
* when transaction terminates, master sets SS line to logic 1

Digital-to-Analog Converter (DAC) : circuit that receives a digital data and is able to generate a voltage signal proportional to the received data 

for MCP4921 SPI packet sent by Master is 16 bits
* first 4 bits represent configuration of the chip
* other 12 bits represent DAC value
* chip does not generate data so it does not have a MISO line
Different devices have different configurations/protocols

Parallel Connection : multiple slaves
* SCK, MOSI and MISO wired together
* SS line per addressed device
* when a specific slave needs to be addressed the relevant SS line is activated

Daisy Chain Connection : multiple slaves
* MOSI/MISO cascade connectoin of all SPI slave devices
* MOSI and MISO connected in sequence
* single SS line for all devices
* devices must support this kind of connection

Clock Polarity and Phase 
* clock of SPI interface programmed in order to set its behavior
* two kind of setting
  * CPOL (clock polarity) : specifies the initial logic state of the clock
  * CPHA (Clock phase) : specifies the clock transition used to same data (data changes in the other transition)
