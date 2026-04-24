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


# step 1: DC OPERTING POINT 
Before tuning 
<img width="1600" height="820" alt="WhatsApp Image 2026-04-24 at 11 13 51 AM" src="https://github.com/user-attachments/assets/c9d68fb7-9778-4b63-8489-528dcf647abd" />


After tuning
<img width="1600" height="823" alt="WhatsApp Image 2026-04-24 at 11 20 05 AM" src="https://github.com/user-attachments/assets/bc97170e-564d-40a0-8e4b-9ac1d5efab8d" />

# 2:TRANSIENT ANLYASIS

# Input Common-Mode Range (ICMR) Analysis

##  Objective

Find:

- Minimum common-mode input voltage → VICM(min)  
- Maximum common-mode input voltage → VICM(max)  

---

##  Circuit Understanding

- NMOS differential pair (M1, M2)  
- Resistive load (RD)  
- Ideal tail current source (ISS)  
- Supply:  
  VDD = +0.9 V  
  VSS = −0.9 V  

---

##  Key Conditions

### NMOS Saturation Condition:
VDS ≥ VGS − VTH  

### Current Source Condition:
Tail node must have sufficient voltage (compliance)

---

##  Step 1: Define Voltages

Let:

VICM = common input voltage  

Source node:

VS = VICM − VGS  

Also:

VGS = VTH + Vov  

Thus:

VS = VICM − (VTH + Vov)  

---

##  Step 2: VICM(min)

Lower limit occurs when **tail current source just remains active**  

Condition:

VS ≥ VSS + VDS(sat,current source)  

Assume:

VDS(sat) ≈ Vov  

So:

VICM − (VTH + Vov) ≥ VSS + Vov  

Rearrange:

VICM ≥ VSS + VTH + 2Vov  

---

### Substitute Values

VSS = −0.9 V  
VTH ≈ 0.4 V  
Vov ≈ 0.2 V  

VICM(min) = −0.9 + 0.4 + 0.4  
VICM(min) = −0.1 V  
<img width="1600" height="813" alt="WhatsApp Image 2026-04-24 at 11 31 29 AM" src="https://github.com/user-attachments/assets/9e6985b3-e865-48ff-862a-c0591960e168" />


---

##  Step 3: VICM(max)

Upper limit occurs when **M1, M2 just remain in saturation**

Condition:

VDS ≥ Vov  

VDS = Vout − VS  

So:

Vout − VS ≥ Vov  

Substitute VS:

Vout − [VICM − (VTH + Vov)] ≥ Vov  

Simplify:

Vout − VICM + VTH + Vov ≥ Vov  

Cancel Vov:

Vout − VICM + VTH ≥ 0  

Thus:

VICM ≤ Vout + VTH  

---

###  Substitute Values

Vout ≈ 0 V (from DC analysis)  
VTH ≈ 0.4 V  

VICM(max) = 0 + 0.4  
VICM(max) = 0.4 V  
<img width="1600" height="811" alt="WhatsApp Image 2026-04-24 at 11 33 00 AM" src="https://github.com/user-attachments/assets/47a922fc-847e-4ec7-83e0-e3c25a800436" />

---

##  Final Results

| Parameter | Value |
|----------|------|
| VICM(min) | −0.1 V |
| VICM(max) | 0.4 V |

---

##  Conclusion

- Valid input common-mode range:

  VICM ∈ [−0.1 V , 0.4 V]

- Below −0.1 V:
  → Tail current source loses compliance  

- Above 0.4 V:
  → NMOS transistors enter triode region  

---

# 3: Differential Input Range for Linear Operation

##  Objective

Find the range of differential input voltage:

vid = Vin1 − Vin2  

for which the differential pair behaves as a **linear amplifier**

---

##  Concept

For a MOS differential pair:

- Linear operation occurs when **both transistors (M1, M2) are ON**
- Current splits approximately linearly between the two branches

---

##  Key Condition

Linearity is maintained when:

|vid| ≤ 2 × Vov  

Where:

Vov = VGS − VTH (overdrive voltage)

---

##  Step 1: Given Value

From design:

Vov ≈ 0.2 V  

---

##  Step 2: Differential Input Limit

|vid|max = 2 × Vov  
|vid|max = 2 × 0.2  
|vid|max = 0.4 V  

---

##  Final Result

| Parameter | Value |
|----------|------|
| Linear input range | −0.4 V ≤ vid ≤ +0.4 V |

---

##  Interpretation

