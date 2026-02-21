# Experiment 1
## DC, AC and Transient Analysis of Common Source Amplifier

### Aim
To perform DC analysis, AC analysis and Transient analysis of a Common Source (CS) amplifier using LTspice.

### Theory
A Common Source (CS) amplifier is a single-stage MOSFET amplifier configuration in which the input signal is applied to the gate terminal and the output is taken from the drain terminal, while the source terminal is connected to ground. It is one of the most widely used basic amplifier configurations in analog integrated circuit design.
In CS configuration, when the input voltage at the gate increases, the gate-to-source voltage (VGS) increases. This increases the drain current (ID), which causes a larger voltage drop across the drain resistor (RD). As a result, the output voltage at the drain decreases. Therefore, the output signal is inverted with respect to the input signal, producing a 180° phase shift.
For proper amplification, the MOSFET must operate in the saturation region. The condition for saturation is:

VDS ≥ (VGS − VT)

In saturation region, the drain current is given by:

ID = (1/2) μn Cox (W/L) (VGS − VT)²

where:
μn = Electron mobility  
Cox = Oxide capacitance per unit area  
W = Channel width  
L = Channel length  
VT = Threshold voltage  

The small-signal voltage gain of a CS amplifier is:
Av = − gm RD

where:
gm = transconductance = 2ID / Vov  

Vov = overdrive voltage = (VGS − VT)  

The negative sign indicates phase inversion.

The bandwidth of the amplifier depends on parasitic capacitances such as gate-to-source capacitance (Cgs), gate-to-drain capacitance (Cgd) and load capacitance (CL). At higher frequencies, these capacitances reduce the gain, producing a roll-off in the frequency response.
In this experiment, a CS amplifier is designed using 180 nm CMOS technology with VDD = 1.2 V. The transistor dimensions are chosen to satisfy power constraint and required drain current. DC analysis determines operating point, transient analysis verifies amplification, and AC analysis determines gain and bandwidth.

### Circuit Diagram
![Circuit](https://github.com/user-attachments/assets/40ac389c-e230-4073-8d82-8e466aebb94b)

### Procedure
1. Open LTspice software.
2. Draw the common source amplifier circuit using NMOS transistor.
3. Set Vdd = 1.2V.
4. Apply sine input at gate terminal.
5. Perform DC analysis to obtain operating point.
6. Perform transient analysis to observe output waveform.
7. Perform AC analysis to obtain frequency response.

### Operating Point Analysis (.op)
Operating point analysis is performed to determine the DC biasing conditions of the MOSFET such as drain current (Id), gate voltage (Vg), source voltage (Vs) and output voltage (Vout).  
This analysis ensures that the transistor is operating in the correct region for amplification.
![Op](https://github.com/user-attachments/assets/0353cf29-49fb-49a8-9738-db5a3e92bb16)

### Design Calculations

Given:
VDD = 1.2 V  
Power constraint P ≤ 0.4 mW  
CL = 0.5 pF  
Ln = 360 nm  

Assume drain current:
Id = 200 µA  

Power check:
P = VDD × Id  
= 1.2 × 200µA  
= 0.24 mW ≤ 0.4 mW ✔

Output voltage condition:
Vout = VDD − Id RD  

For maximum swing,
Vout = VDD / 2 = 0.6 V  

0.6 = 200 × 10⁻⁶ × RD  
RD = 3 kΩ  

MOSFET current equation:

Id = (μn Cox / 2) × (W/L) × (VGS − VT)²  

Substituting values and solving:

W ≈ 2.798 µm  

From simulation:
Id ≈ 121 µA  

To obtain Id ≈ 200 µA,
Width adjusted:

W ≈ 5.128 µm

### DC Analysis
DC analysis is performed to determine operating point values like drain current (Id), output voltage (Vout).
![DC Analysis](https://github.com/user-attachments/assets/e82e1a55-7c00-454d-8d3f-d5f2b47456f7)

### Transient Analysis
Transient analysis is performed by applying sine input signal and observing output waveform.
![Transient Analysis](https://github.com/user-attachments/assets/08614768-3e2c-4c6a-b3f7-2a3eb6fbd53b)

### Theoretical Gain Calculation

Av = gm RD  
= (2Id / Vov) × RD  

= (2 × 200µA / (0.7 − 0.366)) × 3k  

Av ≈ 3.59  

Gain in dB:
Av(dB) = 20 log Av  
≈ 11.1 dB

### Practical Gain from Transient Analysis

Vout(p-p) = 0.08217 V  
Vin(p-p) = 0.01957 V  

Av = Vout / Vin  
= 4.1987  

Av(dB) = 20 log Av  
≈ 12.16 dB

### AC Analysis
AC analysis is performed to determine gain and bandwidth of the amplifier.
![AC Analysis](https://github.com/user-attachments/assets/b4c8603a-5e8b-4a1e-9364-f0175b06512c)
![AC Analysis3dB](https://github.com/user-attachments/assets/fad595ff-4f29-49b6-972a-f86828fe79a7)

### Bandwidth Calculation

BW = fH − fL  

Since fL ≈ 0,  
BW ≈ fH  

BW ≈ 17.19 GHz

### Result
The Common Source (CS) amplifier was successfully designed using NMOS transistor in 180 nm CMOS technology and simulated in LTspice.
From DC analysis, the operating point of the MOSFET was obtained and the transistor was verified to operate in saturation region.

From transient analysis:
Vin(p-p) ≈ 0.01957 V  
Vout(p-p) ≈ 0.08217 V  

Voltage gain:
Av ≈ 4.19  
Av(dB) ≈ 12.16 dB  

From AC analysis:
The frequency response of the amplifier was obtained and the bandwidth was found to be approximately 17.19 GHz.
Thus, the CS amplifier provided voltage amplification with phase inversion and satisfactory gain and bandwidth characteristics.

### Conclusion
In this experiment, a Common Source (CS) amplifier was successfully designed and analyzed using 180 nm CMOS technology in LTspice. The transistor dimensions were chosen to satisfy the given power constraint and drain current requirements.  
The DC analysis confirmed that the MOSFET operates in the saturation region, ensuring proper amplification. Transient analysis verified voltage amplification with 180° phase inversion between input and output signals.  
The practical voltage gain obtained from simulation was approximately 12.16 dB, which is close to the theoretical value, validating the design calculations. AC analysis provided the frequency response and bandwidth of the amplifier, demonstrating satisfactory high-frequency performance.  
Thus, the Common Source amplifier effectively provides voltage gain with controlled power consumption and good bandwidth characteristics, making it suitable for analog integrated circuit applications.
