# 128-Channel DWDM System: Industry-Calibrated Dispersion Compensation

## 📌 Project Overview
This repository contains the design, simulation, and performance analysis of a high-capacity **128-Channel Dense Wavelength Division Multiplexing (DWDM)** optical network operating at **10 Gbps per channel**. The system was simulated using **OptiSystem**, focusing on mitigating Chromatic Dispersion (CD) and non-linearities (SPM, XPM, FWM) over a long-haul transmission link.

The core achievement of this project is the successful implementation of a highly realistic **Dual-Stage Amplification with Mid-Stage DCF (Sandwich Model)** architecture, meticulously calibrated with real-world industry parameters.

## 🏗️ Architectural Design (The Sandwich Model)
To balance signal attenuation and fiber non-linearities, the transmission link follows this exact sequential path:
**`Tx ➔ SMF (100 km) ➔ Pre-Amp EDFA ➔ DCF (20 km) ➔ Booster EDFA ➔ Demux ➔ Rx`**

### 💡 Dispersion Balancing Strategy:
Perfect chromatic dispersion matching was achieved to ensure zero residual dispersion at the receiver:
*   **SMF Accumulation:** 100 km × 16.75 ps/nm/km = **+1675 ps/nm**
*   **DCF Compensation:** 20 km × -83.75 ps/nm/km = **-1675 ps/nm**
*   **Residual Dispersion:** **0 ps/nm**

## ⚙️ Industry-Calibrated Parameters
Unlike ideal theoretical models, this system is tuned to reflect real-world physical limitations:

| Component | Parameter | Calibrated Value | Justification |
| :--- | :--- | :--- | :--- |
| **WDM Mux/Demux** | Bandwidth | **75 GHz** | Reduced from 100 GHz to create a 25 GHz Guard Band, effectively filtering out inter-channel crosstalk and out-of-band ASE noise. |
| **DCF (Dispersion Fiber)**| Attenuation | **0.6 dB/km** | Reflects the high insertion loss typical of heavily doped, narrow-core DCF in real-world scenarios. |
| **DCF (Dispersion Fiber)**| Effective Area | **22 μm²** | Accurately models the narrow core of DCF, triggering realistic non-linear penalties (SPM). |
| **Pre-Amp (EDFA 1)** | Gain | **10 dB** | Kept moderately low to prevent launching high-power signals into the narrow-core DCF, thus minimizing SPM. |

## 📊 Performance & Results
The introduction of real-world constraints (high DCF attenuation, narrow effective area, and tight filtering) successfully normalized the system's performance, bringing the theoretical metrics down to highly realistic, industry-standard levels.

| Channel Number | Max. Q-Factor | Minimum BER |
| :---: | :---: | :---: |
| **Channel 0** | 12.93 | 1.36 × 10<sup>-38</sup> |
| **Channel 32** | 12.65 | 5.18 × 10<sup>-37</sup> |
| **Channel 64** | 11.58 | 2.18 × 10<sup>-31</sup> |
| **Channel 96** | 13.50 | 7.15 × 10<sup>-42</sup> |
| **Channel 98** | 13.42 | 2.02 × 10<sup>-41</sup> |
| **Channel 128** | 11.45 | 1.09 × 10<sup>-30</sup> |

*Note: While the BER values are simulated using the Gaussian Approximation in an ideal noise environment, the Q-Factor range of 11.4 to 13.5 strongly validates the system's robustness, placing it well above the industry minimum threshold (Q > 6) and representing an excellent, deployable design.*

## 🔬 Key Findings
1.  **Noise Suppression via Tight Filtering:** Truncating the filter bandwidth to 75 GHz isolated the main signal lobe and rejected ASE noise, proving that 100 GHz full-window filters are suboptimal for 10 Gbps NRZ modulation.
2.  **Managing the Non-linear Penalty:** The Dual-Stage EDFA deployment successfully circumvented the severe attenuation (12 dB) and high non-linearity of the 22 μm² DCF without saturating the optical receivers.

## 🛠️ Tools Used
*   **OptiSystem** (Network Architecture & Simulation)