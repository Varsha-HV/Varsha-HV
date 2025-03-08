# Experiment 03: DIFFERENTIAL AMPLIFIER
## Introduction
The differential amplifier, a fundamental analog circuit, excels at amplifying the difference between two input signals while effectively suppressing common-mode noise, making it indispensable for precision signal processing applications. This experiment aims to explore its critical performance metrics differential-mode gain, common-mode gain, and common-mode rejection ratio (CMRR) through practical measurements and indepth analysis of a constructed circuit. By doing so, it will provide valuable hands-on insights into the amplifier’s operational principles and realworld significance.
The differential amplifier operates in two distinct modes:  

1. **Common Mode:** This mode considers the average of the two input signals, expressed as **(V₁ + V₂) / 2**, representing the shared component between them.  

2. **Differential Mode:** This mode focuses on the voltage difference between the two inputs, given by **V₁ - V₂**, which is the desired amplified signal in most applications.

## Objective:

To design a differential amplifier for the following specifications.

VDD=2.5V, P<=3mW, Vicm=1.3V, Vocm=1.4V, Vp=0.3V

## Procedure :

### **Steps to Simulate a Differential Amplifier in LTSpice**  

1. **Launch LTSpice:** Open LTSpice and create a new schematic file.  

2. **Import the Library:** Load the **"tsmc018.lib"** library to ensure accurate MOSFET simulations using **TSMC 0.18µm (180nm) CMOS technology**. This library should be stored in the **same LTSpice directory** as the simulation file.  

3. **Place Components:** Add the required components from the library:  
   - **M1 & M2 (CMOSN):** Two NMOS transistors  
   - **R1, R2, RSS:** Three resistors  
   - **VDD, V2, V3:** Three voltage sources  

4. Assign Component Values as per your design

5. **Connect the Circuit:** Wire all components according to the differential amplifier schematic, ensuring correct connections between the **transistors, resistors, and voltage sources**.  

6. **Set Up Simulation:**  
   - Navigate to **"Simulate" > "Edit Simulation Cmd"**  
   - Select the **"DC op pnt"** (DC operating point) tab  

7. **Enable DC Operating Point Analysis:**  
   - Check the option to **"Calculate DC operating point"**  

8. **Run the Simulation:** Click **"Run"** to start the analysis and compute the circuit’s DC operating point.  

9. **View Simulation Results:** Use voltage and current probes to measure values at different circuit nodes.  

10. **Access Detailed Data:** Open the **SPICE Error Log** (`View > SPICE Error Log`) to review computed **DC voltages, currents, and power dissipation** across all components.  

---

### **Key Components and Their Roles**  

1. **M1 & M2 (CMOSN):** NMOS transistors that amplify the difference between the input signals.  
   - Operate in the **saturation region** to function as amplifiers.  
2. **VDD (2V):** Provides power to the circuit, defining its operational voltage range.  
3. **R1 & R2:** Load resistors that convert the transistor's amplified current into measurable output voltage.  
4. **RSS:** A tail resistor that sets the transistor's bias current, crucial for stability and gain control.  
5. **V2 & V3:** Input voltage sources that supply the signals for differential amplification.  
This setup ensures an accurate simulation of the **differential amplifier in TSMC 0.18µm CMOS technology**, allowing for precise analysis of its behavior.

## Circuit diagram

<img width="684" alt="image" src="https://github.com/user-attachments/assets/8cd54078-f576-4b67-8a2c-983898b415c2" />
  **Component Values**
 - **NMOS Transistor Parameters:**  
     - **Model:** CMOSN  
     - **Length (L):** 272nm  
     - **Width (W):** 5.2µm  
   - **Power Supply:** VDD = **2.5V**  
   - **Input AC Signal (V2 & V3):**  
     - **DC Offset = 1.3V**  
     - **Amplitude = 50mV**  
     - **Frequency = 1kHz**  
   - **Resistors:**  
     - **R1 = R2 = 1.833kΩ**  
     - **RSS = 250Ω**

## DC Analysis
![WhatsApp Image 2025-03-08 at 00 11 19_0b5e1ef0](https://github.com/user-attachments/assets/e04611f0-32be-44af-9a1d-80599ed8e4b3)
### **DC Analysis of the Differential Amplifier**  

DC analysis is performed to verify that the MOSFET operates in the **saturation region** and to determine the **DC operating point** of the transistor.  

#### **Key Calculations:**  

- **Bias Current (Iss):**  
  \[
  I_{ss} = \frac{P}{V_{DD}} = \frac{3mW}{2.5V} = 1.2mA
  \]  

- **Load Resistor (R\(_D\)):**  
  \[
  R_D = \frac{V_{DD} - V_{OCM}}{I_{D1}} = \frac{2.5V - 1.4V}{0.6mA} = 1.833kΩ
  \]  

- **Tail Resistor (R\(_{SS}\)):**  
  \[
  R_{SS} = \frac{V_P}{I_{SS}} = \frac{0.3V}{1.2mA} = 250Ω = 250Ω
  \]  

<img width="954" alt="image" src="https://github.com/user-attachments/assets/4a0b35d5-4148-476a-82b8-4a773f4a344a" />

#### **MOSFET Parameters (M1 and M2):**  

- **Drain-to-Source Voltage (V\(_{DS}\))** = 1.10V  
- **Gate-to-Source Voltage (V\(_{GS}\))** = 1.00V  
- **Threshold Voltage (V\(_{th}\))** = 0.474V  
- **Overdrive Voltage (V\(_{OV}\))**:  
  \[
  V_{OV} = V_{GS} - V_{th} = 1.00V - 0.47V = 0.53V
  \]  

Since **V\(_{DS}\) > V\(_{OV}\)**, the MOSFET operates in the **saturation region**.  

The theoretical values of **I\(_{SS}\) = 1.2mA** and **V\(_{out}\) = 1.4V** align with the simulated results, confirming the accuracy of our analysis.

## Transient analysis

Transient analysis examines how a differential amplifier responds to **time-varying input signals**, unlike DC analysis, which focuses on steady-state conditions. It evaluates **gain, linearity, phase shift, and settling time**, ensuring accurate signal processing.  

A key characteristic is the **180-degree phase shift**, where an increase in input voltage results in a decrease in output voltage. This phase inversion is crucial for **balanced signal processing and noise rejection**, making differential amplifiers ideal for **audio, sensor, and communication applications**.

![WhatsApp Image 2025-03-08 at 00 12 18_e2b45fff](https://github.com/user-attachments/assets/7599235d-2457-4bb2-bcd5-3151db28511e)
The voltage gain (\( A_v \)) of the differential amplifier is calculated as:  

\[
A_v = \frac{V_{out}}{V_{in}} = \frac{0.237}{0.103} = 2.3009
\]

Converting to decibels (dB):  

\[
\text{Gain (dB)} = 20 \log(2.3009) = 7.234 \text{ dB}
\]

## AC analysis

### **AC Analysis of a Differential Amplifier**  

AC analysis evaluates the **frequency response** of a differential amplifier, determining **gain, phase shift, and bandwidth**. Unlike transient analysis, it focuses on how the amplifier performs across different frequencies. By sweeping the input frequency, one can identify **distortions and performance limits**, making AC analysis crucial for **audio and communication applications**.

![WhatsApp Image 2025-03-08 at 00 14 35_a2551e70](https://github.com/user-attachments/assets/198b20b1-037c-430e-9fa9-29bc447b67d9)
\[
\text{Gain (dB)} = 20 \log(2.3009) = 7.234 \text{ dB}
\]
Here the value obtained from the analysis exactly equal to our theoritical value 7.234 dB.

