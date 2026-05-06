# 128-Channel DWDM Optical Network: Industry-Calibrated Mid-Stage DCF Architecture

![OptiSystem](https://img.shields.io/badge/Simulation-OptiSystem-blue)
![Data Rate](https://img.shields.io/badge/Capacity-1.28_Tbps-success)
![Modulation](https://img.shields.io/badge/Modulation-10_Gbps_NRZ-orange)

## 📌 Project Overview
This project presents the design, simulation, and strict mathematical optimization of a high-capacity **128-Channel Dense Wavelength Division Multiplexing (DWDM)** optical network. Simulated in OptiSystem, the transmission link spans a long-haul distance, transmitting data at **10 Gbps per channel** (Total Capacity: 1.28 Tbps). 

The primary focus of this project is the successful implementation of a highly realistic **Dual-Stage Amplification with Mid-Stage DCF (Sandwich Model)** architecture, perfectly balancing chromatic dispersion and the optical power budget using industry-standard parameters.

## 🏗️ Architectural Layout
The system mitigates fiber non-linearities (SPM, XPM, FWM) and insertion losses using a symmetrical sandwich topology:
**`Tx Array ➔ SMF (100 km) ➔ Pre-Amp EDFA ➔ DCF (20 km) ➔ Booster EDFA ➔ Demux ➔ Rx Array`**

### System Layout in OptiSystem
![System Architecture](/Images/08%20Architecture%20Design.png)
*Figure 1: The completely optimized 128-Channel DWDM Architecture in OptiSystem.*

---

## 🧮 Mathematical Validations (The Perfect Balance)
Unlike basic theoretical models, this system is meticulously calibrated to reflect real-world physical constraints and perfectly balanced mathematical budgets.

### 1. The Power Budget (Net 0 dB Loss)
The attenuation of the fibers is perfectly counterbalanced by the strategically placed optical amplifiers:
*   **Total Loss:** 100 km SMF (0.2 dB/km = **20 dB**) + 20 km DCF (0.6 dB/km = **12 dB**) = **32 dB Loss**
*   **Total Gain:** EDFA 1 (**20 dB**) + EDFA 2 (**12 dB**) = **32 dB Gain**
*   **Net Power Balance:** **0 dB** (Signal reaches the receiver exactly at optimal launch power).

### 2. The Dispersion Budget (Zero Residual Dispersion)
*   **SMF Accumulation:** 100 km × 16.75 ps/nm/km = **+1675 ps/nm**
*   **DCF Compensation:** 20 km × -83.75 ps/nm/km = **-1675 ps/nm**
*   **Net Dispersion:** **0 ps/nm**

---

## ⚙️ Industry-Calibrated Parameters

| Component | Parameter | Calibrated Value | Justification |
| :--- | :--- | :--- | :--- |
| **WDM Mux/Demux** | Bandwidth | **75 GHz** | Reduced from 100 GHz (with 100 GHz spacing) to create a **25 GHz Guard Band**, effectively filtering out inter-channel crosstalk and out-of-band ASE noise. |
| **DCF (Fiber)**| Attenuation | **0.6 dB/km** | Reflects the high insertion loss typical of heavily doped, narrow-core DCF. |
| **DCF (Fiber)**| Effective Area | **22 μm²** | Accurately models the narrow core of DCF, triggering realistic non-linear penalties. |

---

## ⏳ Simulation & Computational Runtime
Simulating a full 128-channel DWDM system with active non-linear fiber models requires substantial computational resources. The parameters and execution environment for this project are strictly documented below:

*   **Sequence Length:** 1024 bits
*   **Samples per Bit:** 32
*   **Total Samples:** 32,768 per channel
*   **Non-Linear Models:** Self-Phase Modulation (SPM) natively enabled across both SMF and DCF models.
*   **Hardware Environment:** The multi-threaded simulation was compiled and executed via the OptiSystem CIDF Scheduler on a high-performance workstation featuring an **Intel Core i9-14900K** processor paired with **64GB of RAM**.
*   **Execution Time:** ~40 minutes (Time varies slightly based on active parameter sweeps and background scheduler priorities).

---

## 📊 Performance & Results
Across the entire 128-channel spectrum, the system exhibits exceptional stability. The tight filtering (75 GHz) and perfect power balancing resulted in extremely high Q-Factors across all tested boundaries.

| Channel Number | Max. Q-Factor | Minimum BER |
| :---: | :---: | :---: |
| **Channel 1** | **21.40** | 5.39 × 10<sup>-102</sup> |
| **Channel 32** | **16.76** | 1.77 × 10<sup>-63</sup> |
| **Channel 64** | **14.90** | 1.29 × 10<sup>-50</sup> |
| **Channel 96** | **14.85** | 2.87 × 10<sup>-50</sup> |
| **Channel 98** | **15.81** | 1.21 × 10<sup>-56</sup> |
| **Channel 128** | **11.43** | 1.33 × 10<sup>-30</sup> |

### 🔬 A Note on Simulation Artifacts (BER Values)
*It is acknowledged that the extremely low BER values (e.g., $10^{-50}$ or lower) obtained here are theoretical derivatives calculated using the **Gaussian Approximation** within an ideal software environment. In a deployed real-world DWDM system, hardware imperfections, thermal fluctuations, and timing jitter naturally introduce an "Error Floor", limiting practical post-FEC BER to a range of $10^{-12}$ to $10^{-15}$. However, the exceptionally high Q-factor achieved in this simulation robustly guarantees maximum signal integrity and validates the superior efficiency of this architecture.*

---

## 👁️ Eye Diagram Snapshots
Below are the corresponding eye diagrams for the analyzed channels. The wide-open eyes with realistic noise blurs at the top boundaries visually confirm the high signal quality and presence of expected physical non-linearities.

**Channel 1 & Channel 32**
<p align="center">
  <img src="./Images/14 BER Analyzer 0.png" width="48%" />
  <img src="./Images/13 BER Analyzer 32.png" width="48%" />
</p>

**Channel 64 & Channel 96**
<p align="center">
  <img src="./Images/12 BER Analyzer 64.png" width="48%" />
  <img src="./Images/11 BER Analyzer 96.png" width="48%" />
</p>

**Channel 98 & Channel 128**
<p align="center">
  <img src="./Images/10 BER Analyzer 98.png" width="48%" />
  <img src="./Images/09 BER Analyzer 128.png" width="48%" />
</p>

## ⏳ Simulation & Computational Runtime
Simulating a full 128-channel DWDM system with active non-linear fiber models requires substantial computational resources. The parameters and execution environment for this project are strictly documented below:

*   **Sequence Length:** 1024 bits
*   **Samples per Bit:** 32
*   **Total Samples:** 32,768 per channel
*   **Non-Linear Models:** Self-Phase Modulation (SPM) natively enabled across both SMF and DCF models.
*   **Hardware Environment:** The multi-threaded simulation was compiled and executed via the OptiSystem CIDF Scheduler on a high-performance workstation featuring an **Intel Core i9-14900K** processor paired with **64GB of RAM**.
*   **Execution Time:** ~40 minutes (Time varies slightly based on active parameter sweeps and background scheduler priorities).

### OptiSystem Execution Engine
<p align="center">
  <img src="./Images/15 Total Run Time.png" width="70%" alt="OptiSystem CIDF Scheduler Runtime">
</p>
<p align="center">
  <em>Figure: The OptiSystem CIDF Scheduler showcasing the intensive ~40-minute multi-threaded calculation.</em>
</p>