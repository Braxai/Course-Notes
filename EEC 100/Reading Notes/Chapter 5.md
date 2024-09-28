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

![image](https://github.com/user-attachments/assets/af540405-67fd-4e09-954a-499422be6c27)
- ideal op amp
- two resistors
- voltage source
- short circuit connecting noninverting input terminal and common node

Inverting-Amplifier Equation : ![image](https://github.com/user-attachments/assets/bb50858e-083c-43ef-84fc-375171753169)
- valid if op amp is operating in its linear region
![image](https://github.com/user-attachments/assets/a5188da6-6fcc-44d8-84d1-65c5bd17a24e)

Open Loop : if feedback path is opened amplifier is operating open loop 
- open-loop gain : value of A

### 5.4 The Summing-Amplifier Circuit
![image](https://github.com/user-attachments/assets/dfe097a7-81e3-4a70-b3f4-ca56ba53c024)
- output voltage is an inverted, scaled sum of the voltages applied to the input of the amplifier

Inverting Summing-Amplifier Equation : ![image](https://github.com/user-attachments/assets/4ddcaf82-d727-406a-99c0-09e06c9c045b)

If  ![image](https://github.com/user-attachments/assets/bae8ca24-f027-47f0-8a79-0aa3508450d9) then ![image](https://github.com/user-attachments/assets/d8ef01a6-47ea-4d30-a39c-7036f7b05098)

If R<sub>f</sub> = R<sub>s</sub> then ![image](https://github.com/user-attachments/assets/c3a83f70-facb-46f2-a7e5-35afd9496e28)

The number of input voltages can be decreased or increased as needed

### 5.5 The Noninverting-Amplifier Circuit
![image](https://github.com/user-attachments/assets/96dd90dd-f160-45e9-88c0-14ae5bae8e2c)

Noninverting-Amplifier Equation : ![image](https://github.com/user-attachments/assets/98016c07-ec05-42a5-b92e-e441ea1ac523)

### 5.6 The Difference-Amplifier circuit 
![image](https://github.com/user-attachments/assets/17684bde-d972-418a-ac13-b54cb7076ba1)
Output voltage is proportional to difference between the two input voltages 

Difference-Amplifier Equation : ![image](https://github.com/user-attachments/assets/33b8076c-f30a-42be-b27a-07d2d83176c7)
Simplified when ![image](https://github.com/user-attachments/assets/90dc579f-37c2-4bb9-95ba-ec7b460d2fa4) to ![image](https://github.com/user-attachments/assets/ad0bbb72-0349-4427-90b6-8ffa704a651d)

Differential Mode Input : difference between the two input voltages 
Common Mode Input : average of two input voltages 
![image](https://github.com/user-attachments/assets/3611aaa6-3c3d-4e4d-bcfc-388536d3b866)
- A<sub>cm</sub> : common mode gain
- A<sub>dm</sub> : differential mode gain
![image](https://github.com/user-attachments/assets/18a2c06e-2f91-435f-8906-7ad95ee2d962)
![image](https://github.com/user-attachments/assets/df683fb6-820f-4b1b-8a37-263ad7e5d448)



### 5.7 Realistic Model for the Operational Amplifier 
