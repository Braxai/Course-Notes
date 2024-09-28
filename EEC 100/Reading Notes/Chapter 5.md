String Gage : grid of thin wires whose resistance changes when the wires are lengthened or shortened according to the equation  ![image](https://github.com/user-attachments/assets/263fd5f4-c729-462e-b95d-de8a203b8eea)
- R resistance, deltaL/L fractional lengthening of the gage (strain)
- type of transducer, which is a device that measures the metal bar in the bending angle

### 5.1 Operational Amplifier Terminals 
- Noninberting input terminal (+)
- Inverting input terminal (-)
- Power Supply Terminals (V<sub>+</sub> and V<sub>-</sub>
- Output Terminal

![image](https://github.com/user-attachments/assets/e4758340-00e8-4aa3-9d18-21272d86b96e) ![image](https://github.com/user-attachments/assets/f2da6088-dd38-470a-ac79-cf271d68bba9)

### 5.2 Terminal Voltages and Currents 
Voltage variables messured from common reference node

![image](https://github.com/user-attachments/assets/a4cf15fa-50eb-4f88-9023-781be90d2c11)

All voltages considered voltage rises from the common node

![image](https://github.com/user-attachments/assets/16cf1877-5989-44df-b9d1-2cb17758cab8)

Terminal behavior of op amp as linear circuit element characterized by constraints on input vultages and currents

The voltage transfer characters describes how ouput voltages vary as a function of the input voltages 

![image](https://github.com/user-attachments/assets/68998348-8e89-489c-b125-0062ff364c68)
![image](https://github.com/user-attachments/assets/0e11dc75-9360-4a22-afcd-19309ff6dbe0)

Three distinct regions of operation 
1. negative saturation
2. linear region
3. positive saturation
When input voltage difference is small the op amp behaves as a linear device where output voltage is the difference between input voltage times multiplying constant (gain)

If op amp confined to its linear operation region, a constraint is imposed on input voltages where v<sub>p</sub> = v<sub>n</sub>
Negative feedback : signal fed back from output and subtracted from input signal 
- causes input voltage difference to decrease and op amp to operate in its linear region 


Input Current Constraint for an Ideal op amp : i<sub>p</sub> = i<sub>n</sub> = 0

Circuit Analysis Steps 
1. **check for negative feedback path**, if it exists assume op amp operating in linear region
2. **write KCL equation** at inverting input terminal using input current constraing and Ohm's law to find currents
3. **solve KCL equation** and calculate voltage at op amp's output terminal
4. **compare voltage at op amp's output terminal to the power supply voltages** to determine whether the op amp is actually in its linear region or whether it has saturated 

### 5.3 The Inverting-Amplifier Circuit 


### 5.4 The SUmming-Amplifier Circuit

### 5.5 The Noninverting-Amplifier Circuit

### 5.6 The Difference-Amplifier circuit 

### 5.7 Realistic Model for the Operational Amplifier 
