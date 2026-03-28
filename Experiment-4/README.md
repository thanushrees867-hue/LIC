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


Circuit-2: Differential Amplifier with Active Load

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

