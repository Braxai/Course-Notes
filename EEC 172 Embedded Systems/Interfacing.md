* IO/Devices
  * CPU communicates with I/O devices useing Data, Status and Configuration registers 
  * Device mechanism may be digital, analog, optical, mechanical, etc.
  * Program running on CPU uses registers to configure device, initiate a device action, detect device state, determine action completion, etc. 

![image](https://github.com/user-attachments/assets/17456b0c-6d54-4f8d-8767-ae2d0360e015)

Example Device : UART Module 
* Universal Asynchronous Receiver Transmitter (UART) : provides serial communication
  * Asynchronous : doesn't require a clock for sender and receiver to agree on time
  * Serial Protocol : one data line
* UARTs have many configuration, data and status registers

Serial Asynchronous Communication 
* Bytes are transmitted serially using a sequence of equally spaced high/low pulses that encode bits
  * Bracketed by Start, Stop pulses
  * Sender/receiver assume the same rate, use local clocks
    * Rate agreed upon ahead of time
    * Agree on message length

![image](https://github.com/user-attachments/assets/7522a226-7535-4fb0-9c87-1895e701c49f)

Parity Bit : detects error, add a bit so there is even/odd number of ones, if received message doesn't match there is an error 
* Only detects 1 incorrect bit
* Baseline error detection

UART Serial Communication Parameters 
* Baud (bit) rate (determines pulse width)
 * Baud : how many symbols you can send across channel
* Number of pits per character (6, 7, or 8)
* Parity/No parity
 * Even/odd
* Length of stop bit
* more

![image](https://github.com/user-attachments/assets/8eb9a00c-6c90-49a4-ba14-663b4c751235)

Register-Address Sharing 
* A read-only register and a write-only register may share the same address

I/O Device Interaction 
* Two types of instructions for doing I/O
 * Special Purpose I/O instructions (old)
  * x86 includes special in, out instructions
   * I/O instructions have their own address space
 * Memory-mapped load/store instructions (modern)
  * includes x86
  * device registers/device memory appear as specific addresses in the memory space
  * memory address must be decoded within device or decoded externally to select device

Polling (busy wait I/O): Input Device 
* Software checks I/O device status bit
 * loops until device is ready with data
Polling Output Device : loop until device is idle then send data

Interrupt I/O 
* Polling is inefficient
 * wastes CPU time
 * wastes energy
 * system can hang if faulty device
 * only benefit is simplicity and shorter response time
* Interrupts allow device action to change the flow of control in the CPU
 * Event causes 'subroutine call' to device interrupt handler (interrupt service routine)

Interrupts for Single Device 

![image](https://github.com/user-attachments/assets/2289479f-f170-4aa2-bcba-f80556f9627b)
* Handler is function explicitly designed to address a specific interrupt
* Device must be enabled for interrupts
 * Mask = 1 enables corresponding interrupt
 * Mask = 0 default

UARTIntEnable(unsigned long UlBase, unsigned long ulIntFlahs)
* ulBase is base addr of UART port
* ulIntFlags is bit mask of interrupts to enable (logical or)

Device handler can be specified by changing entry in startup_css.c and indicating handler is external 
* Replace a handler by writing your own function and replacing what you want with your function name, include EXTERN function_name to tell compiler the function definition is elsewhere in the file

Highest Priority Interrupts 
* Some interrupts are so important they cannot be ignored
 * hardware faults
 * non-maskable interrupt (NMI)
 * reset
* Generally lead to putting the embedded system into a safe state

Software Perspective : Interrupt Phases 
1. device requests interrupt
2. at the end of current clock cycle CPU checks for pending interrupts
3. cput acknowledges interrupt, saves some data
 * return address (interrupt PC) and program status register
 * cortex M4 saves at specified interrupt stack location 
4. Hardware branches to handler using interrupt bector
 * device assers interrupt wire and places value on data bus that maps to specific vector table entry
 * vector table entry contains address of handler
5. Execute body of handler
6. Return from interrupt (RFI)
Handler can be written as a normal HLL procedure
  * compiler inserts RFI instruction instead of return
  * register lnkage convention is same as procedure call

Interrupts for Multiple Devices 
* Must resolve which device requested interrupt (priority)
 * Simple approach sets priority based on int line # (OK but not flexible)
* can use dedicated interrupt request lines
* interrupt acknowledge lines can be shared 
![image](https://github.com/user-attachments/assets/dc5f72e1-798d-4e27-95c4-ad3bbff36904)

Configurable Interrupt Priority 
* General purpose microcontrollers, such as ARM Cortex, allow software configurable interrupt policy
* Cortext Nested Vectored Interrupt Controller (NVIC) allows software to dynamically map any interrupt request (IRQ) to any priority
 * handler can raise or lower priority of its devices interrupts
* Completely configurable priority for n devices can be built using nlog(n) hardware and the highest priority interrupt can be resolved in log(n) time












