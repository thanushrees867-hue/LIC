Aim:

To design and analyze a Common Source (CS) amplifier using 180 nm CMOS technology under different configurations and to evaluate its performance in terms of operating point, voltage gain, frequency response, bandwidth, and transistor sizing through theoretical calculations and simulation.


Theory:

A Common Source (CS) amplifier is a fundamental CMOS amplifier configuration widely used for voltage amplification. It provides high voltage gain with a 180° phase shift between the input and output signals.

In this configuration, the NMOS transistor acts as the amplifying device, while the load is implemented using either a PMOS active load or a current source. When an input signal is applied at the gate of the NMOS transistor, it controls the drain current, which in turn develops an output voltage across the load.

The operation of the CS amplifier depends on biasing the MOSFETs in the saturation region to ensure proper amplification.


### Key Equations:

Overdrive Voltage:
Vov = VGS − VTH

Drain Current (Saturation Region):
ID = (1/2) μCox (W/L) (Vov)^2

Transconductance:
gm = 2ID / Vov

Output Resistance:
ro = 1 / (λID)

Voltage Gain:
Av = −gm × Rout

where,
Rout = (ro_n || ro_p)


### Working Principle:

- A small change in input voltage (VGS) causes a change in drain current (ID).
  
- This variation in current flows through the load, producing a larger variation in output voltage.
  
- The negative sign in gain indicates a phase inversion of 180°.


### Configuration Variations:

Experiment 2A:

Includes source resistance (Rs), which introduces negative feedback. This improves stability and linearity but reduces gain.

Experiment 2B:

Uses a current source for biasing, providing better control of the operating point and ensuring consistent saturation of transistors.

Experiment 2C:

Optimized for higher gain by reducing overdrive voltage, which increases transconductance (gm). This improves gain but may reduce bandwidth.


### Frequency Response:

At low frequencies, the gain remains constant (midband region). At higher frequencies, parasitic capacitances reduce the gain, defining the upper cutoff frequency (fH). The bandwidth of the amplifier is given by:

BW = fH − fL


### Non-Ideal Effects:

In practical CMOS circuits, performance deviates from theoretical values due to:

- Channel length modulation
  
- Parasitic capacitances
  
- Mobility degradation
  
- Short-channel effects

These factors reduce gain and bandwidth compared to ideal calculations.


Procedure:

A Common Source (CS) amplifier is a fundamental CMOS amplifier configuration widely used for voltage amplification. It provides high voltage gain with a 180° phase shift between the input and output signals.

In this configuration, the NMOS transistor acts as the amplifying device, while the load is implemented using either a PMOS active load or a current source. When an input signal is applied at the gate of the NMOS transistor, it controls the drain current, which in turn develops an output voltage across the load.

The operation of the CS amplifier depends on biasing the MOSFETs in the saturation region to ensure proper amplification.


### Key Equations:

Overdrive Voltage:
Vov = VGS − VTH

Drain Current (Saturation Region):
ID = (1/2) μCox (W/L) (Vov)^2

Transconductance:
gm = 2ID / Vov

Output Resistance:
ro = 1 / (λID)

Voltage Gain:
Av = −gm × Rout

where,
Rout = (ro_n || ro_p)


### Working Principle:

- A small change in input voltage (VGS) causes a change in drain current (ID).
  
- This variation in current flows through the load, producing a larger variation in output voltage.
  
- The negative sign in gain indicates a phase inversion of 180°.


### Configuration Variations:

Experiment 2A:
Includes source resistance (Rs), which introduces negative feedback. This improves stability and linearity but reduces gain.

Experiment 2B:
Uses a current source for biasing, providing better control of the operating point and ensuring consistent saturation of transistors.

Experiment 2C:
Optimized for higher gain by reducing overdrive voltage, which increases transconductance (gm). This improves gain but may reduce bandwidth.


### Frequency Response:

At low frequencies, the gain remains constant (midband region). At higher frequencies, parasitic capacitances reduce the gain, defining the upper cutoff frequency (fH). The bandwidth of the amplifier is given by:

BW = fH − fL


