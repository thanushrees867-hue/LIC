Aim:

To design and analyze different configurations of CMOS differential amplifiers, including resistive load, active load, and current mirror-based circuits, and to evaluate their DC operating point, voltage gain, input/output ranges, and overall performance using theoretical calculations and LTspice simulation.


Theory:

The differential amplifier is one of the most important building blocks in analog electronics, widely used in operational amplifiers, communication systems, and signal processing applications. Its primary function is to amplify the difference between two input signals while rejecting any signal that is common to both inputs, known as the common-mode signal. This property makes the differential amplifier highly effective in reducing noise and improving signal accuracy.

A MOS differential amplifier consists of two matched MOSFETs forming a differential pair, a tail current source that provides a constant bias current, and load elements connected at the drains of the transistors. When both input voltages are equal, the circuit operates in a balanced condition where the tail current splits equally between the two transistors. As a result, both drain currents are equal and the output voltages remain the same, producing zero differential output.

When a differential input is applied, such that one input voltage is slightly higher than the other, the symmetry of the circuit is disturbed. The transistor receiving the higher input voltage experiences an increase in gate-to-source voltage, causing it to conduct more current. At the same time, the other transistor conducts less current. Since the total current supplied by the tail current source remains constant, this redistribution of current leads to a difference in output voltages, thereby achieving amplification.

Key current relation:
ID1 + ID2 = ISS

The operation of the differential amplifier depends on the MOSFETs operating in the saturation region. For proper amplification, the drain-to-source voltage must be greater than or equal to the overdrive voltage. When this condition is satisfied, the transistor behaves like a controlled current source.

Saturation condition:
VDS ≥ Vov

The overdrive voltage is a key parameter that determines the operating point of the transistor. It is defined as the difference between the gate-to-source voltage and the threshold voltage.

Overdrive voltage:
Vov = VGS − Vth

The drain current of a MOSFET operating in saturation is given by:

ID = (1/2) kn (W/L) Vov²

where the process transconductance parameter is:

kn = μn Cox,
kp = μp Cox

The oxide capacitance is given by:

Cox = εox / tox

The small-signal behavior of the differential amplifier is characterized using transconductance, which relates the change in drain current to the change in gate voltage.

gm = 2ID / Vov

gm = √(2kn (W/L) ID)

The voltage gain of the differential amplifier depends on the load used in the circuit.

In the resistive load differential amplifier, resistors are used as load elements. The differential current flowing through the transistors produces voltage drops across these resistors, generating the output voltages. This circuit is simple and easy to design, but the gain is limited due to the finite value of resistance and voltage headroom constraints.

Voltage gain (resistive load):
Av = gm RD

Output voltage:
Vout = VDD − ID RD

In the active load differential amplifier, resistors are replaced with PMOS transistors acting as active loads. These transistors often form a current mirror, which increases the effective output resistance and significantly improves the gain. Active loads also utilize supply voltage more efficiently and reduce circuit size.

Voltage gain (active load):
Av = gm ro

In the current mirror based differential amplifier, current mirrors are used for both load and biasing. The current in one branch is mirrored to another, enhancing the output signal and improving differential-to-single-ended conversion. This configuration provides the highest gain due to very high output resistance.

Voltage gain (current mirror load):
Av = gm rout

The performance of the differential amplifier is also characterized by its ability to reject common-mode signals, quantified using the Common Mode Rejection Ratio.

CMRR = Ad / Acm

The behavior of the amplifier depends on the magnitude of the input signal. For small differential inputs, the amplifier operates in the linear region and produces a proportional output. For large inputs, one transistor may turn off while the other carries most of the current, leading to nonlinear behavior and distortion.

Condition for linear operation:
Vid < √2 Vov

Thus, small input signals result in linear amplification, whereas large input signals lead to nonlinear behavior.


Procedure:

1.Open LTspice and create a new schematic.

2.Construct the differential amplifier circuit using NMOS/PMOS transistors as per the given circuit diagram.

3.Set the supply voltages:

VDD = +0.9 V,
VSS = −0.9 V

4.Apply the given node bias voltage:

Set the common source node voltage Vp = -0.7 V

5.Ensure the total power constraint is satisfied:

P ≤ 1.8 mW,
Choose tail current ISS = 1 mA

6.Set transistor channel length:

L = 480 nm

7.Perform hand calculations for:

Drain current,
Load resistance,
Overdrive voltage,
Gain

8.Verify all MOSFETs operate in saturation using:

VDS ≥ Vov

9.Run DC operating point analysis using .op.

10.Perform transient analysis using .tran.

11.Perform AC analysis using .ac.

12.Observe and record output waveforms and gain.


Circuit 1: Differential Amplifier with Resistive Load

Design steps:

1.Construct NMOS differential pair (M1, M2).

2.Connect resistors RD from drains to VDD.

3.Connect a current source (or NMOS M3) as tail current source.

4.Set tail current:
ISS = 1 mA

5.Calculate drain current:
ID = ISS / 2 = 0.5 mA

6.Calculate load resistance using:
RD = VDD / ID = 1.8 kΩ

7.Apply differential inputs Vin1 and Vin2.

Simulation steps:

8.Perform DC analysis to verify:
Output common-mode voltage = 0 V,
Equal current distribution

9.Apply small differential input (e.g., 20 mV) and run transient analysis.

10.Observe linear output waveform.

11.Increase input (e.g., 300 mV) and observe distortion.

12.Perform AC analysis and measure gain.


Circuit 2: Differential Amplifier with Active Load

Design steps:

1.Replace resistors with PMOS transistors (M3, M4) as active loads.

2.Configure PMOS transistors as a current mirror.

3.Use NMOS differential pair (M1, M2).

4.Provide tail current source at the common source node.

5.Ensure proper biasing so that all transistors operate in saturation.

6.Maintain same current constraint:
ISS = 1 mA

