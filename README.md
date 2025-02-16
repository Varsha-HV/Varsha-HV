 # LINEAR INTEGRATED CIRCUITS - EXPT- 01
## DC,AC and Transcient analysis of CS amplifier

### Introduction 
The Common Source Amplifier is a widely used MOSFET-based amplifier configuration in analog electronics. It plays a crucial role in applications such as audio amplification, signal processing, and communication systems by providing significant voltage gain.  
This experiment focuses on analyzing the CS amplifier through DC, AC, and Transient analysis. DC analysis determines the biasing conditions to ensure stable operation in the active region. AC analysis evaluates key parameters such as voltage gain, input impedance, and frequency response to assess amplification performance. Transient analysis examines the amplifier’s time-domain response, analyzing its behavior with varying input signals.  
#### Objective : 
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



 
 


