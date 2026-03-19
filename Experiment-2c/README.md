Aim:

To design and analyze a CMOS common-source amplifier with active load using 180 nm technology and determine the MOSFET widths (W/L) for a given drain current. The circuit is verified using DC, transient, and AC simulations in LTspice.


Theory:

The given circuit is a CMOS common-source amplifier with an active load. It consists of:

M1 (NMOS): Input transistor

M2 (NMOS): Current source for biasing

M3 (PMOS): Active load

When an input voltage is applied to the gate of M1, it controls the drain current flowing through it. This current flows through the PMOS load (M3), producing an output voltage. Since the PMOS provides high output resistance, small input variations produce large output variations, resulting in amplification.

The drain current in saturation is given by:

ID = (1/2) μ Cox (W/L) (Vov)^2

where Vov = VGS − VTH

Voltage gain is given by:

Av = −gm × Rout


Circuit diagram:
<img width="1874" height="925" alt="Circuit" src="https://github.com/user-attachments/assets/89441bb2-b928-4460-912b-a792928db542" />


Calculations:

Given Parameters

VDD = 1.2 V
L = 0.18 µm
tox = 4.1 × 10⁻⁹ m

Assume,
ID = 200 µA
Vov = 0.15 V

ε = 3.9 × 8.854 × 10⁻¹² = 3.45 × 10⁻¹¹ F/m

Cox = ε / tox
Cox = 3.45 × 10⁻¹¹ / 4.1 × 10⁻⁹
Cox = 8.41 × 10⁻³ F/m²

Mobility:
μn = 0.02738 m²/Vs
μp = 0.01157 m²/Vs

Threshold Voltages:
VTHn = 0.366 V
VTHp = 0.39 V

Channel Length Modulation:
λn = 0.1
λp = 0.12

Input Voltage Calculation

For NMOS (M1):
VGS = VTHn + Vov
VGS = 0.366 + 0.15 = 0.516 V

Vin ≈ 0.516 V

From simulation: Vin ≈ 0.816 V

For PMOS (M3):
VSG = |VTHp| + Vov
VSG = 0.39 + 0.15 = 0.54 V

VG = VDD − VSG
VG = 1.2 − 0.54 = 0.66 V

MOSFET Width Calculation

NMOS (M1 & M2):
W/L ≈ 77.2
W = 77.2 × 0.18 = 13.9 µm

PMOS (M3):
W/L ≈ 183.3
W = 183.3 × 0.18 = 33.0 µm

Theoretical Results

M1 (NMOS): 13.9 µm
M2 (NMOS): 13.9 µm
M3 (PMOS): 33.0 µm

Gain Calculation

Transconductance:
gm = 2ID / Vov
gm = (2 × 200 × 10⁻⁶) / 0.15
gm = 2.67 mS

Output Resistance:
ro1 = 1 / (λn ID) = 50 kΩ
ro3 = 1 / (λp ID) ≈ 41.67 kΩ

Rout = ro1 || ro3 ≈ 22.7 kΩ

Voltage Gain:
Av = gm × Rout
Av = (2.67 × 10⁻³) × (22.7 × 10³)
Av ≈ 60.6 V/V

Gain ≈ 35.6 dB


Operating point:
.op
<img width="1919" height="924" alt="Operating point" src="https://github.com/user-attachments/assets/8148f25d-cc5a-40e2-a37c-eec27619a3f1" />
Proper DC biasing achieved

Transient Analysis:
.tran 5m
<img width="1919" height="923" alt="Transient analysis" src="https://github.com/user-attachments/assets/9736edb8-f90d-490e-be7e-b8ab6cbaade6" />
Output waveform is amplified

AC Analysis:
.ac dec 10 10 100G
<img width="1919" height="925" alt="AC Analysis" src="https://github.com/user-attachments/assets/ef19db5d-89ee-4d71-a0c5-fdd14d768dfc" />
<img width="1908" height="931" alt="AC Analysis 3dB" src="https://github.com/user-attachments/assets/8834e7db-6673-4089-85d1-9afb840bbee1" />

Gain ≈ 21 dB

Bandwidth ≈ 25 MHz

Procedure:

Draw the CMOS amplifier circuit in LTspice

Set VDD = 1.2 V

Apply input signal: SINE(0.816 10m 1k)

Assign MOSFET sizes:

NMOS → W = 13.9 µm, L = 0.18 µm

PMOS → W = 33.0 µm, L = 0.18 µm

Include model file: .lib tsmc018.lib


MOSFET widths:
M1 = 1103.8765 µm
M2 = 1103.8765 µm
M3 = 100.8424 µm

Comparision:

Gain

Theoretical = 35.6 dB
Practical = 21 dB


Conclusion:

The CMOS amplifier was successfully designed and analyzed. Theoretical calculations provided initial estimates, while simulation results reflected practical device behavior. The observed differences highlight the importance of considering non-ideal effects in CMOS design.


Inference:

The performance of the amplifier depends on parameters such as overdrive voltage, transconductance, and output resistance. Practical results differ from theoretical predictions due to real device effects, emphasizing the importance of simulation in circuit design.

The differences between theoretical and simulated results arise due to:

Short-channel effects

Mobility degradation

Velocity saturation

Channel length modulation

Parasitic capacitances

Low overdrive voltage (0.15 V) also results in larger transistor widths.