Simulation steps:

7.Run DC operating point analysis to verify:
Proper current mirroring,
Output bias point

8.Apply small differential input and observe output.

9.Compare gain with Circuit 1 (should be higher).

10.Perform transient analysis for large input and observe nonlinearity.

11.Run AC analysis and note gain improvement.


Circuit 3: Current Mirror Based Differential Amplifier

Design steps:

1.Use NMOS differential pair (M1, M2).

2.Implement PMOS current mirror as load.

3.Use additional current mirror for biasing if required.

4.Ensure proper matching of transistors.

5.Maintain same supply voltages and current constraints.

6.Verify saturation condition for all transistors using:
VDS ≥ Vov

Simulation steps:

7.Perform DC analysis to confirm:
Correct current mirroring,
Stable operating point

8.Apply differential input and run transient analysis.

9.Observe improved output swing and gain.

10.Compare performance with Circuit 1 and Circuit 2.

11.Perform AC analysis and note highest gain among all circuits.


Design Calculations:

Circuit-1:

<img width="1209" height="1021" alt="4a circuit" src="https://github.com/user-attachments/assets/4db44087-521f-47da-ba29-0bb0fd52047d" />


Given Specifications

VDD = +0.9 V

VSS = -0.9 V

P ≤ 1.8 mW

Vin,CM = 0 V

Vout,CM = 0 V

Vp = -0.7 V

L = 480 nm

Process Parameters

Vth,n = 0.366 V

μn = 273.8094 × 10⁻⁴ m²/V·s = 0.02738 m²/V·s

tox = 4.1 × 10⁻⁹ m

εox = 3.9 × ε0 = 3.9 × 8.854 × 10⁻¹² F/m

Step 1: Power Constraint

Total power:

P = (VDD - VSS) × ISS
  = (0.9 - (-0.9)) × ISS
  = 1.8 × ISS

Given:

P ≤ 1.8 mW

Therefore:

1.8 × ISS ≤ 1.8 mW
ISS ≤ 1 mA

Choose:

ISS = 1 mA

Step 2: Drain Current

ID1 = ID2 = ISS / 2
     = 1 mA / 2
     = 0.5 mA

Step 3: Load Resistance (RD)

For zero output common-mode voltage:

Vout = VDD - ID × RD

Given:

Vout,CM = 0 V

So:
0 = 0.9 - (0.5 mA × RD)

RD = 0.9 / 0.5 mA
   = 1.8 kΩ

Step 4: Source Node Voltage

Given:
Vp = VS = -0.7 V

Step 5: Gate-Source Voltage

VGS = VG - VS
    = 0 - (-0.7)
    = 0.7 V

Step 6: Overdrive Voltage

Vov = VGS - Vth
    = 0.7 - 0.366
    = 0.334 V

Step 7: Oxide Capacitance (Cox)

Cox = εox / tox
    = (3.9 × 8.854 × 10⁻¹²) / (4.1 × 10⁻⁹)
    = 8.42 × 10⁻³ F/m²

Step 8: Process Transconductance Parameter (kn)

kn = μn × Cox
   = 0.02738 × 8.42 × 10⁻³
   = 2.305 × 10⁻⁴ A/V²

Step 9: Width-to-Length Ratio (W/L)

Using MOSFET current equation:

ID = (1/2) × kn × (W/L) × Vov²

Substitute values:

0.5 mA = (1/2) × 2.305 × 10⁻⁴ × (W/L) × (0.334)²

0.0005 = 1.1525 × 10⁻⁴ × (W/L) × 0.1115

0.0005 = 1.285 × 10⁻⁵ × (W/L)

W/L = 0.0005 / 1.285 × 10⁻⁵
    ≈ 38.9

Step 10: Transistor Width (W)

W = (W/L) × L
  = 38.9 × 480 nm
  ≈ 18.7 µm

Practical value used:
W ≈ 21.5 µm (used in LTspice)

Step 11: Transconductance (gm)

gm = 2ID / Vov
   = (2 × 0.5 mA) / 0.334
   = 2.99 mS

Step 12: Voltage Gain (Av)

Av = gm × RD
   = 2.99 mS × 1.8 kΩ
   ≈ 5.4

Step 13: Saturation Check

For M1 and M2:

VDS = VD - VS
    = 0 - (-0.7)
    = 0.7 V

VDS > Vov (0.334 V)
✔ Saturation satisfied

For Tail Transistor (M3):

VDS3 = VS - VSS
     = -0.7 - (-0.9)
     = 0.2 V

VDS3 < Vov
✘ Not in saturation

Final Results
ISS = 1 mA
ID = 0.5 mA
RD = 1.8 kΩ
Vov = 0.334 V
W ≈ 21.5 µm
gm ≈ 2.99 mS
Av ≈ 5.4

Important Observation

Input transistors (M1, M2) operate in saturation.

Tail transistor (M3) does not fully satisfy saturation condition due to limited voltage headroom.

Circuit operates correctly but deviates slightly from ideal current source behavior.


Tail Current Source (M3) Not in Saturation

In the first circuit (differential amplifier with resistive load), the tail transistor (M3) is expected to operate in the saturation region so that it behaves like an ideal current source. However, due to the given bias conditions, this requirement is not fully satisfied.

The source node voltage is given as:

VS = Vp = -0.7 V

The supply voltage is:

VSS = -0.9 V

Therefore, the drain-to-source voltage of the tail transistor is:

VDS3 = VS - VSS
     = -0.7 - (-0.9)
     = 0.2 V

The overdrive voltage of NMOS is:

Vov = VGS - Vth
    = 0.7 - 0.366
    = 0.334 V

For saturation:

VDS ≥ Vov

But here:

0.2 V < 0.334 V

Hence, the tail transistor does not satisfy the saturation condition.

Justification