- For |vid| < 0.4 V:
  → Both M1 and M2 conduct  
  → Circuit behaves as **linear amplifier**

- For |vid| > 0.4 V:
  → One transistor turns OFF  
  → Circuit behaves like a **current switch (nonlinear region)**

---

##  Conclusion

- Maximum differential input for linear operation:

  vid ∈ [−0.4 V , +0.4 V]

- For accurate amplification, operate in:

  vid ≈ ±50 mV to ±100 mV  

---

# step 2: Transient Analysis (CL = 10 pF)

### Setup:
- Apply differential input signal  
- Add load capacitor CL = 10 pF at output  

---

### (a) Case 1: vid < 2Vov (Linear Region)

Condition:

|vid| < 2Vov ≈ 0.4 V  

Example:

vid = 50 mV  
<img width="1600" height="817" alt="WhatsApp Image 2026-04-24 at 11 51 13 AM" src="https://github.com/user-attachments/assets/9e8ba618-b720-42a2-8006-7879447766f1" />


#### Observation:

- Output waveform is **sinusoidal**
- No distortion  
- Both M1 and M2 are ON  

✔ Circuit behaves as **linear amplifier**

---

### (b) Case 2: vid > 2Vov (Nonlinear Region)

Example:

vid = 0.5 V  
<img width="1917" height="975" alt="image" src="https://github.com/user-attachments/assets/b6a421f7-3c81-48b1-9ca3-75668f4b2949" />

#### Observation:

- Output becomes **distorted / clipped**
- One transistor turns OFF  
- Current steers completely to one side  

✔ Circuit behaves as **switch**

---

### (c) Comparison

| Condition | Behavior | Output |
|----------|--------|--------|
| vid < 2Vov | Linear | Sinusoidal |
| vid > 2Vov | Nonlinear | Distorted |

---

# gain cal
<img width="1918" height="977" alt="image" src="https://github.com/user-attachments/assets/ea6c4b72-c955-47e5-81f7-89d4f0d83c49" />
 
---

##  step 3: AC Analysis (Frequency Response (CL = 10 pF))

##  Simulation Setup

- AC input: differential (Vin1 = +1, Vin2 = −1)  
- Load capacitance: CL = 10 pF  
- RD = 2.16 kΩ  
- ISS = 0.833 mA  
- Technology: 180 nm  
<img width="1600" height="813" alt="WhatsApp Image 2026-04-24 at 12 07 24 PM" src="https://github.com/user-attachments/assets/bc648a48-3c19-42f4-9f48-877f610b0d2f" />

---

##  (a) Midband Gain

From LTspice cursor:

At 100 kHz:  

Gain = 16.05 dB  

Convert to linear:

Av = 10^(16.05/20) ≈ 6.35  

---

##  (b) −3 dB Bandwidth

Midband gain = 16.05 dB  

−3 dB level = 13.05 dB  

From plot:

f−3dB ≈ 5 MHz (approx)  

---

##  (c) Bandwidth (BW)

BW ≈ f−3dB ≈ 5 MHz  

---

##  (d) Gain Bandwidth Product (GBW)

GBW = Av × BW  

GBW ≈ 6.35 × 5 MHz  
GBW ≈ 31.75 MHz  

---

##  (e) Frequency Response Observation

- Flat gain region up to ~1 MHz  
- Gain starts decreasing after a few MHz  
- Single dominant pole behavior observed  
- Phase shifts from ~180° towards lower values  

---

##  (f) Comparison with Theory

| Parameter | Theoretical | Simulation | Remarks |
|----------|------------|------------|--------|
| Gain | ~9 (19 dB) | ~6.35 (16 dB) | Reduced due to ro, parasitics |
| BW | ~7.3 MHz | ~5 MHz | Load + device capacitance effect |
| GBW | ~66 MHz | ~32 MHz | Practical limitations |

---

##  (g) Reason for Differences

- Channel length modulation (ro effect)  
- Parasitic capacitances (Cgs, Cgd)  
- Non-ideal current source  
- Loading due to CL  

---

##  Final Conclusion

- Amplifier shows proper **low-pass frequency response**  
- Gain is lower than ideal due to non-ideal effects  
- Bandwidth is mainly limited by **RD × CL**  
- Simulation results are realistic and valid  

---

##  Key Takeaways

- Midband gain ≈ 16 dB  
- Bandwidth ≈ 5 MHz  
- GBW ≈ 32 MHz  
- Real circuits always show reduced gain vs theory  

---


