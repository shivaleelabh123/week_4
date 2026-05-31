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
<img width="1663" height="982" alt="image" src="https://github.com/user-attachments/assets/cc9dd04e-ac1c-49c5-a2ac-7c1d8a36d4ad" />

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

##  Step 5: Saturation Conditions

### For M1, M2:

Condition:

VDS ≥ VGS − VTH = Vov  

0.9 V ≥ 0.2 V ✔  

M1, M2 operate in saturation  

---

##  Step 6: Gain Calculation

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

## Step 7: Final Design Summary

| Parameter | Value |
|----------|------|
| VDD | 1.8 V |
| ISS | 833 µA |
| ID (each) | 416 µA |
| Vov | 0.2 V |
| (W/L)₁,₂ | 104 |
| W₁,₂ | 37.4 µm |
| RD | 2.16 kΩ |
| Gain | ~9 (≈19 dB) |

---

# step 1:
# 1: DC OPERTING POINT 
Before tuning 
<img width="1600" height="820" alt="WhatsApp Image 2026-04-24 at 11 13 51 AM" src="https://github.com/user-attachments/assets/c9d68fb7-9778-4b63-8489-528dcf647abd" />


After tuning
<img width="1600" height="823" alt="WhatsApp Image 2026-04-24 at 11 20 05 AM" src="https://github.com/user-attachments/assets/bc97170e-564d-40a0-8e4b-9ac1d5efab8d" />


# 2:Input Common-Mode Range (ICMR) Analysis

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

# step 2:
# Transient Analysis (CL = 10 pF)

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

# gain calculation
<img width="1918" height="977" alt="image" src="https://github.com/user-attachments/assets/ea6c4b72-c955-47e5-81f7-89d4f0d83c49" />
 
---

##  step 3:
# AC Analysis (Frequency Response (CL = 10 pF))

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


# step 4: Comparison of Theoretical vs Simulation Results

## 1. DC Operating Point

| Parameter | Theoretical | Simulation | Observation |
|----------|------------|------------|-------------|
| Tail current (ISS) | 833 µA | ~830–840 µA | Very close  |
| Branch current (ID1 = ID2) | 416 µA | ~410–420 µA | Good matching  |
| Output voltage (VoCM) | ~0 V | ~0 V | Correct biasing  |
| Tail node voltage | ≈ −0.7 V | ~−0.7 V | Matches |

### Conclusion:
- DC biasing is accurate  
- Transistors operate in saturation  
- Circuit is properly designed  

---

## 2. Gain Comparison

### Theoretical:
Av = gm × RD  
Av ≈ 9  
Av(dB) ≈ 19 dB  

### Simulation:
Av ≈ 6.35  
Av ≈ 16.05 dB  

### Comparison:

| Parameter | Theoretical | Simulation | Difference |
|----------|------------|------------|------------|
| Gain (Av) | ~9 | ~6.35 | Reduced |
| Gain (dB) | ~19 dB | ~16 dB | ~3 dB lower |

### Reason:
- Finite output resistance (ro)  
- Channel length modulation  
- Non-ideal current source  
- Loading effects  

Actual gain:
Av = gm × (RD || ro)

---

## 3. Bandwidth Comparison

### Theoretical:
f-3dB ≈ 7.3 MHz  

### Simulation:
f-3dB ≈ 5 MHz  

### Comparison:

| Parameter | Theoretical | Simulation | Difference |
|----------|------------|------------|------------|
| Bandwidth | ~7.3 MHz | ~5 MHz | Reduced |

### Reason:
- Parasitic capacitances (Cgs, Cgd)  
- Miller effect  
- Layout/wiring capacitance  

---

## 4. Gain Bandwidth Product (GBW)

### Theoretical:
GBW ≈ 9 × 7.3 ≈ 66 MHz  

### Simulation:
GBW ≈ 6.35 × 5 ≈ 31.75 MHz  

### Comparison:

| Parameter | Theoretical | Simulation |
|----------|------------|------------|
| GBW | ~66 MHz | ~32 MHz |

### Reason:
- Reduction in both gain and bandwidth  

---

## 5. ICMR Comparison

| Parameter | Theoretical | Simulation | Observation |
|----------|------------|------------|-------------|
| VICM(min) | −0.1 V | ~−0.1 V | Matches ✔ |
| VICM(max) | 0.4 V | ~0.35–0.4 V | Slight variation |

### Reason:
- Threshold voltage variation  
- Non-ideal MOS behavior  

---

## 6. Differential Input Range