This occurs due to limited voltage headroom in the circuit. Since the total supply voltage is only 1.8 V (from +0.9 V to −0.9 V), there is insufficient voltage across the tail transistor to maintain saturation while also keeping the input transistors properly biased.

Thus, the tail transistor operates in the linear region, behaving like a resistor instead of an ideal current source. However, it still approximately maintains the required current, allowing the circuit to function correctly with slight deviation from ideal behavior.


Circuit-2: Differential Amplifier with Active Load

<img width="1895" height="1079" alt="4b circuit" src="https://github.com/user-attachments/assets/c99cff59-c9bd-4dbf-9547-e8a2da1a6bb1" />

Given Specifications

VDD = +0.9 V

VSS = -0.9 V

P ≤ 1.8 mW

Vin,CM = 0 V

Vout,CM = 0 V

Vp = -0.7 V

L = 480 nm

Process Parameters

Vth,n = 0.366 V

Vth,p = 0.39 V

μn = 0.02738 m²/V·s

μp = 0.01156 m²/V·s

tox = 4.1 × 10⁻⁹ m

εox = 3.9 × ε0 = 3.9 × 8.854 × 10⁻¹² F/m

Step 1: Power Constraint

P = (VDD - VSS) × ISS
  = 1.8 × ISS

1.8 × ISS ≤ 1.8 mW

ISS ≤ 1 mA

Choose:
ISS = 1 mA

Step 2: Drain Current

ID1 = ID2 = ISS / 2
     = 0.5 mA

Step 3: Source Node Voltage

Vp = VS = -0.7 V

Step 4: NMOS Gate-Source Voltage

VGS,n = VG - VS
      = 0 - (-0.7)
      = 0.7 V

Step 5: NMOS Overdrive Voltage

Vov,n = VGS,n - Vth,n
      = 0.7 - 0.366
      = 0.334 V

Step 6: Oxide Capacitance

Cox = εox / tox
    = (3.9 × 8.854 × 10⁻¹²) / (4.1 × 10⁻⁹)
    = 8.42 × 10⁻³ F/m²

Step 7: Process Parameters

kn = μn × Cox
   = 0.02738 × 8.42 × 10⁻³
   = 2.305 × 10⁻⁴ A/V²

kp = μp × Cox
   = 0.01156 × 8.42 × 10⁻³
   = 9.73 × 10⁻⁵ A/V²

Step 8: NMOS (M1, M2) Sizing

Using:

ID = (1/2) kn (W/L) Vov²

0.5 mA = (1/2) × 2.305×10⁻⁴ × (W/L) × (0.334)²

W/L ≈ 38.9

W ≈ 18.7 µm

✔ Practical value used:

W ≈ 21.5 µm

Step 9: PMOS Active Load Design

For PMOS:

VSG,p = VS,p - VG,p

Since PMOS source is connected to VDD:

VS,p = 0.9 V

To carry same current:

ID = 0.5 mA

PMOS Overdrive Voltage

Vov,p = VSG,p - |Vth,p|

Assume symmetric design:

Vov,p ≈ 0.2 V

PMOS Sizing

ID = (1/2) kp (W/L) Vov²

0.5 mA = (1/2) × 9.73×10⁻⁵ × (W/L) × (0.2)²

0.0005 = 4.865×10⁻⁵ × (W/L) × 0.04

0.0005 = 1.946×10⁻⁶ × (W/L)

W/L ≈ 257

PMOS Width

W = 257 × 480 nm
  ≈ 123 µm

PMOS must be larger than NMOS due to lower mobility

Step 10: Transconductance

gm = 2ID / Vov,n
   = (2 × 0.5 mA) / 0.334
   = 2.99 mS

Step 11: Output Resistance

For active load:

ro ≫ RD

Approximate:

Av = gm × ro

Step 12: Saturation Check

NMOS:

VDS,n = VD - VS ≈ sufficient

✔ In saturation

PMOS:

VSD,p ≥ Vov,p

✔ Must be ensured

Tail Transistor:

VDS3 = 0.2 V < Vov

✘ Not fully in saturation

Final Results

ISS = 1 mA

ID = 0.5 mA

Vov,n = 0.334 V

Wn ≈ 21.5 µm

Wp ≈ 120 µm

gm ≈ 2.99 mS

Av >> Circuit 1

Important Observations

Active load increases output resistance

Gain is much higher than resistive load circuit

PMOS devices must be wider due to lower mobility

Tail transistor still limited by voltage headroom

Circuit provides better efficiency and performance


In the second circuit, which uses a PMOS active load (current mirror configuration), all MOSFETs are ideally expected to operate in the saturation region for proper differential amplification. However, due to circuit constraints and biasing conditions, some MOSFETs may not strictly satisfy the saturation condition.

Saturation Condition

For NMOS:

VDS ≥ Vov

For PMOS:

VSD ≥ Vov

NMOS Transistors (M1, M2)

The source voltage is fixed as:

VS = Vp = -0.7 V

The overdrive voltage is:

Vov = 0.334 V

The drain voltage depends on the PMOS active load. Unlike Circuit 1, the drain is not fixed at 0 V but is controlled by the PMOS current mirror.

Due to this:

VDS = VD - VS

If the PMOS load pulls the drain voltage down:

VD decreases → VDS reduces

When:

VDS < 0.334 V

the NMOS transistors enter the linear region.

Justification

The active load (PMOS current mirror) dynamically controls the drain voltage.

The low supply voltage (±0.9 V) limits the available voltage headroom.

The fixed source voltage Vp=−0.7V reduces the effective VDS.

Hence, NMOS transistors may not always remain in saturation.

PMOS Transistors (Active Load: M3, M4)

For PMOS:

VSD = VS - VD

Here:

VS = VDD = 0.9 V

For saturation:

VSD ≥ Vov,p

However, since the drain voltage is determined by the NMOS operation:

VD increases → VSD decreases

If:

VSD < Vov,p

