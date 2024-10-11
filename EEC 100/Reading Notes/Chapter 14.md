# Frequency-Selective Circuits 

## Introduction 
Frequency Response : result of varying source frequency on circuit voltages and currents
  - varying frequency of a sinusoidal source does not change element types or connections but does change the capacitor and inductor impedances because these impedances are functions of frequency

Frequency-Selectir Circuits : output signals reside within a desired frequency range, excluding all other frequencies that appear in the circuits input 
  - Also called filters because they filter out certain input signals on the basis of frequency
  - Attenuate : weaken or lessen the efect of any input signals with freq outside desired freq band

## Preliminaries  

Transfer function ![image](https://github.com/user-attachments/assets/b3f547bb-ad13-4593-b3a6-663d627db313)

Passband : signals passed from input to output fall within this band of frequencies 

Stopband : signals not in a circutis passband are in the stopband

Frequency Response Plot : shows a circutis transfer function (amplitude and phase) change as the source frequency changes
- A graph of ![image](https://github.com/user-attachments/assets/464be842-08ed-4711-a0c2-fcad77f4988e) versus frequency  called the magnitude plot.
- A graph of ![image](https://github.com/user-attachments/assets/ffc18b92-b345-4d99-bab6-7675a144e97a) versus frequency  called the phase angle plot.

Cuttoff Frequency : separates passband and stopband
- Low-Pass Filter : passes signals at frequencies lower than the cutoff frequency from the input to the output 
- High-Pass Filter : passes signals at frequencies higher than the cutoff frequency 
- Bandpass Filter : passes source voltage to output only when the source frequency is within the band defined by the two cutoff frequencies
- Bandreject Filter : passes source voltage to output only when the source frequency is outside the band defined by the two cutoff frequencies
- Passive Filter : behavior depends only on passive elements (resistors, capacitors, and inductors)

## Low-Pass Filters
Two circuits that behave as low-pass filters are series RL and RC circuits

### Series RL Circuit Qualitative Analysis 
Inductor Impedance : jwL
- low frequencies : wl << R
- high frequencies : wl >> R

![image](https://github.com/user-attachments/assets/aa5716a4-884a-4fb8-9c0f-1946aee46d30)
![image](https://github.com/user-attachments/assets/f5efd99e-d198-4c4c-892f-e991bda6e713)

### Defining Cutoff Frequency
![image](https://github.com/user-attachments/assets/f3c36335-3c1b-4cc4-8994-bd7534a1d6c3)
- Hmax : maximum magnitude of the transfer function
- Load voltage max wen magnitude of circuit's transfer function is also a maximum : ![image](https://github.com/user-attachments/assets/c2f7a01f-b3d4-49f4-96c4-3fcaa6d0d614)

### Series RL Circuit Quantitative Analysis 
![image](https://github.com/user-attachments/assets/9b84b3f8-e0df-4bbd-a7f7-85014e7db0a7)

![image](https://github.com/user-attachments/assets/bde580ea-c320-4116-9b4c-be3b82a3f1eb)

**Cutoff Frequency for RL Filters** 
![image](https://github.com/user-attachments/assets/fbe59b71-404b-4175-9f03-c7941aa05693)

### Series RC Circuit 
Series RC low-pass filter ![image](https://github.com/user-attachments/assets/52659c2f-360c-4f79-9af4-9e47f3d7a631)
- Fucntions as a low-pass filter

Transfer Function for Low-Pass Filters 
![image](https://github.com/user-attachments/assets/a3c74202-dd80-4148-ac8f-ba662dd61dc8)

### Relating Frequency Domain to the Time Domain 
Time constant 
- RL circuit : L/R
- RC circuti : RC
![image](https://github.com/user-attachments/assets/cd2b97ff-d72e-4046-8b77-92b73e13c7dc)

## High-Pass Filters 

### Series RC Circuit 
Output voltage defined across resistor (capacitor in low-pass) 
![image](https://github.com/user-attachments/assets/2369f222-166d-4732-b607-4a9aa6d58c4d)

![image](https://github.com/user-attachments/assets/0e3bd3f0-452f-40c6-8cbb-0940441c01c7)
![image](https://github.com/user-attachments/assets/cf6041b5-411e-4930-9f25-1d713dfedf32)
![image](https://github.com/user-attachments/assets/9d10af46-352b-42fe-83ce-45cf887b5778)

Cutoff Frequency for series RC circuit
![image](https://github.com/user-attachments/assets/cb9740a3-e8c8-4121-b14a-d7809d83b459)

Transfer Function for High-Pass Filters 
![image](https://github.com/user-attachments/assets/b05d03a4-18dd-41dc-9c3f-b1e88dd29157)

## Bandpass Filters 

### Center Frequency, Bandwidth, and Quality Factor 
- center frequency ![image](https://github.com/user-attachments/assets/cfead99f-882a-4fb0-bf72-c40cf26fb3f2) : frequency for which a circuits transfer function is purely real
  - resonant frequency
- Bandwidth ![image](https://github.com/user-attachments/assets/87765393-7416-4d0c-b3e6-531732b739c3) : width of passband
- Quality Factor Q : ratio of center frequency to the badnwidth

### Series RLC Circuit 
![image](https://github.com/user-attachments/assets/60f442a6-1346-4b54-9e8a-11de300974ab)
![image](https://github.com/user-attachments/assets/75dbab66-c836-496e-9c3e-3e48bbc22a47)
![image](https://github.com/user-attachments/assets/11e2cef3-a03f-4d98-93f8-c0f857dd002c)
![image](https://github.com/user-attachments/assets/0498bd1e-2488-4afd-a4ba-e937c5c120ae)
![image](https://github.com/user-attachments/assets/a19b8aa2-5da4-42f1-a5cd-6fc3bf44fde7)

Center Frequency : ![image](https://github.com/user-attachments/assets/a75dffdd-eade-4b89-9551-6c3a274b5e0b)

![image](https://github.com/user-attachments/assets/9ece56c1-28db-4813-9eef-91e4ee86eec7)

![image](https://github.com/user-attachments/assets/d539a56d-8b8e-41fe-ad56-dd69a04ec4d2)

![image](https://github.com/user-attachments/assets/edbc361d-9403-4ca8-83e3-15a84dc1f919)

![image](https://github.com/user-attachments/assets/f3f8bdec-049f-4251-880f-d468d5785339)

![image](https://github.com/user-attachments/assets/df7ecee9-8259-434f-8b44-1e8076532fff)

![image](https://github.com/user-attachments/assets/b5710250-d9e0-4f8d-be11-e8ef2b02120e)

![image](https://github.com/user-attachments/assets/4c0c8678-31ac-47e1-9a07-bb7ad8dcfa14)

### Relating Frequency Domain to the Time Domain
Neper frequency alpha and resonant frequency omega o 
![image](https://github.com/user-attachments/assets/1209d64e-d853-4a05-b6f5-fd930b9aaa42)

bandwidth of neper frequency ![image](https://github.com/user-attachments/assets/1025d5d2-6016-4590-8e0a-eaed0814d513)

## Bandpassreject Filters 

### RLC Circuit 
![image](https://github.com/user-attachments/assets/1128437b-54d7-43eb-870e-03e662514cb2)

Frequency Response Plot for series RLC bandreject filter circuit 
![image](https://github.com/user-attachments/assets/e5a6b69e-d182-49f0-a029-87b31cb8ff79)

![image](https://github.com/user-attachments/assets/9d6ab848-0afd-4081-acdb-712d862aee67)