| Parameter | Theoretical | Simulation | Observation |
|----------|------------|------------|-------------|
| Linear range | ±0.4 V | ~±0.35–0.4 V | Close ✔ |

### Observation:
- Both transistors ON in linear region  
- Matches expected behavior  

---

## 7. Transient Analysis

| Condition | Theory | Simulation | Result |
|----------|-------|------------|--------|
| |vid| < 2Vov | Linear | Sinusoidal output | ✔ |
| |vid| > 2Vov | Nonlinear | Distorted output | ✔ |

---

## 8. Overall Summary

| Parameter | Theoretical | Simulation | Status |
|----------|------------|------------|--------|
| Gain | 19 dB | 16 dB | Lower |
| Bandwidth | 7.3 MHz | 5 MHz | Lower |
| GBW | 66 MHz | 32 MHz | Lower |
| ICMR | Accurate | Matches | Good |
| Linearity | ±0.4 V | Matches | Good |
| DC Bias | Ideal | Matches | Good |

---

## Final Conclusion

- The MOS differential amplifier operates correctly as per design  
- DC operating point closely matches theoretical values  
- Gain and bandwidth are lower in simulation due to non-ideal effects:
  - Channel length modulation  
  - Parasitic capacitances  
  - Finite output resistance  
- The circuit behaves:
  - As a linear amplifier for small signals  
  - As a switch for large signals  
- Overall, simulation results validate the theoretical design with expected practical deviations


### CERCUIT 2:

# Differential Amplifier Design (Active Load / Current Mirror Load)
<img width="1907" height="982" alt="image" src="https://github.com/user-attachments/assets/3569c911-14af-4409-a7d8-28d6f092f57c" />

## Step 1: DC Analysis

From the LTspice operating point (.op) simulation results:<img width="1600" height="816" alt="WhatsApp Image 2026-05-31 at 11 27 33 PM" src="https://github.com/user-attachments/assets/bf1e7747-ad57-41ca-8c9c-592230179af2" />


### Voltages:
- **V(n001) [VDD]:** 0.9 V
- **V(n002) [Bias Voltage]:** -0.37 V
- **V(n003) [VSS]:** -0.9 V
- **V(vin1):** 0 V
- **V(vin2):** 0 V
- **V(vout1):** 0.04135 V (≈ 0 V)
- **V(vout2):** 0.04135 V (≈ 0 V)
- **V(vp) [Tail Node]:** -0.70115 V (Perfectly matches the -0.7 V target)

### Currents:
- **Total Sinking Tail Current Id(M5):** 0.002107 A (2.107 mA)
- **Branch NMOS Currents Id(M1) & Id(M2):** 0.001053 A (1.053 mA) each
- **Load PMOS Currents Id(M3) & Id(M4):** 0.001053 A (1.053 mA) each

### Key DC Observations:
- **Tail Headroom Voltage:** VDS5 = Vp - VSS = -0.70115 V - (-0.9 V) = 0.19885 V ≈ 0.2 V.
- **Symmetry Check:** The total tail current of 2.107 mA splits perfectly down the center with exactly 1.053 mA passing through each branch.
- **Output Common Mode Alignment:** Both Vout1 and Vout2 settle stably at 41.35 mV, satisfying the required 0 V output bias target.

---

## Step 2: Transient Analysis

### (a) Case 1: vid < 2Vov (Linear Region)
- **Setup:** Input amplitude set to 10mV (`SINE(0 10m 1k)`).
- **Waveform Plot:**
<img width="1600" height="815" alt="WhatsApp Image 2026-05-31 at 11 26 22 PM" src="https://github.com/user-attachments/assets/018d7f2c-5bd3-45a4-ba5c-68d46e2ee21c" />

- **Observation:** - Input signals V(vin1) and V(vin2) are standard small-signal differential sine waves.
  - Output waveforms V(vout1) and V(vout2) show safe, stable, inverted sinusoidal tracking without harmonic distortion.
  - Circuit behaves perfectly as a linear differential amplifier.

---

### (b) Case 2: vid > 2Vov (Nonlinear / Clipped Region)
- **Setup:** Input amplitude increased to 300mV (`SINE(0 300m 1k)`).
- **Waveform Plot:**
<img width="1600" height="815" alt="WhatsApp Image 2026-05-31 at 11 29 55 PM" src="https://github.com/user-attachments/assets/deb1c450-e9bc-4f55-a017-fe9b9fdbf8fd" />

- **Observation:**
  - The massive 300 mV input dynamic swing completely overdrives the differential stage.
  - The output voltage swings completely between the upper and lower headroom boundaries, leading to severe flatline compression clipping.
  - The circuit drops out of active linear amplification and functions cleanly as a current switch.