then PMOS transistors enter the linear region.

Justification

The PMOS devices form a current mirror, so their operation depends on NMOS drain voltage.

Any increase in drain voltage reduces VSD, affecting saturation.

Due to limited voltage headroom, it is difficult to maintain both NMOS and PMOS in saturation simultaneously.

Key Reason

Low supply voltage (±0.9 V) → Limited voltage headroom

This creates a trade-off condition:

If NMOS stays in saturation → PMOS may leave saturation

If PMOS stays in saturation → NMOS may leave saturation

Thus, all transistors cannot be perfectly in saturation at the same time.

Finally,

Due to low voltage headroom and active load interaction, some MOSFETs in Circuit 2 do not strictly satisfy saturation conditions.

This is a practical limitation, not a design error.

The circuit still functions correctly with:
    Proper current steering
    Improved gain compared to Circuit 1
    Acceptable non-ideal behavior


Circuit-3: Current Mirror Loaded Differential Amplifier

<img width="1919" height="1079" alt="4c circuit" src="https://github.com/user-attachments/assets/753d1bb8-1dee-4fdd-9ae9-698ef37824d8" />

Given Specifications

VDD = +0.9 V

VSS = -0.9 V

P ≤ 1.8 mW

Vin,CM = 0 V

Vout,CM = 0 V

L = 480 nm

Process Parameters

Vth,n = 0.366 V

Vth,p = 0.39 V

μn = 0.02738 m²/V·s

μp = 0.01156 m²/V·s

tox = 4.1 × 10⁻⁹ m

εox = 3.9 × ε0 = 3.45 × 10⁻¹¹ F/m

Step 1: Oxide Capacitance

Cox = εox / tox
    = (3.45 × 10⁻¹¹) / (4.1 × 10⁻⁹)
    ≈ 8.42 × 10⁻³ F/m²

Step 2: Process Transconductance Parameters

kn = μn × Cox
   = 0.02738 × 8.42 × 10⁻³
   ≈ 2.305 × 10⁻⁴ A/V²

kp = μp × Cox
   = 0.01156 × 8.42 × 10⁻³
   ≈ 9.73 × 10⁻⁵ A/V²

Step 3: Power Constraint

P = (VDD - VSS) × ISS
  = 1.8 × ISS

1.8 × ISS ≤ 1.8 mW

ISS ≤ 1 mA

Choose:

ISS = 1 mA

Step 4: Drain Current

ID1 = ID2 = ISS / 2
     = 0.5 mA

Step 5: Choose Overdrive Voltage

Vov,n = 0.15 V   (design choice for higher gain)

Step 6: Gate-Source Voltage

VGS = Vth + Vov
    = 0.366 + 0.15
    = 0.516 V

Step 7: Source Node Voltage

VS = VG - VGS
   = 0 - 0.516
   = -0.516 V

Step 8: NMOS Sizing (M1, M2)

ID = (1/2) kn (W/L) Vov²

0.5 mA = (1/2)(2.305×10⁻⁴)(W/L)(0.15)²

0.0005 = 1.1525×10⁻⁴ × (W/L) × 0.0225

0.0005 = 2.593×10⁻⁶ × (W/L)

W/L ≈ 193

Step 9: NMOS Width

Wn = 193 × 480 nm
    ≈ 92.6 µm

✔ Use practical:

Wn ≈ 95 µm

Step 10: PMOS Current Mirror Design

ID = 0.5 mA

Vov,p ≈ 0.2 V

ID = (1/2) kp (W/L) Vov²

0.5 mA = (1/2)(9.73×10⁻⁵)(W/L)(0.2)²

0.0005 = 4.865×10⁻⁵ × (W/L) × 0.04

0.0005 = 1.946×10⁻⁶ × (W/L)

W/L ≈ 257

Step 11: PMOS Width

Wp = 257 × 480 nm
    ≈ 123 µm

✔ Use:

Wp ≈ 125 µm

Step 12: Transconductance

gm = 2ID / Vov
   = (2 × 0.5 mA) / 0.15
   ≈ 6.67 mS

Step 13: Gain (Theoretical)

Av = gm × ro

Since:

ro is high (current mirror load)

Av >> Circuit 1 and Circuit 2

Typical:

Av ≈ 30 – 80 V/V

Step 14: Saturation Check

NMOS

VDS ≈ 0.5–0.7 V > Vov (0.15)

✔ Saturation

PMOS

VSD ≈ 0.9 V > Vov

✔ Saturation

Tail Transistor

VDS3 ≈ 0.38 V > Vov

✔ Saturation

Final Results

ISS = 1 mA

ID = 0.5 mA

Wn ≈ 95 µm

Wp ≈ 125 µm

gm ≈ 6.67 mS

Av ≈ 30–80 V/V (expected)

Lower Vov → Higher gm → Higher gain

That’s why we chose:

Vov = 0.15 V (instead of 0.334 V)


Simulation results:

Circuit 1: Differential Amplifier with Resistive Load

1. Operating Point Analysis (.op)

Procedure:

Run .op simulation in LTspice

Observe node voltages and drain currents

Expected Results:

ID1 ≈ ID2 ≈ 0.5 mA

Vout ≈ 0 V

VS ≈ -0.7 V

Screenshot:

<img width="1918" height="1076" alt="4a op" src="https://github.com/user-attachments/assets/0922cc87-4a67-4920-92da-0ad5b11f60e6" />

Extracted Values from Simulation

VDD = 0.9 V
VSS = -0.9 V

VS (node p) ≈ -0.7157 V
Vout1 ≈ 0 V
Vout2 ≈ 0 V

ISS = 1 mA
ID1 = ID2 ≈ 0.5 mA

I(R1) = I(R2) ≈ 0.5 mA

Key Observations

1. Current Distribution

ID1 = ID2 = 0.5 mA

ISS = 1 mA

✔ Confirms:

ID1 + ID2 = ISS

Differential pair is perfectly balanced

2. Output Voltage

Vout1 ≈ Vout2 ≈ 0 V

✔ Matches design condition:

Vout,CM = 0 V

3. Source Node Voltage

VS ≈ -0.7157 V

✔ Close to given:

Vp = -0.7 V

Small deviation due to device model + current source behavior

Saturation Check

NMOS (M1, M2)

VDS = VD - VS
     = 0 - (-0.7157)
     ≈ 0.716 V
Vov = 0.334 V

✔ Condition:

VDS > Vov → 0.716 > 0.334

✔ NMOS in saturation

Tail Transistor (M3)

VDS3 = VS - VSS
     = -0.7157 - (-0.9)
     ≈ 0.184 V
Vov = 0.334 V

❌ Condition:

0.184 < 0.334

❌ Tail transistor not in saturation

Final Interpretation

Differential pair is perfectly symmetric

Output is correctly centered at 0 V

Drain currents match theoretical values

NMOS transistors operate in saturation region

Tail current source operates in linear region

Justification

Due to low supply voltage (±0.9 V), the voltage across the tail transistor is insufficient to satisfy the saturation condition (VDS < Vov). Hence, it operates in the linear region. However, it still maintains approximately constant current, allowing proper differential operation.


Transient Analysis

Case 1: Small Signal Input (No Clipping)

<img width="1918" height="1070" alt="4a trans" src="https://github.com/user-attachments/assets/ce2b548d-2bb8-4998-aa67-3c6efa4b46ef" />

Input Conditions

Vin1 = SINE(0 2m 1k)

Vin2 = SINE(0 -2m 1k)

Observations from Waveform

Output signals Vout1 and Vout2 are:

Sinusoidal

Equal amplitude

180° out of phase

No distortion observed

Circuit operates in linear region

Gain Calculation (From Graph)

Input Differential Voltage

Vin(diff) = Vin1 - Vin2 = 2m - (-2m) = 4 mV (peak)

Output Differential Voltage

From graph:

Vout ≈ 12 mV (peak)

Gain (V/V)

Av = Vout / Vin
   = 12 mV / 4 mV
   = 3 V/V

Gain (dB)

Av(dB) = 20 log10(3)
       ≈ 9.54 dB

Comparison with Theoretical Gain

Theoretical Av ≈ 5.4 V/V

Reason for Difference

Lower gain observed due to:
- Tail transistor not in saturation
- Small signal approximation limitations
- Real device model effects (channel length modulation, etc.)

Result

Gain ≈ 3 V/V

Gain ≈ 9.54 dB

Linear amplification confirmed

Case 2: Large Signal Input (Clipping Region)

<img width="1919" height="1071" alt="4a trans1" src="https://github.com/user-attachments/assets/200ef695-cddf-4611-9344-192e73677094" />

Input Conditions

Vin1 = SINE(0 0.9 1k)

Vin2 = SINE(0 -0.9 1k)

Observations from Waveform

Output is not sinusoidal

Clear clipping at ±0.9 V

Flat tops indicate saturation of output

Explanation

When input amplitude exceeds linear range:
- One transistor turns OFF
- Other transistor carries full current
- Output reaches supply limits

Key Condition

Linear operation: Vid < √2 × Vov

Vov = 0.334 V

√2 × Vov ≈ 0.472 V

Since:

Vin(diff) ≈ 1.8 V >> 0.472 V

❌ Circuit operates in nonlinear region

Result

Output is clipped at supply rails

Differential amplifier behaves like a switch

Nonlinear behavior confirmed

Final Interpretation

Small Signal Case
-Linear operation
-Gain measurable
-Matches differential amplifier theory

Large Signal Case
-Nonlinear operation
-Clipping occurs
-Limited by supply voltage

Key Conclusion

The circuit operates as a linear amplifier only for small differential inputs. When the input exceeds the linear range, the output saturates at the supply limits, resulting in clipping and nonlinear behavior.

gain (3 V/V) is lower than expected (5.4 V/V)

The reduction in gain compared to theoretical value is due to non-ideal current source behavior and limited voltage headroom.


AC Analysis:

Observation from AC Plot

From your graph (flat region at mid-frequency):

Gain ≈ 15.88 dB

Convert Gain to V/V

Av = 10^(Gain(dB) / 20)
   = 10^(15.88 / 20)
   ≈ 6.23 V/V

Final AC Gain

Av ≈ 6.23 V/V

Av ≈ 15.88 dB

Comparison with Theoretical Gain

Theoretical Value

Av = gm × RD
   = 2.99 mS × 1.8 kΩ
   ≈ 5.4 V/V

Av(dB) = 20 log10(5.4)
       ≈ 14.65 dB

| Type          | Gain (V/V) | Gain (dB) |
| ------------- | ---------- | --------- |
| Theoretical   | 5.4        | 14.65 dB  |
| AC Simulation | 6.23       | 15.88 dB  |

Interpretation

Simulation gain is slightly higher than theoretical value due to:
- Channel length modulation (finite ro)
- Device model non-idealities
- More accurate small-signal modeling in AC analysis

AC analysis provides more accurate gain compared to transient analysis because it directly uses small-signal parameters without nonlinear effects.

Frequency Response Observation

Gain is constant at mid-frequency → flat region

Gain drops at low frequency → due to biasing effects

Gain rolls off at high frequency → due to parasitic capacitances

Conclusion for circuit 1: The AC analysis shows a gain of approximately 6.23 V/V (15.88 dB), which closely matches the theoretical value of 5.4 V/V. The slight deviation is due to non-ideal device effects. The circuit exhibits proper amplification with stable midband gain.


Circuit-2: Active Load Differential Amplifier

Operating point:

<img width="1919" height="1076" alt="4b op" src="https://github.com/user-attachments/assets/3d496584-70de-41f8-99e8-16c4afab2861" />

