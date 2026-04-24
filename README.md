# week_4
# **Experiment 4: MOS Differential Amplifier Design and Analysis**

## **Aim**

Design and analyze a MOS differential amplifier circuit for the following specifications:

- **Supply Voltage (VDD):** +0.9 V  
- **Negative Supply (VSS):** −0.9 V
- **Tail node voltage (Vp):** -0.7 V 
- **Maximum Power (P):** ≤ 1.5 mW  
- **Channel Length (L):** 360 nm  
- **Input Common Mode Voltage (VinCM):** 0 V  
- **Output Common Mode Voltage (VoCM):** 0 V

 # Differential Amplifier 



##  1. Introduction

A differential amplifier is one of the most fundamental building blocks in analog electronics. It amplifies the difference between two input signals while rejecting any signal that is common to both inputs.

Mathematically:

Vout = Ad (V1 − V2)

Where:
- Ad = Differential gain  
- V1, V2 = Input voltages  

Differential amplifiers are widely used in:
- Operational amplifiers (Op-Amps)
- Analog signal processing
- Communication systems
- Instrumentation circuits

The key advantage is its ability to reject noise, especially common-mode noise, making it highly reliable for real-world applications.

---

##  2. Basic Concept

A differential amplifier has:
- Two inputs (Vin1 and Vin2)
- One or two outputs
- A constant current source (tail current)
- Matched transistors

It produces output proportional to the difference:

If Vin1 = Vin2 → Output = 0 (ideal case)

---

##  3. Theory of Differential Amplifier

###  Differential Mode Operation

When inputs are different:

Vd = V1 − V2  

Output:

Vout = Ad × Vd  

---

###  Common Mode Operation

When both inputs are same:

Vc = (V1 + V2)/2  

Ideally:

Vout = 0  

But practically:

Vout = Ac × Vc  

---

### Common Mode Rejection Ratio (CMRR)

CMRR = Ad / Ac  

In dB:

CMRR(dB) = 20 log(Ad / Ac)  

Higher CMRR → Better noise rejection  

---

###  Small Signal Analysis

For MOS differential pair:

Drain current:

ID = (1/2) µnCox (W/L) Vov²  

Transconductance:

gm = 2ID / Vov  

Voltage gain:

Av = gm × RD  

---

##  4. Working Principle

###  Case 1: Equal Inputs (Vin1 = Vin2)

- Current splits equally
- ID1 = ID2 = ISS/2
- Output voltages are equal
- Differential output = 0

---

###  Case 2: Vin1 > Vin2

- M1 conducts more current
- M2 conducts less current
- Output at M1 side decreases
- Output at M2 side increases

Thus output depends on input difference.

---

###  Case 3: Vin1 < Vin2

- Opposite of Case 2
- Current shifts toward M2
- Output polarity reverses

---

###  Current Steering Concept

The total tail current ISS is constant.

It is "steered" between two transistors depending on input difference.

ISS = ID1 + ID2  

---

##  5. Types of Differential Amplifiers

---

###  5.1 BJT Differential Amplifier

- Uses bipolar junction transistors
- High gain
- Faster operation
- Used in early analog ICs

---

### 5.2 MOS Differential Amplifier

- Uses MOSFETs
- Low power consumption
- High input impedance
- Widely used in modern IC design

---

###  5.3 Resistive Load Differential Amplifier

- Uses resistors as load
- Simple design
- Low gain compared to active loads

---

###  5.4 Current Mirror Load Differential Amplifier

- Uses active load (MOS current mirror)
- Higher gain
- Better performance
- Used in op-amps

---

###  5.5 Single-Ended Differential Amplifier

- One output
- Simpler design
- Used in many practical circuits

---

### 5.6 Double-Ended Differential Amplifier

- Two outputs
- Better signal symmetry
- Used in high-performance circuits

---

###  5.7 Long-Tailed Pair

- Classic differential amplifier
- Uses constant current source
- Improves stability and gain

---

###  5.8 Fully Differential Amplifier

- Differential input and output
- High noise immunity
- Used in high-speed ADC/DAC systems

