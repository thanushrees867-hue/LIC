Aim: 

To design and analyze a Common Source amplifier
using 180nm CMOS technology with current source load
and to determine:

1. DC Operating Point
2. Gate Bias Voltages
3. Transistor Widths
4. Voltage Gain
5. Frequency Response
6. Saturation Verification

Given:

VDD = 1.2 V

Power ≤ 0.4 mW

CL = 0.5 pF

Technology = 180 nm

Ln = 360 nm

Vth(n) = 0.366 V

Vth(p) = 0.39 V

Circuit diagram:
<img width="1424" height="793" alt="Circuit2" src="https://github.com/user-attachments/assets/f35b8aa3-e4c1-46ae-81c3-ee5b7bc10414" />

Assumed parameters:

ID = 200 µA

VOV = 0.2 V

λn = 0.1

λp = 0.12

Theory:

A Common Source amplifier provides voltage gain
with 180° phase shift.


M1 → Amplifying NMOS

M2 → Current source NMOS

M3 → PMOS active load


In saturation:

ID = (µCox /2)(W/L)(VOV)^2

gm = 2ID / VOV

ro = 1 / (λID)

Voltage gain:

Av = -gm (ro1 || ro3)


DC Design Calculations:


1. Power Verification:

P = VDD × ID

P = 1.2 × 200µA

P = 0.24 mW

Since 0.24 mW < 0.4 mW

Power condition satisfied.


2. Gate voltage Calculations:

For M1,

VOV = VGS − VTH

VGS = 0.2 + 0.366

VGS = 0.566 V

Assume VS1 = 0.3 V

VG1 = VGS + VS1

VG1 = 0.566 + 0.3

VG1 = 0.866 V

For M2,

VS2 = 0 V

VGS2 = 0.566 V

VG2 = 0.566 V

For M3(PMOS), 

0.2 = VSG − 0.39

VSG = 0.59 V

VG3 = 1.2 − 0.59

VG3 = 0.61 V


3. Output Voltage:

Vout ≈ VDD / 2

Vout = 1.2 / 2

Vout = 0.6 V


4. Saturation Verification:

M1,

VDS1 = 0.6 − 0.3

VDS1 = 0.3 V

0.3 ≥ 0.2 ✔

M2,

VDS2 = 0.3 V

0.3 ≥ 0.2 ✔

M3,

VSD3 = 1.2 − 0.6

VSD3 = 0.6 V

0.6 ≥ 0.2 ✔

5. Small Signal Parameters:

gm = 2ID / VOV

gm = (2 × 200µA) / 0.2

gm = 2 mS

ro1 = 1 / (0.1 × 200µA)

ro1 = 50 kΩ

ro3 = 1 / (0.12 × 200µA)

ro3 = 41.66 kΩ

Rout = ro1 || ro3

Rout ≈ 22.7 kΩ


6. Theoretical gain:

Av = (-gm*(ro1||ro3))/(1+(gm*ro2))

Av ≈ -0.45 V/V

Av(dB) = 20 log(0.45)

Av(dB) ≈ -6.9357 dB


7. Width Calculations:

NMOS,

ID = (µnCox /2)(W/L)(VOV)^2

200µA = (µnCox /2)(W/360nm)(0.2)^2

Wn ≈ 7.8 µm

PMOS,

200µA = (µpCox /2)(W/360nm)(0.2)^2

Wp ≈ 18.47 µm


Operating Point:

<img width="1718" height="797" alt="OP2" src="https://github.com/user-attachments/assets/23c6ee4c-3e89-4652-a560-8b789effc4e7" />

ID ≈ 200 µA

Vout ≈ 0.6 V

VS1 ≈ 0.3 V

VG1 = 0.866 V

VG2 = 0.566 V

VG3 = 0.61 V

Biasing is verified with this values


Transient Analysis:

<img width="1919" height="944" alt="Trans2" src="https://github.com/user-attachments/assets/57b33b1a-c900-44a6-ba85-c56133f051fa" />

SINE(0.81 10m 1k)

Vin(p-p) = 20 mV

Vout(p-p) ≈ 41.89 mV

Av ≈ 2.094 V/V

Av(dB) ≈ 6.4 dB


AC Analysis:

<img width="1906" height="886" alt="AC2" src="https://github.com/user-attachments/assets/1b0e1230-a84c-4b14-a840-fdb7c74b4755" />

<img width="1893" height="921" alt="ACdB2" src="https://github.com/user-attachments/assets/24c0e98b-dfa3-46e0-b134-f9f4dfb75791" />

.ac dec 100 10 100G

Midband Gain ≈ 6.4 dB

fH=138.181MHz

fL=0Hz

BW = 138.151MHz    


Inference:

1. All MOSFETs operate in saturation.

2. Power constraint satisfied.

3. Gain reduced due to non-ideal ro,
   channel length modulation and
   parasitic capacitances.

4. AC and transient gains match closely.


Result:

The Common Source amplifier with current source load
was successfully designed using 180nm technology.

Power consumption = 0.24 mW

Simulated Gain ≈ 6.4 dB

All transistors operate in saturation.

Design satisfies given specifications.
