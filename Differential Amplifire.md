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

DC analysis is performed to verify that the MOSFET operates in the **saturation region** and to determine the **DC operating point** of the transistor.  

#### **Key Calculations:**  

- **Bias Current (I_ss):**  
  *I_ss = P / V_DD = 3mW / 2.5V = 1.2mA*

- **Load Resistor (R_D):**  
  *R_D = (V_DD - V_OCM) / I_D1 = (2.5V - 1.4V) / 0.6mA = 1.833kΩ*

- **R_SS :**  
  *R_SS = V_P / I_SS = 0.3V / 1.2mA = 250Ω*


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

$$
A_v = \frac{V_{out}}{V_{in}} = \frac{0.237}{0.103} = 2.3009
$$

Converting to decibels (dB):  

$$
\text{Gain (dB)} = 20 \log(2.3009) = 7.234 \text{ dB}
$$

## DC Sweep
A **DC sweep analysis** of a differential amplifier examines how the **output voltage** responds to varying **DC input voltages**, revealing its **transfer characteristics, gain, linearity, and voltage ranges**. It helps determine the **operating point, bias conditions, and performance in low-frequency applications**, while also identifying **non-linearities and saturation effects**.
![WhatsApp Image 2025-03-08 at 21 31 25_f9f7c8ad](https://github.com/user-attachments/assets/a2b9d5e0-665f-4e75-b2a3-18e191d9561e)   

## Common-Mode Voltage Calculations

### Minimum Common-Mode Input Voltage (Vicm_min)
**Equation:**  
Vicm_min = Vth1 + Vp  

**Calculation:**  
Vicm_min = 0.474V + 0.3V  
Vicm_min = **0.774V**  

---

### Maximum Common-Mode input Voltage (Vocm_max)
**Equation:**  
Vicm_max = Vdd - (Iss × Rd) / 2 + Vth  

**Calculation:**  
Vocm_max = 2.5V - (1.2mA × 1.833kΩ) / 2 + 0.474V  
Vocm_max = **1.8742V**  

---

### Average Common-Mode Input Voltage (Vicm_avg)
**Equation:**  
Vicm_avg = (Vicm_min + Vicm_max) / 2  

**Calculation:**  
Vicm_avg = (0.774V + 1.8742V) / 2  
Vicm_avg = **1.3241V**  


## AC analysis

AC analysis evaluates the **frequency response** of a differential amplifier, determining **gain, phase shift, and bandwidth**. Unlike transient analysis, it focuses on how the amplifier performs across different frequencies. By sweeping the input frequency, one can identify **distortions and performance limits**, making AC analysis crucial for **audio and communication applications**.

![WhatsApp Image 2025-03-08 at 00 14 35_a2551e70](https://github.com/user-attachments/assets/198b20b1-037c-430e-9fa9-29bc447b67d9)

$$
\text{Gain (dB)} = 20 \log(2.3009) = 7.234 \text{ dB}
$$

Here the value obtained from the analysis exactly equal to our theoritical value 7.234 dB.

# Circuit 2
## Introduction
<img width="722" alt="image" src="https://github.com/user-attachments/assets/603263af-7b25-4571-9057-1a6e910a2de6" />

### **Modified Differential Amplifier with Current Source Biasing**  

This circuit represents an **enhanced differential amplifier**, where the traditional **tail resistor (R_SS)** is replaced by a **current source (I1)**. This modification improves **bias stability**, ensuring a **more controlled and constant current** for the differential pair (**M1 and M2**). By using a current source, the amplifier achieves **better common-mode rejection** and a **more predictable operating point**, leading to **greater accuracy and stability** in signal amplification.  

This configuration is particularly useful in applications requiring **precise signal processing** and **high immunity to common-mode noise**, such as **sensor interfaces and instrumentation circuits**. The amplifier retains its fundamental function of **differential signal amplification** while rejecting common-mode interference, but with improved **performance and reliability** due to current source biasing.  

### **Specifications**  
- **NMOS Transistor Model:** CMOSN  
- **MOSFET Length (L):** 272nm  
- **MOSFET Width (W):** 5.2µm  
- **Load Resistors (R1, R2):** 1.833kΩ  
- **Supply Voltage (V_DD):** 2.5V  
- **Input AC Signal:**  
  - DC Offset: 1.3V  
  - Amplitude: 50mV  
  - Frequency: 1kHz  

### **Key Components**  
- **M1 & M2:** NMOS transistors forming the differential pair, amplifying the input difference.  
- **R1 & R2:** Load resistors that convert the amplified differential current into voltage outputs.  
- **V3:** DC power supply providing the necessary operating voltage.  
- **I1:** Current source that stabilizes the bias current, improving performance.  
- **V1 & V2:** Differential input voltage sources applied to the amplifier.

 ## DC Analysis
 <img width="960" alt="image" src="https://github.com/user-attachments/assets/53a35d7e-f0fc-4885-a9e0-0beb0cdf5985" />

 Iss= P/Vdd = 3mW/2.5V =1.2mA

Rd=(Vdd-Vocm)/Id1 = (2.5-1.4)/0.6mA = 1.833kohm

Here the resistor Rss is replaced by current Iss=1.2mA.

Vds=1.10V

Vgs=1.00V

Vth=0.474V

Vov=1.00-0.47=0.53V

 Vds>Vov.

So, FET is in saturation region.

We can observe that even after replacing resistor Rss into current source I1 of 1.2mA,

the output voltage Vout is perfectly matching with the theoritical value i.e, 1.4V.

## Transient analysis

<img width="956" alt="image" src="https://github.com/user-attachments/assets/7309eb43-c4ad-466f-80dc-f07031be3f2a" />

We can observe 180 degree phase shift between input and output voltage, as observed in the circuit 1

$$
A_v = \frac{V_{out}}{V_{in}} = \frac{1.55-1.25}{1.36-1.26} = 3
$$

Converting to decibels (dB):  

$$
\text{Gain (dB)} = 20 \log(3) = 9.54 \text{ dB}
$$

## DC sweep

![WhatsApp Image 2025-03-08 at 21 32 45_8a15ef75](https://github.com/user-attachments/assets/62b35d3e-8414-497b-84af-c3c2f57ddc29)

**Equation:**  
Vicm_min = Vth1 + Vp  

**Calculation:**  
Vicm_min = 0.474V + 0.3V  
Vicm_min = **0.774V**  

---

### Maximum Common-Mode input Voltage (Vocm_max)
**Equation:**  
Vicm_max = Vdd - (Iss × Rd) / 2 + Vth  

**Calculation:**  
Vocm_max = 2.5V - (1.2mA × 1.833kΩ) / 2 + 0.474V  
Vocm_max = **1.8742V**  

---

### Average Common-Mode Input Voltage (Vicm_avg)
**Equation:**  
Vicm_avg = (Vicm_min + Vicm_max) / 2  

**Calculation:**  
Vicm_avg = (0.774V + 1.8742V) / 2  
Vicm_avg = **1.3241V**  

## AC analysis

![WhatsApp Image 2025-03-08 at 00 17 14_37a09490](https://github.com/user-attachments/assets/21048fac-48b2-49a0-8deb-1a3a3292975e)


$$
\text{Gain (dB)} = 20 \log(3) = 9.54 \text{ dB}
$$

Here the value obtained from the analysis exactly equal to our theoritical value 9.54dB.

# Circuit 3

## Introduction
### **Differential Amplifier with NMOS Current Source Biasing**  

This circuit showcases an **enhanced differential amplifier** where the conventional **tail resistor** is replaced with an **NMOS transistor (M3)** acting as a **current source**. This modification improves the **stability and control** of the bias current for the differential pair (**M1 and M2**), leading to a more predictable **operating point** and **enhanced common-mode rejection**.  

By using an **active NMOS current source**, the circuit achieves **greater accuracy and stability** in amplifying the difference between the input signals (**V2 and V1**). This approach provides **better bias current regulation**, which is essential for applications requiring **precise signal processing** and **strong immunity to common-mode noise**. While retaining its core functionality of **differential signal amplification**, the circuit benefits from improved **performance and reliability** due to the active biasing technique.

<img width="957" alt="image" src="https://github.com/user-attachments/assets/51d055ae-13c9-49f0-b10d-45c27418478e" />

### **Circuit Specifications**  

#### **NMOS Transistor Operation**  
- The **NMOS transistors (M1, M2, M3)** operate in the **saturation region** to function as amplifiers.  

#### **Differential Pair (M1 & M2)**  
- **Model:** CMOSN  
- **MOSFET Length (L):** 272nm  
- **MOSFET Width (W):** 5.2µm  
- **Load Resistors (R1, R2):** 1.833kΩ  
- **Supply Voltage (VDD):** 2.5V  
- **Input AC Signal:**  
  - DC Offset: **1.3V**  
  - Amplitude: **50mV**  
  - Frequency: **1kHz**  

#### **Current Source Transistor (M3)**  
- **Model:** CMOSN  
- **MOSFET Length (L):** 181.375nm  
- **MOSFET Width (W):** 21.59µm  

### Key Components and Their Roles
M1 & M2: Primary NMOS transistors forming the differential pair, responsible for amplifying the difference between the input signals (V2 and V1).
M3: NMOS transistor functioning as a current source, replacing the traditional tail resistor (R_SS) and ensuring a more stable bias current for the differential pair.
R1 & R2: Load resistors connected to the drains of M1 and M2, converting the amplified current into an output voltage.
V3: DC power supply providing the required operating voltage for the amplifier.
V1 & V2: Input voltage sources supplying the differential input signals to be amplified.

## DC Analysis

![WhatsApp Image 2025-03-07 at 20 50 21_ad74d463](https://github.com/user-attachments/assets/ec257077-1521-4afe-b89b-6082efa4ddb3)


### **For M1 and M2:**
- **Bias Current (I_ss):**  
  *I_ss = P / V_DD = 3mW / 2.5V = 1.2mA*

- **Load Resistor (R_D):**  
  *R_D = (V_DD - V_OCM) / I_D1 = (2.5V - 1.4V) / 0.6mA = 1.833kΩ*

- **R_SS :**  
  *R_SS = V_P / I_SS = 0.3V / 1.2mA = 250Ω*
   
- **Drain-to-Source Voltage (V\(_{DS}\))** = 1.10V  
- **Gate-to-Source Voltage (V\(_{GS}\))** = 1.00V  
- **Threshold Voltage (V\(_{th}\))** = 0.474V  
- **Overdrive Voltage (V\(_{OV}\))**:  
  \[
  V_{OV} = V_{GS} - V_{th} = 1.00V - 0.47V = 0.53V
  \]  

Since **V\(_{DS}\) > V\(_{OV}\)**, the MOSFET operates in the **saturation region**.  

### **For M3:**
1. **MOSFET Parameters (M3)**  
   - \(V_{ds} = 0.3V\)  
   - \(V_{gs} = 0.774V\)  
   - \(V_{ov} = 0.274V\)  

2. **Operating Region Check:**  
   - Since \(V_{gd} < V_{th}\) and \(V_{ds} > V_{ov}\), **M3 is in saturation region**.

---

### **Output Voltage Verification:**
- **Given Values:**  
  \(V_{out} = 1.4V\), \(V_p = 0.3V\)  
- **Theoretical Match:**  
  The values match theoretical calculations.

---

### **Calculation for \( V_4 \):**
\[
V_4 = V_p + V_{th} = 0.3V + 0.47V = 0.774V
\]

This confirms that the theoretical and calculated values align correctly.

## Transient analysis
![WhatsApp Image 2025-03-07 at 20 51 11_af3382e6](https://github.com/user-attachments/assets/68934f5e-0d41-4f95-a39f-f599f747eb71)

We can observe 180 degree phase shift between input and output voltage.

$$
A_v = \frac{V_{out}}{V_{in}} = \frac{1.55-1.25}{1.36-1.26} = 3
$$

Converting to decibels (dB):  

$$
\text{Gain (dB)} = 20 \log(3) = 9.54 \text{ dB}
$$

## DC sweep
<img width="960" alt="image" src="https://github.com/user-attachments/assets/75596a5e-0022-4657-9dff-b09f34d60734" />

## Common-Mode Voltage Calculations

### Minimum Common-Mode Output Voltage (Vocm_min)

#### Equation:
```
Vocm_min = Vov1 + Vov3
```

### Overdrive Voltage Calculations:

1. **Overdrive Voltage for M1 (Vov1):**  
   ```
   Vov1 = Vgd - Vth
        = 1.00V - 0.474V
        = 0.526V
   ```

2. **Overdrive Voltage for M3 (Vov3):**  
   ```
   Vov3 = Vgd - Vth
        = 0.774V - 0.5V
        = 0.274V
   ```

### Final Calculation for Vocm_min:
```
Vocm_min = Vov1 + Vov3
         = 0.526V + 0.274V
         = 0.8V
```


## AC analysis

![WhatsApp Image 2025-03-07 at 20 52 00_c466d381](https://github.com/user-attachments/assets/5b501fa6-f7d6-41ff-baaf-18888de11dd8)

$$
\text{Gain (dB)} = 20 \log(3) = 9.54 \text{ dB}
$$

## Inference

- The **differential amplifier** efficiently amplifies the difference between two input signals while suppressing common-mode interference, enhancing signal integrity.  
- **Replacing the tail resistor with a current source** significantly improves the **common-mode rejection ratio (CMRR)**, leading to better performance and stability.  
- **Increasing the MOSFET width** enhances the **gain** of the amplifier but comes at the cost of **higher power consumption**.  
- The **bias point selection** plays a crucial role in determining the **gain, linearity, and power dissipation**, affecting the overall performance of the circuit.  
- **Transient analysis** helps in understanding the amplifier’s response to **time-varying signals**, showcasing its dynamic behavior.  
- **AC analysis** provides a detailed view of the **frequency response**, helping identify the amplifier’s **bandwidth and frequency-dependent limitations**.  



