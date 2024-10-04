### 9.1 The Sinusoidal Source
Sinusoidal Voltge Source (independent or dependent) : produces voltage that varies sinusoidally with time 
Sinusoidal Current Source (independent or dependent) : produces current that varies sinusoidally with time 
- expressed with sin or cos

![image](https://github.com/user-attachments/assets/31dbbda1-5ef2-442d-b689-070c143eab07)

Amplitude : V<sub>m</sub>
Period ( T ) : time required for the function to pass through all its possible values, measured in seconds
Frequency ( f ) : 1 / T , measured in Hz ( cycles per second )

![image](https://github.com/user-attachments/assets/8371ef2b-f1f4-408f-8fa2-eb346008b222)

Angular Frequency : ![image](https://github.com/user-attachments/assets/3afbcc1e-2056-4811-82b7-0dc8c29c393b)
- 2pi rad = 360 degrees

Phase Angle  ![image](https://github.com/user-attachments/assets/8863c845-2b01-4750-8df8-f0a56bb7df4d) : determines the value of the sinusoidal function at t = 0, fixes point on periodic wave where we start measuring time 
- changes shift sinusoidal function but has no effect on apmlitude or angular frequency
  - positive phase angle shifts to the left
  - negative phase angle shifts to the right 

![image](https://github.com/user-attachments/assets/1252376a-9c28-4e54-9bc6-365f0373f299)

rms value of a period function is the squeare root of the mean value of the squared function 
![image](https://github.com/user-attachments/assets/7b5c133f-d353-4582-98a4-586df7033b73)
![image](https://github.com/user-attachments/assets/faa31048-a08e-4a0c-8d1b-1628772ea45f)

RMS Value of a Sinusoidal Voltage Source ![image](https://github.com/user-attachments/assets/351ff6c1-2648-4a6a-b4cc-4133dfa7fa56)

### 9.2 The Sinusoidal Response 
Transient Component : decays to zero as t -> 0 
Steady-State Component : persists as long as the switch remains closed and the source continues to supply the sinusoidal voltage 

Four important characteristics of the steady-state solution
1. Steady-state solution is a cosine function, just like the circuits source
2. Frequency of the solution is identical to frequency of the source
3. Maximum amplitude of the steady-state response differs from the maximum amplitude of the source
- maximum amplitude of the currnet is ![image](https://github.com/user-attachments/assets/b62d1c50-ad26-4c93-8c10-af852ec3f748) while maximum amplitude of the source is V<sub>m</sub>
4. Phase angle of the steady-state response differs from the phase angle of the source 

### 9.3 The Phasor 
Phasor : complex number that carries the amplitude and phase angle information of a sinusoidal function 
Euler's Identity ![image](https://github.com/user-attachments/assets/44d23ca8-5f17-4cfd-96d1-7263969eea63)
- cos is real part of exponential ![image](https://github.com/user-attachments/assets/14d008f5-5394-4a39-b408-bc8460ad60b0)
- sin is imaginary part of exponential ![image](https://github.com/user-attachments/assets/1ee74304-1977-471b-a10b-4da72564d103)
![image](https://github.com/user-attachments/assets/402abcc5-98d3-4ad2-8e00-68abe31a5aba)

![image](https://github.com/user-attachments/assets/2fe1f170-2934-4902-ab49-5ddaadf79bff)
Phasor Representation (phasor transform) : ![image](https://github.com/user-attachments/assets/eaabf172-5dad-4d6c-b039-5bfadf3eca60)
![image](https://github.com/user-attachments/assets/28670203-e109-42f4-87d8-02d901dba25b)

Frequency Domain : complex-number domain ( phasor transform transfers the sinusoidal function from time domain to complex-number domain )
![image](https://github.com/user-attachments/assets/f06085ee-77bb-428c-9cd2-338a311d197d)
![image](https://github.com/user-attachments/assets/934fa8ad-e19b-43e2-8a73-a4923d5e1e4a)

Inverse Phasor Transform ![image](https://github.com/user-attachments/assets/5c6f708b-d0d0-4e32-adbd-dc4986bdad93)

### 9.4 The Passive Circuit Elements in the Frequency domain 
2 Step process to apply phasor transform in circuit analysis 
1. Establish relationship between phasor current and phasor voltage at terminals of the passive cicuit elements
2. Develop phasor-domain version of Kirchhoff's laws

V-I Relationship for a Resistor 
![image](https://github.com/user-attachments/assets/3019244c-1eef-493e-926a-81441566d111) ![image](https://github.com/user-attachments/assets/f8d6721b-2665-409d-8b39-b64ef1968385)
where  is the maximum amplitude of the current in amperes and  is the phase angle of the current.

![image](https://github.com/user-attachments/assets/6b718d99-2d9e-4fbd-999c-abce1398bf5c)

V = RI relationship between phasor voltage and phasor current for a resistor 

In Phase : both waves reach corresponding values on their respective curves at the same time

V-I Relationship for an Inductor 
![image](https://github.com/user-attachments/assets/c3ad855e-dcb5-46cf-b087-099aa081e50b)

Because ![image](https://github.com/user-attachments/assets/fb0390db-0838-46a6-8f3c-bf8059c9a73c)
Then
![image](https://github.com/user-attachments/assets/c8cfdf30-5056-4ce5-affb-ba1839c603e8)
![image](https://github.com/user-attachments/assets/684d99fe-0e1b-4437-b7a1-85a10f22d573)

Voltage can lead or lag current, in this case voltage reaches its negative peack 90 degrees before current reaches its negative peak so the voltage leads current by 90 degrees

V-I Relationship for a Capacitor 
![image](https://github.com/user-attachments/assets/b32d9562-414f-480e-b5e4-215676e90b83)

Impedance : ![image](https://github.com/user-attachments/assets/786411d8-7b30-4641-b706-b38617d9fe2d)
- Z represents the impedance of the circuit element
    - Resistor Impedance  = R
    - Inductor Impedance = ![image](https://github.com/user-attachments/assets/6c8ac78c-0b85-4b45-9f63-675c7c9b7bfd)
    - Mutual Inductance Impedance = ![image](https://github.com/user-attachments/assets/af1595ea-c180-4ff6-ae7f-0cb73cc0510b)
    - Capacitor Impedance = ![image](https://github.com/user-attachments/assets/da53e9cb-b079-44a1-b114-245759bd6d37)
Reactance : imaginary part of impedance
![image](https://github.com/user-attachments/assets/61f14a74-f1cc-4934-8e23-dc7aff6c567c)

### 9.5 Kirchhoff’s Laws in the Frequency Domain
KVL in the Frequency Domain ![image](https://github.com/user-attachments/assets/6e560a9a-6220-4226-abe7-d0a2d2b13a5f)
- voltage law with phasor voltages 
KCL in the Frequency Domain ![image](https://github.com/user-attachments/assets/0c090bee-dcff-499a-a6a2-8f8033b9b331)
- current law with phasor representations of individual currents 

### 9.7 Source Transformations and Thévenin–Norton Equivalent Circuits
Source Transformation in the frequency domain 
![image](https://github.com/user-attachments/assets/2b5c4d63-a887-465c-b443-c04a06fcf3b4)

Thevenin equivalent circuit in frquency-domain 
![image](https://github.com/user-attachments/assets/56b070a4-77cb-4353-87a5-28e14791efc0)

Norton equivalent circuit in frquency-domain 
![image](https://github.com/user-attachments/assets/9bdef8f3-7f95-4904-935f-e8cd160ed00e)

### 9.8 The Node-Voltage Method
Modifications
- if circuit is in time domain it must be transformed to the appropriate frequency domain
    - To do this, transform known voltages and currents to phasors, replace unknown voltages and currents with phasor symbols, and replace the component values for resistors, inductors, mutually coupled coils, and capacitors with their impedance values.
- Find values of known voltage and current phasors of interest
- Apply inverse phasor transform to the voltage and current phasors to find the steady-state values of the correspondign voltage and currents in the time domain 

### 9.9 The Mesh-Current Method
If a problem begins with a circuit in the time domain it needs to be transformed into the frequency domain. 
![image](https://github.com/user-attachments/assets/f13f2547-bc6a-4a7f-983d-a0c175443466)
The Mesh Current Method can be used to find the mesh-current phasors 
Apply inverse phasor transform to the phasor voltages and currents to find the steady-state voltage and currents in the time domain 
