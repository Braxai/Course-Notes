CPU Bus 
* Bus : shared medium allowing CPU, memory and/or devices (actors) to communicate
  * set of wires and electrical protocol (physical layer)
  * communications protocol (logical layer)
 * Bus Lines
   * bus wires (lines) grouped as address, data and control lines
 * Bus Width : number of bus lines in each group varies significantly with the hardware application
   * Wide busses can have more data lines than word size
     * parallel instruction fetch
     * parallel data
   * Narrow busses can use fewer bus lines for address, data and control by time multiplexing a larger number of logical bus lines across a smaller number of physical bus lines
     * in the limit, physical bus width can be 1 trading space for time
   * Bus width usually wider on chip and narrower off chip
     * wide off chip requires many pins, increases cost and energy
     * on chip line cost is relatively small

* I2C : low cost, low performance

Bus Protocol
* determine how devices communicate
* asynchronous or synchronous

Timing Diagrams 
* most common method for specifying protocol

Asynchronous Protocol : no clock, 4 round handshake 
* master asserts req to receive (read) data
* servant puts data on bus, asserts ack
* master receives data and deaserts req
* servant deasserts ack, ready for next request

Asynchronous bus memory read 
* includes two 4 roudn handhsakes: one for address, one for data
* Advantage
  * communication at maximum rate allowed by pair of actors
  * energy efficient
* Disadvantage
  * far slower
 
Synchronous CPU Bus
* clock provides synchronization
* R/W true when reading, false when writing
* data ready signals when data are ready (asynchronous)


