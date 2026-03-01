Aim:
To design and analyze a Common Source (CS) amplifier using 180nm CMOS technology with PMOS active load.
To determine:
1. Operating Point
2. Voltage Gain
3. Frequency Response
4. Bandwidth

Given,
VDD = 1.2 V
Power ≤ 0.4 mW
CL = 0.5 pF
Technology = 180 nm
Vth(n) = 0.36 V
Vth(p) = 0.39 V
Assume,
ID = 200 µA
Vov = 0.25 V

Circuit diagram:
<img width="1517" height="871" alt="Circuit2a" src="https://github.com/user-attachments/assets/831f96a8-4993-4e5b-a52a-2b032589d237" />

Theory:
A Common Source amplifier provides high voltage gain
with 180 degree phase shift.

NMOS acts as amplifying transistor.
PMOS acts as active load.

Overdrive voltage:
Vov = VGS - VTH

Transconductance:
gm = 2ID / Vov

Output resistance:
ro = 1 / (λ ID)

Voltage Gain:
Av = -gm (ro_n || ro_p) / (1 + gmRs)

Bandwidth:
BW = fH - fL

To find Rs:
Desired source voltage (VS) = 0.2 V
Drain current ID = 200 µA
VS = ID × RS
RS = VS / ID
RS = 0.2 / (200 × 10^-6)
RS = 0.2 / 0.0002
RS = 1000 Ω

To ensure proper biasing and keep NMOS in saturation region.
VDS ≥ VOV
We assumed,
VOV = 0.25 V
With RS creating VS = 0.2 V,
we maintain sufficient VDS margin for saturation.

Design Calculations:
P = VDD × ID
P = 1.2 × 200µA
P = 0.24 mW <0.4mW

VGS = Vov + VTH
VGS = 0.25 + 0.36
VGS = 0.61 V

Vout ≈ (VDD / 2)+VS
Vout ≈ (1.2 / 2)+0.2
Vout ≈ 0.8 V
Assume, VS=0.2V
VDS = Vout − VS
VDS = 0.8 − 0.2
VDS = 0.6 V

For PMOS:
VSD = VDD − Vout
VSD = 1.2 − 0.8048
VSD = 0.3952 V
VOV(p) = 0.25 V
Since VSD > VOV(p),
PMOS operates in saturation region.

gm = 2ID / Vov
gm = (2 × 200µA) / 0.25
gm = 1.6 mS

Assume λ = 0.1
ro = 1 / (λ ID)
ro = 1 / (0.1 × 200µA)
ro = 50 kΩ
(ro_n || ro_p) ≈ 25 kΩ

Av = -gm (ro_n || ro_p) / (1 + gmRs)
Av = (-1.6mS × 25kΩ) / (1 + (1.6mS × 1kΩ))
Av ≈ -15.38 V/V
Av(dB) = 20 log(15.38)
Av(dB) = 23.74 dB

Procedure:
1. Draw schematic in LTspice.
2. Place NMOS and PMOS transistors.
3. Set VDD = 1.2 V.
4. Apply bias voltage 0.56 V to PMOS gate.
5. Apply input signal:
   SINE(0.81 10m 1k)
6. Add Rs = 1 kΩ.
7. Include commands:
   .op
   .tran 5m
   .ac dec 100 10 100G
8. Run Operating Point analysis.
9. Run Transient analysis.
10. Run AC analysis.

Operating Point:
<img width="1737" height="926" alt="OP2a" src="https://github.com/user-attachments/assets/e178e038-7811-4f4f-b2a5-c433e3dc3f66" />

VDD = 1.2 V
Vbias = 0.56 V
Vout = 0.8048 V
ID(M1) = 200 µA
ID(M2) = 200 µA
Transistors operating in saturation region.
ID=un*Cox*(W/L)*(Vov)^2*(1/2)
Theoritical calculated width, W for NMOS = 4.9954um, W for PMOS = 11.823um.
In Simulation for ID=200uA and Vout=0.8V , W for NMOS = 29.995um, W for PMOS = 26.023um

Transient Analysis:
<img width="1914" height="926" alt="Trans2a" src="https://github.com/user-attachments/assets/a62ab1a9-6e83-43d0-88f2-b63e86d255d1" />

Input:
SINE(0.81 10m 1k)
10m = Peak amplitude
Vin(p-p) = 20 mV
Measured Vout ≈ 123 mV (approx)
Av = Vout(p-p) / Vin(p-p)
Av ≈ 6.30 V/V
Av(dB) ≈ 16 dB

AC Analysis:
<img width="1919" height="869" alt="AC2a" src="https://github.com/user-attachments/assets/0784beae-ebf6-4414-acc5-bd1fc584f758" />
<img width="1909" height="920" alt="ACdB2a" src="https://github.com/user-attachments/assets/a3cd6394-2641-44fe-ad30-3149fa395352" />

Midband Gain ≈ 16 dB
High cutoff frequency (fH) = 376.34 MHz
Low cutoff frequency (fL) ≈ 0 Hz
Bandwidth:
BW = 376.34 MHz

Comparision:
Theoretical Gain = 23.74 dB
Simulated Gain = 16 dB
Theoretical Av = 15.38 V/V
Simulated Av = 6.30 V/V
Bandwidth = 376 MHz
Power = 0.24 mW

Inference:
Simulated gain is lower due to:
1. Channel length modulation
2. Source degeneration resistance
3. Parasitic capacitances
4. Non-ideal MOS effects
AC gain differs from transient gain due to
small signal assumption in AC analysis.

Result:
The Common Source amplifier using 180nm technology
was successfully designed and simulated.
Gain obtained = 16 dB
Bandwidth = 376 MHz
Power consumption = 0.24 mW
The design satisfies given specifications.
