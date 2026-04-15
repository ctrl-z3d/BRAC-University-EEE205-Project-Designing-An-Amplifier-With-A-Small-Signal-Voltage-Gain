# -Designing-An-Amplifier-With-A-Small-Signal-Voltage-Gain
In this project, we learned about a BJT amplifier, and we also learned that 
an amplifier designed using small-signal analysis must operate with a  small input signal to maintain linear gain and proper transistor operation.

# EEE205 – Electronic Circuits I: Design Project

**Department of Electrical & Electronic Engineering, BRAC University**

---

## Objective

Design a Common Emitter BJT amplifier meeting the following specifications:

- **Voltage Gain:** |Av| = 30
- **Input Resistance:** Ri > 17.5 kΩ
- **Supply Voltage:** Single 10V DC source (Vcc = 10V)
- **Transistor:** NPN BJT

---

## Design Overview

A **Voltage Divider Biased Common Emitter (CE) BJT Amplifier** was selected for its high voltage gain and stable biasing characteristics.

### Key Design Parameters

| Parameter | Value |
|-----------|-------|
| β (beta) | 100 |
| Load Resistance (RL) | 10 kΩ |
| Collector Resistance (RC) | 13 kΩ |
| Emitter Resistance (RE) | 23.42 kΩ |
| R1 | 449 kΩ |
| R2 | 291 kΩ |
| Input Coupling Cap (C1) | 1 µF |
| Output Coupling Cap (C2) | 1 µF |
| Emitter Bypass Cap (CE) | 47 µF |
| Calculated Ri | ~17.02 kΩ |

### Design Equations

- **Voltage Gain:** |Av| = (RC ∥ RL) / re
- **Input Resistance:** Ri = R1 ∥ R2 ∥ βre
- **Emitter resistance:** re = 26mV / IE

---

## Simulation Results (PSpice)

| Quantity | Value |
|----------|-------|
| Input Voltage (Vi) | 9.995 mV |
| Output Voltage (Vo) | 264.621 mV |
| Simulated Gain \|Av\| | **≈ 26.5** |

The simulated gain closely matches the target of 30.

---

## Hardware Results

**Transistor used:** C828 (NPN BJT)

| Quantity | Value |
|----------|-------|
| Input Voltage (Vi) | 100 mV |
| Output Voltage (Vo) | 300 mV |
| Measured Gain \|Av\| | **3** |

---

## What We Learned

The significant gap between simulated and hardware gain is attributed to **violation of the small-signal assumption**:

- The amplifier was designed for ~10 mV input, where the BJT stays in the active (linear) region.
- Hardware testing required a minimum of 100 mV from the function generator — 10× the design input.
- The larger signal drove the transistor into **saturation** during portions of the cycle, causing **gain compression** and non-linear behavior.
- The small-signal model breaks down under these conditions, making the theoretical gain formula invalid.

> **Conclusion:** A BJT small-signal amplifier must be driven within its linear operating range. Exceeding the design input amplitude leads to saturation, non-linearity, and reduced effective gain — regardless of correct biasing.

---

## Tools Used

- PSpice Schematics (simulation)
- Oscilloscope & AC Function Generator (hardware verification)
- DC Power Supply (10V)