### Non-Ideal Effects:

In practical CMOS circuits, performance deviates from theoretical values due to:

- Channel length modulation
  
- Parasitic capacitances
  
- Mobility degradation
  
- Short-channel effects

These factors reduce gain and bandwidth compared to ideal calculations.


Comparision- 2a,2b,2c


Basic Configurations:

| Parameter            | Experiment 2A                          | Experiment 2B                          | Experiment 2C                          |
|---------------------|----------------------------------------|----------------------------------------|----------------------------------------|
| Circuit Type        | CS with PMOS active load + Rs          | CS with current source load            | CS with active load                    |
| Load Type           | PMOS load                              | NMOS current source + PMOS load        | PMOS active load                       |
| Source Resistance   | Present (Rs = 1kΩ)                     | Not present                            | Not present                            |
| Biasing Complexity  | Medium                                 | High                                   | Moderate                               |


Gain Comparision:

| Parameter                 | 2A            | 2B            | 2C            |
|--------------------------|--------------|--------------|--------------|
| Theoretical Gain (dB)    | 23.74 dB     | -6.93 dB     | 35.6 dB      |
| Simulated Gain (dB)      | 16 dB        | 6.4 dB       | 21 dB        |
| Voltage Gain (V/V)       | 6.3          | 2.09         | ~11.2        |


Bandwidth Comparision:

| Parameter     | 2A         | 2B         | 2C         |
|--------------|-----------|-----------|-----------|
| Bandwidth    | 376 MHz   | 138 MHz   | 25 MHz    |
| High Cutoff  | Very High | Moderate  | Low       |


Power Consumption:

| Parameter | 2A       | 2B       | 2C       |
|----------|---------|---------|---------|
| Power    | 0.24 mW | 0.24 mW | 0.24 mW |


Design Parameters:

| Parameter             | 2A        | 2B        | 2C        |
|----------------------|----------|----------|----------|
| Overdrive Voltage    | 0.25 V   | 0.2 V    | 0.15 V   |
| gm                   | 1.6 mS   | 2 mS     | 2.67 mS  |
| ro                   | ~25 kΩ   | ~22.7 kΩ | ~22.7 kΩ |


Key Observations:

- Experiment 2C provides the highest gain due to higher gm and no source degeneration.
  
- Experiment 2A provides the highest bandwidth but reduced gain due to Rs.
  
- Experiment 2B offers stable biasing but lower gain due to current source limitations.


Conclusion:

The Common Source (CS) amplifiers using 180 nm CMOS technology were successfully designed and analyzed under three different configurations: with source degeneration (Experiment 2A), with current source load (Experiment 2B), and with optimized active load (Experiment 2C).

All designs satisfied the given power constraint of 0.4 mW, operating at approximately 0.24 mW. The simulation results verified proper biasing conditions, with all MOSFETs operating in the saturation region.

Among the three designs, Experiment 2C achieved the highest voltage gain due to lower overdrive voltage and higher transconductance. Experiment 2A provided the highest bandwidth due to reduced effective gain and the presence of source degeneration. Experiment 2B offered stable biasing through current source implementation but resulted in comparatively lower gain.

The differences between theoretical and simulated results were observed due to non-ideal effects such as channel length modulation, parasitic capacitances, mobility degradation, and short-channel effects inherent in CMOS technology.


Inference:

Experiment 2A demonstrates that introducing source resistance improves stability and linearity but reduces voltage gain due to negative feedback.

Experiment 2B shows that current source biasing enhances control over operating point and ensures reliable saturation operation, but limits gain due to finite output resistance.

Experiment 2C highlights that reducing overdrive voltage increases transconductance, thereby improving voltage gain, but at the cost of reduced bandwidth and increased sensitivity to device non-idealities.

Thus, a trade-off exists between gain, bandwidth, and stability:

- Higher gain → lower bandwidth (Experiment 2C)
  
- Higher bandwidth → lower gain (Experiment 2A)
  
- Better stability → moderate performance (Experiment 2B)

This analysis emphasizes the importance of selecting appropriate amplifier configuration based on application requirements.