---

## Step 3: AC Analysis (Frequency Response)

- **Simulation Traces:**
<img width="1600" height="852" alt="WhatsApp Image 2026-05-31 at 11 46 42 PM" src="https://github.com/user-attachments/assets/e29b5af9-62dd-4562-8cf1-a14deabdb393" />

From the simulated AC response plots:

- **(a) Midband Gain:** - The low-frequency flat band gain records a peak magnitude value of **3.81 dB**.
  - Convert to linear scale: Av = 10^(3.81 / 20) ≈ 1.55 V/V.

- **(b) -3 dB Bandwidth (BW):**
  - Midband Gain = 3.81 dB.
  - Half-power boundary location (-3 dB level) = 0.81 dB.
  - Cutoff frequency measured at the 0.81 dB drop marker: **f-3dB ≈ 26.81 MHz**.

- **(c) Unity Gain Frequency / Bandwidth (UGB):**
  - The frequency marker where the magnitude curve drops down across the 0 dB reference line: **f-0dB ≈ 87.91 MHz**.

- **(d) Gain Bandwidth Product (GBP):**
  - GBP = Linear Gain × -3 dB Bandwidth
  - GBP = 1.55 × 26.81 MHz ≈ **41.56 MHz**.

---

## Inference and Structural Summary 

- **Active Load Advantages:** Substituting passive resistors with active PMOS loads ($M_3, M_4$) yields substantial silicon real estate area savings and improves layout matching constraints.
- **Headroom vs. Swing Limitations:** The overall output range is restricted by the minimum saturation voltage requirements ($V_{DS(sat)}$) needed to keep the stacked active NMOS driver and PMOS load configurations functioning inside their saturation regions.
- **Dominant Pole Action:** Because the active load nodes present a high small-signal incremental channel output resistance ($R_{out} \approx r_{o} \parallel r_{o}$), it interacts directly with the $C_L = 10\text{ pF}$ external capacitor to dictate a low-frequency dominant pole roll-off.



### CIRCUIT 3

<img width="1917" height="983" alt="image" src="https://github.com/user-attachments/assets/f6e5acc8-605f-4c29-a9fe-729da5c463a9" />

# CMOS Current Mirror (Differential to Single-Ended)

## Step 1: DC Analysis

From the LTspice operating point (.op) simulation logs:

### Voltages:
- **V(n001) [Bias V5]:** 0.3 V
- **V(n002) [VDD]:** 0.9 V
- **V(n003):** 0.7956 V
- **V(n004):** 0.7956 V
- **V(n005) [Gate Bias V3]:** -0.37 V
- **V(n006):** -0.78208 V
- **V(n007) [VSS]:** -0.9 V
- **V(vin1):** 0 V
- **V(vin2):** 0 V
- **V(vout1):** 0.85215 V
- **V(vout2):** 0.85215 V
- **V(vp) [Tail Node]:** -0.51117 V

### Currents:
- **Branch NMOS Currents Id(M1) & Id(M2):** 0.0001973 A (197.3 µA) each
- **Load PMOS Currents Id(M3) & Id(M4):** 0.0001973 A (197.3 µA) each

### Key DC Observations:
- **Current Matching:** Branch currents are symmetrically balanced at 197.3 µA under zero differential input configuration.
- **Output Setup:** The operating point levels out both output nodes at a matching quiescent level of 0.852 V prior to dynamic signal entry.
<img width="1600" height="824" alt="WhatsApp Image 2026-06-01 at 12 28 54 AM" src="https://github.com/user-attachments/assets/7cb882e8-83d5-4053-bfbb-fde4935f3d5c" />

---

## Step 2: Transient Analysis

### (a) Case 1: vid < 2Vov (Linear Region)
- **Setup:** Input amplitude set to 10mV (`SINE(0 10m 1k)`).
- **Waveform Plot:**
<img width="1600" height="814" alt="WhatsApp Image 2026-06-01 at 12 32 10 AM" src="https://github.com/user-attachments/assets/2e061f5b-8f64-49c0-8626-d81967ad8d7e" />

- **Observation:**
  - V(vout1) and V(vout2) trace out balanced, clean, out-of-phase differential sine waves.
  - The peak-to-peak output swing scales smoothly without any distortion artifacts.
  - Circuit functions cleanly within its linear amplification limits.

---

