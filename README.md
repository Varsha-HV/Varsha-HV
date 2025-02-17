 # LINEAR INTEGRATED CIRCUITS - EXPT- 01
## DC,AC and Transcient analysis of CS amplifier

### Introduction 
The Common Source Amplifier is a widely used MOSFET-based amplifier configuration in analog electronics. It plays a crucial role in applications such as audio amplification, signal processing, and communication systems by providing significant voltage gain.  
This experiment focuses on analyzing the CS amplifier through DC, AC, and Transient analysis. DC analysis determines the biasing conditions to ensure stable operation in the active region. AC analysis evaluates key parameters such as voltage gain, input impedance, and frequency response to assess amplification performance. Transient analysis examines the amplifier’s time-domain response, analyzing its behavior with varying input signals.  
*Objective:* : 
To analyze the DC biasing, AC gain, and transient response of a Common Source (CS) Amplifier using a MOSFET and understand its role in signal amplification. This includes evaluating voltage gain, impedance, frequency response, and time-domain behavior for practical applications.
### Key components used and their roles
MOSFET – Acts as the main amplifying element, controlling current flow.

Resistors – Set the biasing conditions and stabilize the operating point.

Power Supply – Provides the necessary DC voltage for MOSFET operation.
### Circuit diagram 
![Screenshot 2025-02-16 193317](https://github.com/user-attachments/assets/bfa75dd5-a0d9-4e70-b342-1eb4afa4a3fc)

V1: AC input signal (SINE wave with 0.9V DC offset and 50mV amplitude at 1kHz).

V2: DC supply voltage (1.8V).

R1: Load resistor (1kΩ) to convert the amplified current signal into a voltage signal.

M1: NMOS transistor operating as an amplifier.

### Components details :
The circuit performs DC, AC, and Transient analysis, as specified by the simulation commands (.op, .ac, .tran). It amplifies the small input signal and produces an inverted output at V_out.
The circuit uses the TSMC 180nm technology library (tsmc018.lib), which provides accurate MOSFET model parameters for simulation. This library contains real-world transistor characteristics, such as threshold voltage, mobility, and capacitances, ensuring a precise representation of MOSFET behavior in analog circuits. By including this library, the simulation accurately reflects the amplification, frequency response, and transient behavior of the Common Source (CS) Amplifier.
 
 NMOS transistor (M1) is defined as CMOSN, referring to a specific  NMOS model from the TSMC 180nm library

 MOSFET Length(l) : 250nm

 MOSFET width(w) : 0.05um

 Threshold voltage(v_th) : 0.3662473
 

 Resistor (R1 - 1kΩ): Converts amplified current variations into an output voltage signal.
 
 Voltage Source (V1 - AC Signal Source): Provides the input signal (SINE wave with 0.9V DC offset, 50mV amplitude, 1kHz frequency).

 Voltage Source (V2 - 1.8V DC Supply): Supplies the necessary biasing voltage for MOSFET operation

 Ground (GND): Serves as the common reference for all voltages.
 
 The input AC signal 

DC Offset: 0.9V (to keep the MOSFET in active mode)

Amplitude: 50mV (small input signal to be amplified)

Frequency: 1kHz 

### DC analysis


![WhatsApp Image 2025-02-15 at 12 48 09_c2827f40](https://github.com/user-attachments/assets/3ae6f788-9978-4fd6-9b3f-009ee7884ef3)

From the stimulation : if l = 180nm , w = 1um ,V_out = 1.64727V  and I_d = 0.0001527A

if the power rating(power dissipiation across the resistor) is 50uW. given supply voltage is 1.8V .then the current through the resistor is given by :

I_d = power/Voltage = 50u/1.8 = 27.7uA

Since the calculated value dosent match the simulated value to get required current value we adjust w and l values

| Width   | Length  | Current |
|-------  |-------- |---------|
|  0.07u  |   250nm |  25.53uA|
|  0.25u  |   250nm |  37.26uA|
|  0.30u  |  250nm  |  41.94uA|
|  0.05u  |  250nm  |  27.7uA |


NMOS should be operated in saturation region , this can be confirmed by the DC operating point analysis

V_DS ≥ V_GS-V_T

V_GS = V_G - V_S = 0.9V−0V = 0.9V

V_DS = V_D - V_S = 1.8V−0V = 1.8V

For saturation:
V_DS ≥ V_GS-V_T

1.8 ≥ 0.9V - 0.36624V

1.8V ≥ 0.5337V

Since 1.8V is greater than 0.53375V, the MOSFET is in saturation. 

### Transient analysis

![Screenshot 2025-02-15 125526](https://github.com/user-attachments/assets/b537b924-ce1c-4c41-905e-7fb0eccc3290)

Transient analysis examines the time-domain response of the CS amplifier to an AC input signal (1kHz sine wave). It helps analyze amplification, signal distortion, and dynamic performance by simulating real-time behavior (`.tran 5m`).

### AC analysis

![WhatsApp Image 2025-02-15 at 13 03 11_c2339011](https://github.com/user-attachments/assets/0443722c-5f7c-4a5f-97f1-7b706b8d0a96)

The AC input signal has:

Frequency: 1KHz 

Amplitude: 50mV

DC Offset: 0.9V

This analysis determines the gain, bandwidth, and frequency response, helping evaluate the amplifier’s performance over different frequencies.

### Inference

DC Analysis: The MOSFET operates in saturation, with w/l controlling 
 I_d and transconductance. Proper biasing ensures stable operation.

Transient Analysis: The amplifier inverts and amplifies the signal. Higher 
w/l increases gain but raises power consumption and potential distortion.

AC Analysis: Gain depends on gm amd w/l A larger w/l  improves gain but reduces bandwidth, while a smaller w/l enhances stability.

# EXPERIMENT NO - 02

## CS Amplifier with PMOS Load

### Introduction 

In a Common Source (CS) Amplifier, a PMOS transistor can replace the traditional resistive load. Using a PMOS transistor improves the amplifier’s performance by increasing the output resistance, which results in higher voltage gain and better linearity. This configuration also enhances power efficiency and allows for better tuning and flexibility in design. PMOS load CS amplifiers are particularly useful in high-gain analog circuits where improved performance and efficiency are needed, such as in operational amplifiers.

*Objective:*
To analyze the performance of a Common Source Amplifier with a PMOS load, focusing on improvements in gain, linearity, and efficiency.

### Key components used and their roles

PMOS Transistor: Acts as the active load, replacing the resistor to improve voltage gain and linearity.

NMOS Transistor: Serves as the amplifying device in the common-source configuration.

Biasing Resistors: Set the appropriate operating point for the transistors to ensure proper function and amplification.

Power Supply: Provides the required voltage for circuit operation.
 
 ### Circuit diagram 

 <img width="960" alt="image" src="https://github.com/user-attachments/assets/5eb55346-a3ef-4279-9a88-6fb518b107d9" />


V1: AC input signal (SINE wave with 0.9V DC offset and 50mV amplitude at 1kHz).

V2: DC supply voltage (1.8V).

R1: Load resistor (1kΩ) to convert the amplified current signal into a voltage signal.

M1: NMOS transistor operating as an amplifier

The source of the PMOS (M2) is connected to V2 (1.8V).

The gate is biased at 1.3V using V3.

The drain is connected to R1 (1kΩ) load, which is then connected to ground.

## Components details :

MOSFET:

Type: NMOS/PMOS

Length (𝐿) = 500nm

Width (w) = 490nm

Threshold Voltage (v_th) = 0.3662473V

Power Supply:

v_dd = 1.8V

Type: Sine wave

Offset Voltage = 0.9V

Amplitude = 50mV

Frequency = 1kHz