Extracted Values from Simulation

VDD = 0.9 V

VSS = -0.9 V

VS (node p) ≈ -0.545 V

Vout1 ≈ 0 V

Vout2 ≈ 0 V

ID1 ≈ ID2 ≈ 0.5 mA

ID4 ≈ ID5 ≈ 0.5 mA

ISS ≈ 1 mA

Key Observations

1. Current Distribution

ID1 = ID2 ≈ 0.5 mA

ISS ≈ 1 mA

✔ Confirms:

ID1 + ID2 = ISS

Differential pair is perfectly balanced

2. Current Mirror Operation (PMOS)

ID4 ≈ ID5 ≈ 0.5 mA

✔ Confirms:

PMOS transistors form a current mirror

Active load is functioning correctly

3. Output Voltage

Vout1 ≈ Vout2 ≈ 0 V

✔ Output is centered → proper biasing

4. Source Node Voltage

VS ≈ -0.545 V

Different from Circuit 1 (-0.7 V) because:

Biasing is now controlled by Vb

Tail transistor is actively biased

Saturation Check

NMOS (M1, M2)

VDS = VD - VS
     = 0 - (-0.545)
     ≈ 0.545 V

Vov ≈ 0.334 V

✔ Condition:

VDS > Vov → 0.545 > 0.334

✔ NMOS in saturation

PMOS (M4, M5)

VSD = VS - VD
     = 0.9 - 0
     = 0.9 V

✔ Condition:

VSD > Vov,p

✔ PMOS in saturation

Tail Transistor (M3)

VDS3 = VS - VSS
     = -0.545 - (-0.9)
     ≈ 0.355 V

✔ Compare:

Vov ≈ 0.334 V

✔ Condition:

0.355 > 0.334

✔ Tail transistor is in saturation

*All MOSFETs in Circuit 2 operate in saturation region.

Interpretation

Proper biasing using Vb = -0.35 V improves operation

Active load ensures:

Higher output resistance

Better gain

Unlike Circuit 1:

Tail transistor is now fully in saturation

Current source behaves more ideally

In Circuit 2, the use of a bias voltage (Vb) ensures sufficient VDS across the tail transistor, allowing it to remain in saturation. This improves current source behavior and enhances amplifier performance compared to Circuit 1.

The operating point confirms that all transistors are properly biased in saturation. The differential pair is balanced, and the active load operates correctly as a current mirror. This results in improved performance compared to the resistive load circuit.


Transient Analysis

Case 1: Small Signal Input (Linear Region)

<img width="1919" height="1078" alt="4b trans" src="https://github.com/user-attachments/assets/77ad8c30-1f40-451f-9284-e6a2c6f1851a" />

Input Conditions

Vin1 = SINE(0 2m 1k)

Vin2 = SINE(0 -2m 1k)

Observations from Waveform

Output signals are:

Sinusoidal

Amplified

180° out of phase

No distortion

Proper differential amplification

Gain Calculation (From Graph)

Input Differential Voltage

Vin(diff) = 2m - (-2m) = 4 mV (peak)

Output Differential Voltage

From graph:

Gain (V/V)

Av = 3.75 V/V

Gain (dB)

Av(dB) = 20 log10(3.75)
       ≈ 11.48 dB

Result

Gain ≈ 3.75 V/V

Gain ≈ 11.48 dB

Justification

Although active load ideally increases gain, the observed gain is lower due to:
- Limited voltage headroom
- Output node not having large ro in practical model
- Possible mismatch in PMOS current mirror
- Small signal extraction from transient is less accurate

Case 2: Large Signal Input (Clipping Region)

<img width="1919" height="1078" alt="4b trans1" src="https://github.com/user-attachments/assets/ef4bc301-68e8-41fd-a32f-dac59252a149" />

Input Conditions

Vin1 = SINE(0 0.9 1k)

Vin2 = SINE(0 -0.9 1k)

Observations

Output is highly distorted

Sharp transitions → switching behavior

Output swings close to supply limits (~1.2 V)

Explanation

Large differential input causes:
- One transistor fully ON
- Other transistor OFF
- Current mirror forces abrupt switching

Result

Strong nonlinear behavior

Circuit behaves like a comparator/switch

| Feature           | Circuit 1       | Circuit 2             |
| ----------------- | --------------- | --------------------- |
| Small Signal Gain | ~3 V/V          | ~1.75 V/V             |
| Linearity         | Better          | Slightly reduced      |
| Large Signal      | Smooth clipping | Sharp switching       |
| Behavior          | Amplifier       | Amplifier + switching |

The active load circuit shows sharper transitions and higher nonlinearity compared to the resistive load circuit due to current mirror action.

Transient analysis may not reflect true gain of active load amplifier. AC analysis must be used for accurate gain measurement.

The circuit operates linearly for small signals but exhibits strong nonlinear behavior for large inputs. The gain obtained from transient analysis is lower than expected due to non-ideal effects and measurement limitations.


AC Analysis

<img width="1919" height="1079" alt="4b ac" src="https://github.com/user-attachments/assets/2e15f5e8-d60f-4127-a5d1-a43106591be1" />

Observation from AC Plot

From your graph (flat midband region):

Gain ≈ 12.3 dB

(Blue trace is flat ≈ constant gain)

Convert Gain to V/V

Av = 10^(Gain/20)
   = 10^(12.3 / 20)
   ≈ 4.12 V/V

Final AC Gain

Av ≈ 4.1 V/V

Av ≈ 12.3 dB

Justification

Although active load ideally increases gain, the observed gain is lower due to:

1. Limited output resistance (ro) in practical CMOS model

2. Low supply voltage (±0.9 V) reducing voltage headroom

3. PMOS current mirror not providing ideal high resistance

4. Channel length modulation reducing effective gain

5. Device sizing not optimized for maximum gain

Frequency Response Observation

