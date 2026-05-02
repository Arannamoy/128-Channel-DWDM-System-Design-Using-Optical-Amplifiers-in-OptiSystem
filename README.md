# 128-Channel DWDM Optical Communication System with Dispersion Compensation

## 📌 Project Overview
This project simulates a high-capacity **128-Channel Dense Wavelength Division Multiplexing (DWDM)** optical communication network. The architecture is designed to transmit data over a 100 km standard single-mode optical fiber link, addressing critical linear and non-linear impairments such as attenuation, chromatic dispersion, and phase modulation.

## 🛠️ Tools & Environment
* **Software:** OptiSystem [Version 23.0]
* **Global Parameters:** Sequence length = 1024, Samples per bit = 32 (optimized for deep non-linear physical analysis).

## ⚙️ System Architecture
The system consists of a 128-channel WDM transmitter, a 100 km optical fiber link (divided into two 50 km spans) with an EDFA for loss compensation, a precise Dispersion Compensating Fiber (DCF), and a WDM Demultiplexer. 

![System Architecture](/Images/001%20Architectural%20Design.png)

### Architecture Parameters:
* **Transmitter:** 128 Channels, 100 GHz spacing, 193.1 THz start frequency, -0.8 dBm power/channel, 10 Gbps NRZ.
* **Transmission Link:** 100 km SMF (Loss: 0.2 dB/km, Dispersion: 16.75 ps/nm/km).
* **Amplification:** EDFA with 20 dB Gain and 4 dB Noise Figure.
* **Dispersion Compensation Unit:** 20 km DCF (Dispersion: -83.75 ps/nm/km) to perfectly negate the +1675 ps/nm accumulated SMF dispersion.

## 📊 Optical Spectrum Analysis
The spectrum analyzer clearly shows the multiplexed 128 channels covering a massive bandwidth without significant clipping or distortion after transmission.

![Optical Spectrum Analyzer](/Images/003%20Optical%20Spectrum%20Analyzer.png)

## 📈 Simulation Results & Eye Diagrams
The system was evaluated using BER Analyzers across multiple spectrum indices. The Cut-off frequency for receivers was optimized to `0.6 * Bit rate` and `0.75 * Bit rate` depending on the channel's noise profile.

| Channel Index | Max. Q-Factor | Min. BER | Observation |
| :--- | :--- | :--- | :--- |
| **Channel 0** | 11.51 | $5.26 \times 10^{-31}$ | Excellent transmission |
| **Channel 32** | 9.65 | $2.26 \times 10^{-22}$ | Clear eye opening |
| **Channel 64** | 11.47 | $8.47 \times 10^{-31}$ | Highly stable mid-band |
| **Channel 96** | 7.40 | $6.39 \times 10^{-14}$ | Good signal strength |
| **Channel 128** | 5.32 | $4.99 \times 10^{-08}$ | Within safe FEC limit (Q > 3.8) |

*Note: The gradual decrease in Q-factor towards higher channels (Gain Tilt) is a realistic demonstration of inter-channel power transfer (Stimulated Raman Scattering) in massive DWDM systems.*

### 👁️ Eye Diagrams (Channels 0 & 32)
![BER Analyzer Channels 0 and 32](/Images/004%20BER%20Analyzer%200%20and%2032.png)

### 👁️ Eye Diagrams (Channels 64 & 96)
![BER Analyzer Channels 64 and 96](/Images/004%20BER%20Analyzer%2064%20and%2096.png)

### 👁️ Eye Diagrams (Channels 98 & 128)
![BER Analyzer Channels 98 and 128](/Images/004%20BER%20Analyzer%2098%20and%20128.png)

## ⏱️ Computation Performance
Due to the massive 128-channel bandwidth and deep non-linear physical calculations (Sequence length: 1024), the simulation required significant computational power.

![Total Running Time](/Images/002%20Total%20Running%20Time.png)

## 💡 Conclusion
The architecture successfully establishes a stable 128-channel optical network. By mathematically aligning the DCF dispersion (-83.75 ps/nm/km over 20km) with the SMF dispersion (16.75 ps/nm/km over 100km), the chromatic dispersion was neutralized perfectly, ensuring reliable long-haul data transmission.