---

###  5.9 Telescopic Differential Amplifier

- Uses cascode structure
- High gain
- Low power
- Limited output swing

---

###  5.10 Folded Cascode Differential Amplifier

- Improved output swing
- High gain and bandwidth
- Widely used in analog ICs

---

##  6. Applications

- Operational amplifiers
- Instrumentation amplifiers
- Comparators
- Analog filters
- Communication systems
- Data converters (ADC/DAC)

---

##  7. Key Design Parameters

- Tail current (ISS)
- Overdrive voltage (Vov)
- Transconductance (gm)
- Load resistance (RD)
- Gain (Av)
- Bandwidth
- CMRR

---
# CIRCUIT 1

# Differential Amplifier Design (NMOS with Resistive Load)

##  Given Specifications

- Technology: 180 nm  
- Channel Length: L = 360 nm  
- Power Constraint: P ≤ 1.5 mW  
- Supply Voltage: VDD = 1.8 V  

---

##  Step 1: Tail Current Calculation

Total power relation:

P = VDD × I_total  

I_total = P / VDD  
I_total = 1.5 mW / 1.8 V ≈ 0.833 mA  

Tail current:

ISS ≈ 833 µA  

Branch currents:

ID1 = ID2 = ISS / 2 ≈ 416 µA  

---

##  Step 2: Overdrive Voltage

Choose:

Vov = VGS − VTH ≈ 0.2 V  

---

##  Step 3: NMOS (M1, M2) Design

Saturation current equation:

ID = (1/2) × µnCox × (W/L) × Vov²  

Rearranged:

W/L = (2ID) / (µnCox × Vov²)  

Assume:

µnCox ≈ 200 µA/V²  

Substitute:

W/L = (2 × 416 µA) / (200 × 0.2²)  
W/L = 832 / (200 × 0.04)  
W/L = 832 / 8  
W/L ≈ 104  

Thus:

(W/L)₁ = (W/L)₂ ≈ 104  

Given L = 0.36 µm:

W ≈ 104 × 0.36 ≈ 37.4 µm  

---

##  Step 4: Load Resistor Design

Assume output common-mode voltage:

Vout ≈ VDD / 2 = 0.9 V  

Voltage across RD:

VRD = VDD − Vout = 1.8 − 0.9 = 0.9 V  

RD = VRD / ID  
RD = 0.9 / 416 µA ≈ 2.16 kΩ  

---

##  Step 5: Tail Current Source (M3)

Current:

ID3 = ISS = 833 µA  

W/L = (2 × 833 µA) / (200 × 0.04)  
W/L = 1666 / 8 ≈ 208  

Thus:

(W/L)₃ ≈ 208  

Width:

W ≈ 208 × 0.36 ≈ 74.9 µm  

---

##  Step 6: Saturation Conditions

### For M1, M2:

Condition:

VDS ≥ VGS − VTH = Vov  

0.9 V ≥ 0.2 V ✔  

M1, M2 operate in saturation  

---

### For M3:

Condition:

VDS3 ≥ Vov  

Source node:

VS ≈ 0.2 V  

So:

VDS3 ≈ 0.2 V ✔  

M3 operates in saturation  

---

##  Step 7: Gain Calculation

Transconductance:

gm = 2ID / Vov  
gm = 2 × 416 µA / 0.2  
gm ≈ 4.16 mS  

Voltage gain:

Av = gm × RD  
Av = 4.16 mS × 2.16 kΩ  
Av ≈ 9  

Gain in dB:

Av(dB) = 20 log(9) ≈ 19 dB  

---

## Step 8: Final Design Summary

| Parameter | Value |
|----------|------|
| VDD | 1.8 V |
| ISS | 833 µA |
| ID (each) | 416 µA |
| Vov | 0.2 V |
| (W/L)₁,₂ | 104 |
| W₁,₂ | 37.4 µm |
| (W/L)₃ | 208 |
| W₃ | 74.9 µm |
| RD | 2.16 kΩ |
| Gain | ~9 (≈19 dB) |

---