### (b) Case 2: vid > 2Vov (Nonlinear / Clipped Region)
- **Setup:** Input amplitude increased to 300mV (`SINE(0 300m 1k)`).
- **Waveform Plot:**
<img width="1600" height="824" alt="WhatsApp Image 2026-06-01 at 12 33 22 AM" src="https://github.com/user-attachments/assets/0caa3aef-b64c-4705-ac3f-56ec7bdaf929" />

- **Observation:**
  - The massive 300 mV input amplitude overdrives the active differential matching core.
  - The signal faces severe flatline clipping distortion as it hits the voltage headroom boundaries of the active current mirror configuration.
  - Circuit saturates entirely and acts like a non-linear current switch.

---

## Step 3: AC Analysis (Frequency Response)

- **Simulation Traces:**
<img width="1600" height="822" alt="WhatsApp Image 2026-06-01 at 12 37 21 AM" src="https://github.com/user-attachments/assets/8f3053a7-8415-4deb-9044-f99c79030f21" />

From the simulated AC frequency sweeps:

- **(a) Midband Gain:**
  - The low-frequency flat band gain records a maximum magnitude value of **2.01 dB**.
  - Convert to linear scale: Av = 10^(2.01 / 20) ≈ 1.26 V/V.

- **(b) -3 dB Bandwidth (BW):**
  - Midband Gain = 2.01 dB.
  - Half-power boundary location (-3 dB level) = -0.99 dB.
  - Cutoff frequency measured at the -0.99 dB drop marker: **f-3dB ≈ 26.81 MHz**.

- **(c) Unity Gain Frequency / Bandwidth (UGB):**
  - The frequency marker location where the magnitude curve crosses the 0 dB reference baseline: **f-0dB ≈ 87.91 MHz**.

- **(d) Gain Bandwidth Product (GBP):**
  - GBP = Linear Gain × -3 dB Bandwidth
  - GBP = 1.26 × 26.81 MHz ≈ **33.78 MHz**.

---

## Inference and Structural Summary 

- **Differential to Single-Ended Conversion:** This configuration uses a PMOS current mirror active load to cleanly convert a differential input signal into a single-ended output reference.
- **Transconductance Doubling Effect:** The active current mirror architecture routes current from the opposite branch to combine in-phase at the primary output node, effectively doubling the stage's transconductance.
- **Frequency Pole Limits:** The high internal small-signal resistance profile ($r_o \parallel r_o$) interacts with the load capacitance ($C_L = 10\text{ pF}$) to create a lower-frequency dominant pole, capping high-frequency gain performance.





#### Comparative Analysis of Circuits 1, 2, and 3

| Comparison Parameter | Circuit 1: NMOS with Resistive Load | Circuit 2: NMOS with Active Load | Circuit 3: CMOS Current Mirror (Diff to Single-Ended) |
| :--- | :--- | :--- | :--- |
| **Voltage Gain (Av)** | **Highest (16.05 dB / ~6.35 V/V)**<br>Limited strictly by gm × RD. | **Moderate-Low (3.81 dB / ~1.55 V/V)**<br>Reduced due to specific biasing constraints. | **Lowest (2.01 dB / ~1.26 V/V)**<br>Features transconductance doubling but experiences loading limitations. |
| **Power Consumption** | **Moderate (~1.50 mW)**<br>Tail current: ~833 µA @ 1.8 V total supply. | **Highest (~3.79 mW)**<br>Tail current: ~2.107 mA @ 1.8 V total supply. | **Lowest (~0.71 mW)**<br>Tail current: ~394.6 µA @ 1.8 V total supply. |
| **Silicon Area** | **Extremely Large**<br>Passive resistors (RD = 2.16 kΩ) occupy massive IC real estate. | **Small / Compact**<br>Bulky resistors are replaced with compact active PMOS loads. | **Minimal / Most Compact**<br>All-MOS implementation with single-ended output routing savings. |
| **Input Common-Mode Range (ICMR)** | **Symmetric (–0.1 V to 0.4 V)**<br>Bounded tightly by tail compliance and driver triode limits. | **Highly Constrained**<br>Requires sufficient headroom to keep the active PMOS and NMOS stacked pairs saturated. | **Flexible**<br>Biased at a lower branch current, which relaxes compliance limits on the tail node. |
| **Output Voltage Swing** | **Symmetric & Wide**<br>Can swing closely to VDD since voltage drops purely across RD. | **Moderately Restricted**<br>Limited symmetrically by the saturation requirements (VDS(sat)) of M3/M4. | **Asymmetric**<br>Single-ended output topology limits the swing boundaries based on the current mirror tracking. |
| **Output Type** | Differential (Double-Ended) | Differential (Double-Ended) | Single-Ended |