Gain is flat in midband → proper amplifier operation

Peak around ~100 Hz (due to bias/network effects)

Gain decreases at high frequency → parasitic capacitances

Active load increases gain only if output resistance is high.

In this design, ro is limited, so gain improvement is not observed.

The AC analysis shows a gain of approximately 4.1 V/V (12.3 dB). Although active load is expected to increase gain, practical limitations such as low output resistance and limited voltage headroom result in lower gain compared to Circuit 1.

FINAL RESULT 

Gain (AC) = 4.1 V/V

Gain (AC) = 12.3 dB

Comparison with AC Analysis

| Method      | Gain (V/V) | Gain (dB) |
| ----------- | ---------- | --------- |
| Transient   | 3.75       | 11.48 dB  |
| AC Analysis | 4.1        | 12.3 dB   |


Circuit-3: Current Mirror Differential Amplifier

Operating point:

<img width="1913" height="1019" alt="4c op" src="https://github.com/user-attachments/assets/dfcf8639-6325-40a2-bc7d-db9e6be34328" />

Extracted Values from Simulation

VDD = 0.9 V

VSS = -0.9 V

VS (node p) ≈ -0.606 V

Vout1 ≈ 0 V

Vout2 ≈ 0 V

ISS ≈ 1 mA

ID1 ≈ ID2 ≈ 0.5 mA

ID3 ≈ ID4 ≈ 0.5 mA

Key Observations

1. Current Distribution

ID1 = ID2 ≈ 0.5 mA

ISS ≈ 1 mA

✔ Confirms:

ID1 + ID2 = ISS

Differential pair is perfectly balanced

2. Current Mirror Operation

ID3 ≈ ID4 ≈ 0.5 mA

✔ Confirms:

PMOS transistors form a current mirror load

Proper mirroring ensures high output resistance

3. Output Voltage

Vout1 ≈ Vout2 ≈ 0 V

✔ Output centered → correct biasing

4. Source Node Voltage

VS ≈ -0.606 V

Slight variation from design due to:

Bias voltage (Vb1 = -0.35 V)

Device model non-idealities

Saturation Check

NMOS (M1, M2)

VDS = VD - VS
     = 0 - (-0.606)
     ≈ 0.606 V

Vov ≈ 0.15 V

✔ Condition:

VDS > Vov → 0.606 > 0.15

✔ NMOS in saturation

PMOS (M3, M4)

VSD = VS - VD
     = 0.9 - 0
     = 0.9 V

✔ Condition:

VSD > Vov,p

✔ PMOS in saturation

Tail Transistor (M5)

VDS5 = VS - VSS
     = -0.606 - (-0.9)
     ≈ 0.294 V

Vov ≈ 0.15 V

✔ Condition:

0.294 > 0.15

✔ Tail transistor in saturation

All MOSFETs in Circuit 3 operate in saturation region.

Interpretation

Proper biasing ensures all devices in saturation

Current mirror load provides:

High output resistance

Improved gain

Compared to Circuit 2:

Better bias stability

More controlled current flow

The use of proper bias voltages (Vb1 and Vb2) ensures sufficient VDS across all transistors, allowing them to operate in saturation. This improves the current mirror accuracy and enhances amplifier performance.

The operating point confirms correct biasing of the circuit. The differential pair is balanced, and the current mirror operates properly. All transistors are in saturation, ensuring high gain and proper amplifier operation.


Transient analysis:

Case 1: Small Signal Input (Linear Region)

<img width="1919" height="1018" alt="4c trans" src="https://github.com/user-attachments/assets/fa75bef7-b37d-4054-929f-f99b583c8a4f" />

Input Conditions

Vin1 = SINE(0 2m 1k)

Vin2 = SINE(0 -2m 1k)

Observations from Waveform

Output signals:

Sinusoidal

Large amplitude

180° out of phase

Very high amplification compared to Circuit 1 & 2

Proper differential operation

Gain Calculation (From Graph)

Input Differential Voltage

Vin(diff) = 2m - (-2m) = 4 mV

Output Differential Voltage

From graph:

Gain (V/V)

Av = 52.6875 V/V

Gain (dB)

Av(dB) = 20 log10(52.6875)
       ≈ 34.43 dB

Result

Gain ≈ 52.6875 V/V

Gain ≈ 34.43 dB

Theoretical gain:

Av=-gm,n*(ro,n||ro,p)

ro,n = 1/lamda*Id = 20k ohm  (lamda=0.1)

ro,p = 1/lamda*Id = 16.666k ohm (lamda=0.12)

gm = 2*Id/Vov

Vov = 0.15V

Gm,n = 6.667e-3

Av = -60.6096V/V

AvdB = 35.6508dB

✔ Highest gain among all circuits

Case 2: Large Signal Input (Clipping Region)

<img width="1919" height="1030" alt="4c trans1" src="https://github.com/user-attachments/assets/35640f5b-c054-499e-a556-83c9b33cee53" />

Input Conditions

Vin = 0.9 V

Observations

Output is strongly clipped

Flat tops near supply rails (±0.9 V)

Very sharp transitions

Explanation

High gain causes output to saturate quickly.

Even small increase in input pushes output to supply limits.

Result

Strong nonlinear behavior

Circuit behaves like a high-gain comparator

| Circuit   | Type of Load              | Theoretical Gain (V/V) | Theoretical Gain (dB) | Simulation Gain (V/V) | Simulation Gain (dB) |
| --------- | ------------------------- | ---------------------- | --------------------- | --------------------- | -------------------- |
| Circuit 1 | Resistive Load            | 5.4                    | 14.65 dB              | 6.23                  | 15.88 dB             |
| Circuit 2 | Active Load (PMOS Mirror) | High (≈10–20 expected) | ≈20–26 dB             | 4.1                   | 12.3 dB              |
| Circuit 3 | Current Mirror Load       | 60.6096                | 35.65 dB              | 52.69                 | 34.43 dB             |


