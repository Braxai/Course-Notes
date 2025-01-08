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
