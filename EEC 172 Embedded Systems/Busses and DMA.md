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

Two Bus System
* limits mnumber of actors on processor-memory bus to maintain high performance
* slow device son separate bus
* connected by a bridge which translates the two protocols
ARM 
* advanced high-performance vs advanced peripheral bus (high vs low speed)

Ensuring mutual exlusicivity on a shared bus
* central arbitration : central entity guarantees mutual exlusivity
 * arbitration : arbiter decides who gets to access the bus when requests are received
* distributed arbitration : all devices participate in choosing who gets access next

Multiple Bus Masters 
* multiple masters share the same bus
* Directed Memory Access (DMA) : simple I/O processor (programmable state machine)
* multiple processors
* high speed devices
How to decide which master can access the bus
* bus master wanting to use bus makes request and waits for request to be granted through arbitration
* bus priority : highest priority device serviced first
* fairness : lowest priority device should never be completely locked out from using bus (starved)

Daisy Chain Bus Arbitration 
* arbiter gives grant to highest priority an it propagates down the chain of devices
 * poor fairness, low priority devices may take forever to process
 * infledxible, priority hardwired
 * performance: grant-chain signal propagation may limit bus speed

Centralized Arbitration
* unique req/grant line pair for each device
* priority/fairness flexible in hardware and/or software
* used in essentialy all modern processor-memory busses and high speed I/O busses

### Direct Memory Access (DMA) : do I/O while CPU is doing something else (maybe sleeping)
* many I/O operations are simple sequential transfers of large data set
 * peripheral to memory
 * memory to peripheral
 * memory to memory
* I/O transfers might often be interrupt driven, using the CPU for such transfers is a waste

DMA Programming : DMA light-weight, specialized I/O processor (state machine) that is "programmed" (initialized) by software running on the CPu

DMA Initialization : CPU programs DMA registers that control the transfer

DMA Transfer : Flow THrough
* Data passes through controller
* 2 cycles/transfer
 * fetch and deposit

Device DMA 
* device can have its own dedicated DMA controller
* allows simple 1 cycle transfer
 * bus abitrate
 * address on bus, write data
 * bus release
* can now act as a master and initiate communication on the bus

Memory to Memory block copy
* more efficient than using processor

DMA Burst Transfers 
* bursts allow more efficient bus utilization
* dma includes data buffer
 * places sources address on bus, reads data burst

Bridge will have its own DMA 

Multi Channel DMA
* DMA controller can have multiple channels (multiple contexts), one for each DMA request
* switches between channels as requests arrive

Chained DMA
* DMA transfers can be chained : one transfer starts immediately after the prior transfer completes
* interrupts only after last transfer in chain
* reduces CPU overhead
 * one initialization
 * one interrupt
* dma controller has one context for each of the chained transfers 