1. Circuit 3 provides the highest gain due to high output resistance (ro).

2. Circuit 1 shows moderate gain with stable linear behavior.

3. Circuit 2 theoretically should have higher gain than Circuit 1, but due to practical limitations (low ro, headroom), its gain is lower.

Gain increases with increase in output resistance (ro).

Circuit 3 uses current mirror load → highest ro → highest gain.   


AC Analysis: Current Mirror Differential Amplifier


Observation from AC Plot

From your graph (flat midband region):

Gain ≈ 35.23 dB

Convert Gain to V/V

Av = 10^(Gain/20)
   = 10^(35.23 / 20)
   ≈ 57.7 V/V

Final AC Gain

Av ≈ 57.7 V/V

Av ≈ 35.23 dB

AC gain is slightly higher than theoretical due to:
- Channel length modulation (increases effective ro)
- More accurate small-signal modeling
- Ideal biasing in AC analysis

Frequency Response

Flat region → midband gain (~35 dB)

Slight rise at low frequency → bias effect

Roll-off at high frequency → parasitic capacitances 

FINAL RESULT

Gain (AC) = 57.7 V/V

Gain (AC) = 35.23 dB

The current mirror differential amplifier (Circuit 3) achieves the highest gain due to significantly increased output resistance (ro), validating the theoretical relation Av = gm × ro. The AC gain closely matches theoretical and transient results, confirming correct design and operation.


Comparision

| Parameter              | Circuit 1 (Resistive Load)    | Circuit 2 (Active Load)  | Circuit 3 (Current Mirror Load) |
| ---------------------- | ----------------------------- | ------------------------ | ------------------------------- |
| Load Type              | Resistor (RD)                 | PMOS Active Load         | Current Mirror Load             |
| Tail Current Source    | Not ideal (not in saturation) | Improved (in saturation) | Fully ideal (in saturation)     |
| Gain (V/V)             | 6.23                          | 4.1                      | 57.7                            |
| Gain (dB)              | 15.88 dB                      | 12.3 dB                  | 35.23 dB                        |
| Output Resistance (ro) | Low                           | Moderate                 | Very High                       |
| Linearity              | High                          | Moderate                 | Low (for large signals)         |
| Clipping Behavior      | Smooth                        | Faster clipping          | Very sharp clipping             |
| Saturation Condition   | Partial                       | Full                     | Full                            |
| Circuit Complexity     | Simple                        | Moderate                 | Complex                         |
| Power Efficiency       | Low                           | Better                   | Best                            |
| Performance            | Basic                         | Improved                 | Best                            |

Key observations:

1. Circuit 1 is simple and provides stable linear amplification but limited gain.

2. Circuit 2 improves biasing and uses active load, but gain is limited due to practical constraints.

3. Circuit 3 provides the highest gain due to current mirror load and proper saturation of all transistors.


Advantages and Disadvantages

Circuit 1 (Resistive Load)

Advantages:

Simple design

Good linearity

Easy to analyze

Disadvantages:

Low gain

Poor efficiency

Large area (resistors)

Circuit 2 (Active Load)

Advantages:

Better gain than basic design (theoretically)

Improved efficiency

Smaller area

Disadvantages:

Gain limited by practical ro

More complex

Sensitive to biasing

Circuit 3 (Current Mirror Load)

Advantages:

Highest gain

High output resistance

Best performance

Disadvantages:

Reduced linear range

Early clipping

Highest complexity


Conclusion:

In this experiment, three types of CMOS differential amplifiers were designed and analyzed using LTspice: a resistive load differential amplifier (Circuit 1), an active load differential amplifier (Circuit 2), and a current mirror load differential amplifier (Circuit 3). The design was carried out under given constraints of power (≤1.8 mW), supply voltage (±0.9 V), and technology parameters (L = 480 nm).

The operating point analysis confirmed that proper biasing was achieved in all circuits. However, Circuit 1 showed limitations in maintaining ideal saturation conditions due to the use of resistive loads and a less effective tail current source. Circuit 2 improved the biasing conditions by introducing an active load, while Circuit 3 ensured that all transistors operated in saturation through the use of current mirror configurations.

From transient and AC analysis, it was observed that the gain of the amplifier significantly depends on the output resistance (ro) of the circuit. Circuit 1 exhibited moderate gain (~6.23 V/V or 15.88 dB) with good linearity. Circuit 2 showed lower practical gain (~4.1 V/V or 12.3 dB) due to non-idealities and limited output resistance. Circuit 3 achieved the highest gain (~57.7 V/V or 35.23 dB) due to the current mirror load, which increases output resistance and improves amplification.

It was also observed that as gain increases, the linear operating range decreases. Circuit 3, while providing the highest gain, showed early clipping for larger input signals, behaving similarly to a high-gain comparator. In contrast, Circuit 1 maintained better linearity over a wider input range.

Thus, the experiment verifies the theoretical relation Av = gm × ro and demonstrates that increasing output resistance using active and current mirror loads significantly enhances the gain of differential amplifiers. Among the three circuits, the current mirror differential amplifier provides the best performance in terms of gain, while the resistive load amplifier offers better linearity, and the active load amplifier provides a balance between the two.

*The current mirror differential amplifier achieves the highest gain due to increased output resistance, confirming that gain is directly proportional to ro.


Inference:

1. The gain of a differential amplifier is directly proportional to the output resistance (ro), as given by Av = gm × ro.

2. Use of current mirror load significantly increases output resistance, thereby improving the gain.

3. Proper biasing ensures all MOSFETs operate in saturation, which is essential for linear amplification.

4. As gain increases, the linear operating range decreases, leading to earlier clipping in high-gain circuits.

5. Among the three circuits, the current mirror differential amplifier provides the highest gain, while the resistive load amplifier offers better linearity.
