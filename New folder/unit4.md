## 5G Multiple Access Schemes

A key element of any cellular communication system is the **multiple access technology** used.  **5G multiple access schemes** are being carefully considered to ensure that the best techniques are adopted. 

* There are several **candidate 5G multiple access schemes**, each with its own advantages and disadvantages. 
* As a result, it is unlikely that **any single technique** will meet all requirements. 

The following are some of the candidate systems being considered as **5G multiple access schemes**:

*   **OFDMA (Orthogonal Frequency Division Multiple Access)**: 
    *   OFDMA has been widely used and **very successful for 4G** and could be used as a 5G multiple access scheme.
    *   However, it requires the use of **OFDM** and has some **drawbacks** due to the requirement for **orthogonality between carriers** and the use of a **cyclic prefix**. 
    *   As a result, other **multiple access schemes are being investigated**.

*   **SCMA (Sparse Code Multiple Access)**:
    *   SCMA is another idea being considered as a 5G multiple access scheme.
    *   It is effectively a **combination of OFDMA and CDMA**.
    *   Typically, with **OFDMA**, a single user is assigned to a specific subcarrier or group of subcarriers. 
    *   However, if each subcarrier has an added **spreading code**, then it could transmit data to or from **multiple users**. 
    *   This technique uses what is called **sparse code**, and a significant number of **users can be added** while maintaining **spectral efficiency** levels.

*   **NOMA (Non-Orthogonal Multiple Access)**: 
    *   NOMA is one of the techniques being considered as a 5G multiple access scheme. 
    *   NOMA **overlays multiple users** in the **power domain**, using **cancellation techniques** to eliminate the strongest signal. 
    *   NOMA could use either **OFDMA** or **DFT-spread OFDM** (Discrete Fourier Transform spread Orthogonal Frequency Division Multiplexing).



## OFDM Technology in 5G Systems

**Orthogonal Frequency Division Multiplexing (OFDM)** is a digital modulation method that has been widely used in wireless communications like WLAN, LTE, DVB-T, and 5G. OFDM is a multi-carrier modulation scheme that breaks the transmission frequency band into several contiguous narrower subbands (carriers). Each carrier is modulated individually, which can be implemented with an inverse fast Fourier transform (IFFT).

* The **OFDM signal** is more robust over a frequency selective fading channel and eliminates adjacent subcarrier crosstalk because it uses narrow orthogonal subcarriers.

* At the receiver, the **OFDM signal** can be demodulated with a fast Fourier transform (FFT) and equalized with a complex gain on each subcarrier. 
* Combining **OFDM with MIMO** can improve communication speed without increasing the frequency band.

**5G New Radio (NR)** uses a variety of different frequency bands, with assignments generally done by international agreement, although the numbering is done by 3GPP. 

* The **5G NR** specification is subdivided into two frequency bands: **FR1** (below 6 GHz) and **FR2** (mmWave). Each band has different capabilities.
* The **maximum channel bandwidth** defined for **FR1** is **100 MHz** due to the limited continuous spectrum in this crowded frequency range.
* The most commonly used band for **5G** in this range is around **3.5 GHz**.

**OFDM** was selected as the **waveform** for **Phase 1** of **5G NR**.  **CP-OFDM (Cyclic Prefix OFDM)**, the specific version of OFDM used in **5G NR**, was also selected for the **3GPP Release 15 standard**.

### The Principles of OFDM

An **OFDM signal** aggregates the information from single carrier orthogonal waveforms in the frequency domain into a time domain waveform that can be transmitted wirelessly. **Subcarriers** use either **QPSK** or **QAM** as their primary modulation method.

![Screenshot 2024-12-03 163413](https://github.com/user-attachments/assets/71447ae0-180f-41cc-ac0c-87db091d07d8)


**OFDM** arranges carriers at intervals of **1/symbol time**, so that the amplitude of other subcarriers is **0** when the amplitude of each subcarrier reaches its maximum, thus preventing inter-symbol interference. 

**Multi-carrier transmission OFDM** is also effective in multipath environments because the effects of multipath are concentrated on specific subcarriers compared to single carrier transmission, where the whole transmission is affected by the multipath. 

**OFDM (Orthogonal Frequency Division Multiplexing)** is a digital modulation technique that divides a wideband signal into multiple narrowband subcarriers. These subcarriers are orthogonal to each other, meaning their frequencies are spaced so that they do not interfere with each other. This orthogonality allows for efficient use of the available bandwidth and makes OFDM robust against frequency-selective fading, a common problem in wireless communication channels.

**Key Features of OFDM:**

* **Multi-Carrier Modulation:** OFDM transmits data over multiple parallel subcarriers, improving data rate and resilience to fading.
* **Orthogonality:** The subcarriers are carefully spaced to ensure they do not interfere with each other, enabling efficient spectral usage.
* **IFFT/FFT Implementation:** OFDM modulation and demodulation are implemented using Inverse Fast Fourier Transform (IFFT) at the transmitter and Fast Fourier Transform (FFT) at the receiver, allowing for efficient processing.
* **Resistance to Multipath Fading:** By dividing the signal into narrowband subcarriers, OFDM effectively mitigates the impact of multipath propagation, where signals arrive at the receiver at different times due to reflections and scattering.

**Applications of OFDM:**

* **4G LTE (Long-Term Evolution):** OFDM is a key technology in 4G LTE, enabling high data rates and improved spectral efficiency.
* **5G New Radio (NR):** OFDM continues to be a fundamental modulation technique in 5G NR, further optimized to support wider bandwidths and higher frequencies.
* **Wi-Fi (Wireless Fidelity):** Many Wi-Fi standards, including the latest versions, utilize OFDM for high-speed data transmission.
* **Digital Video Broadcasting (DVB):** OFDM is employed in DVB-T (Terrestrial) and DVB-H (Handheld) for digital television broadcasting.



**Key Requirements for 5G:**

* **Peak Data Rate:** 5G is expected to provide peak data rates of at least 20 Gbps downlink and 10 Gbps uplink per mobile base station, a significant increase over LTE.
* **Connection Density:** To support massive IoT deployments, 5G should be able to handle at least 1 million connected devices per square kilometer.
* **Mobility:** 5G must support seamless connectivity for users moving at speeds ranging from 0 km/h to 500 km/h.
* **Energy Efficiency:** 5G radio interfaces should be energy-efficient both under load and in idle states.
* **Spectral Efficiency:** 5G aims for a spectral efficiency of 30 bits/Hz downlink and 15 bits/Hz uplink, assuming 8x4 MIMO (8 spatial layers downlink, 4 spatial layers uplink).
* **Real-World Data Rate:** While peak data rates represent theoretical limits, the 5G specifications target per-user download speeds of 100 Mbps and upload speeds of 50 Mbps in real-world scenarios.
* **Latency:** Under ideal conditions, 5G networks should offer a maximum latency of just 4 ms, significantly lower than the 20 ms latency typical of LTE.

**advantages**:

* Multiple users can be assigned to **OFDM subcarriers**.
* Efficient frequency use due to orthogonality (1/symbol time interval).
* Resistance to transmission distortion from multipath, enabling demodulation by error correction without using a complex equalizer.

 **disadvantages**:

* The signal amplitude changes significantly, requiring amplifiers with a higher peak to average power ratio, a transmit power smaller than the average allowed by the amplifier, or a wide dynamic range.
* When the carrier interval is narrow, the OFDM effect is weaker against Doppler shift, making it preferable to use an amplifier with a wide dynamic range. 


### Requirements for the 5G Waveform

The choice of which multiple access scheme or schemes will be used with 5G will ultimately be determined through the ongoing standardization process.**Potential applications** for 5G mobile communications place specific requirements on the 5G waveform in order to provide the needed performance. These applications include the following:

*   High-speed video downloads
*   Gaming
*   Car-to-car/car-to-infrastructure communications
*   General cellular communications
*   IoT/M2M communications

The modulation scheme and the general waveform must support the following **key requirements**:

*   Capable of handling **high data rate, high bandwidth signals**
*   Capable of providing **low latency transmissions for long and short data bursts**, meaning very short transmission time intervals (TTIs) are needed
*   Able to **quickly switch between uplink and downlink** for time division duplex (TDD) systems, which are likely to be used
*   Enable the possibility of **energy-efficient communications** by minimizing turn-on times for low data rate devices 





## DFTs (Discrete Fourier Transforms) in OFDM

* **Orthogonality:** DFTs are used in OFDM to create orthogonal subcarriers, which means the subcarriers do not interfere with each other. This orthogonality is crucial for achieving high spectral efficiency and enabling efficient multiple access schemes like OFDMA. 

* **Modulation and Demodulation:** DFTs are used to modulate data onto the subcarriers at the transmitter and to demodulate the data from the subcarriers at the receiver. This process is computationally efficient due to the availability of fast Fourier transform (FFT) algorithms. 

* **Flexibility in Bandwidth Allocation:** DFT-s-OFDM (also known as SC-FDMA) offers flexibility in bandwidth allocation for different users by changing the number of subcarriers assigned to each user.  This allows the system to adapt to varying data rate requirements.

* **PAPR Reduction in Uplink:** DFT-s-OFDM is often preferred for the uplink due to its lower peak-to-average power ratio (PAPR) compared to CP-OFDM. This is advantageous for mobile devices as it improves power amplifier efficiency and extends battery life.

* **DFT Block Sizes:** The choice of DFT block size affects the flexibility and efficiency of the system. Using block sizes that are a power of 2 allows for efficient FFT implementation. However, to support a wider range of data rates, block sizes may be chosen as products of small numbers, allowing for efficient FFT implementations based on combinations of radix 2, 3, and 5.


## Cyclic Prefix OFDM (CP-OFDM) in 5G

**CP-OFDM** is the specific version of **OFDM** used in the **5G NR downlink**, the same waveform that **LTE** adopted for its downlink signal. 

In **CP-OFDM**, the **last part of the OFDM frame data** is added to the **beginning of the OFDM frame**. The **cyclic prefix (CP)** length is chosen to be **greater than the channel delay propagation**.  This technique **overcomes the inter-symbol interference** (ISI) that can result from delays and reflections.  

The **length of the channel delay** is **dependent on the frequency**, and the chosen CP must be long enough to account for both **interferences**. Therefore, the **CP length is adaptive** based on the link conditions.

**key features**

* **Mitigating Inter-Symbol Interference (ISI):** The cyclic prefix (CP) is a copy of the end of the OFDM symbol that is added to the beginning of the symbol. It acts as a guard interval to prevent ISI caused by multipath propagation, where delayed signal components from the previous symbol can interfere with the current symbol. 

* **Maintaining Subcarrier Orthogonality:** The CP ensures that the number of waveform periods within the delayed OFDM symbol is an integer multiple of the FFT period. This helps maintain the orthogonality of the subcarriers, preventing Inter-Carrier Interference (ICI).

* **Simplified Equalization:** The use of a CP allows the receiver to perform equalization using a simple frequency-domain multiplication.  This avoids the need for complex time-domain equalization techniques.

* **Adaptive CP Length:** The length of the CP is chosen to be longer than the maximum delay spread of the channel. The CP length can be adapted based on the channel conditions to optimize performance while minimizing overhead.

* **CP Overhead:** The CP introduces overhead, as it consumes a portion of the available time resources. The overhead is proportional to the CP length and inversely proportional to the OFDM symbol length. The choice of CP length involves a trade-off between ISI/ICI mitigation and overhead.

* **CP Design in 5G NR:** The CP design in 5G NR aligns symbols between different subcarrier spacing values and the reference numerology (15 kHz) to ensure compatibility and efficient resource utilization.


![Screenshot 2024-12-03 162630](https://github.com/user-attachments/assets/50a92ca1-01ed-4780-ae32-f42b7ec2700f)

#### Differences Between 4G and 5G Uplinks:

The **5G NR uplink** uses a **different format** than the 4G LTE uplink. The 5G NR uplink uses **CP-OFDM and DFT-S-OFDM-based waveforms**, providing the use of a **flexible subcarrier space**.  

While **LTE subcarriers** typically have **15 kHz separation**, 5G NR allows for subcarriers to be separated at **15 kHz x 2s**, with a **maximum separation of 240 kHz**. To preserve orthogonality of the carriers, **integral carrier separation** is required instead of fractional carrier separation.

#### Why Flexible Carrier Spacing?

**Flexible carrier spacing** adequately supports the various **spectrum bands/types and deployment models** that 5G NR needs to accommodate. For example:

* 5G NR must operate on **mmWave bands**, which have **wider channel widths** (up to 400 MHz).  

The **3GPP 5G NR Release-15 specification** details the **scalable OFDM numerology** with a 2s scale of subcarrier spacing that can scale with the channel width.  

As a result:

* The **FFT size is scaled**, preventing unnecessary processing complexity increases for **wider bandwidths**.
* Flexible carrier space provides additional **resistance to phase noise effects** within the system.


#### Why CP-OFDM for 5G New Radio?

thE **Ericsson Research** fully endorses **3GPP's** choice to use the **CP-OFDM** waveform for **5G New Radio**. Their research indicated that **CP-OFDM** was the most suitable candidate for NR because:

* **Compatibility** with multiple antenna technologies.
* **High spectral efficiency**.
* **Low implementation complexity**.
* **Well-localized** in the time domain, which is important for:
    * **Latency-critical applications**.
    * **TDD implementations**. 
* More **resistant to oscillator phase noise and Doppler** than other multi-carrier waveforms.
    * **Robustness to phase noise** is critical for operation at **high carrier frequencies** (e.g. mmWave band).

While OFDM has two main drawbacks:

* Less **frequency localization**.
* **High peak-to-average power ratio (PAPR)**.

Simple, well-established techniques, such as **clipping and filtering**, can reduce PAPR and improve frequency localization. These techniques can be easily applied to **CP-OFDM at the transmitter** independent of the receiver. 




### DFT-spread-OFDM (DFT-s-OFDM)

DFT-spread-OFDM (Discrete Fourier Transform spread Orthogonal Frequency Division Multiplexing) is a communication technique that combines **Single Carrier Frequency Division Multiple Access (SC-FDMA)** with the advantages of **Orthogonal Frequency Division Multiplexing (OFDM)**. It is widely used in **uplink transmission in LTE (Long Term Evolution)** due to its low Peak-to-Average Power Ratio (PAPR).


#### **Key Concepts:**
1. **OFDM Basics**:
   - OFDM divides the bandwidth into multiple orthogonal subcarriers, each carrying a part of the data.
   - High PAPR is a disadvantage for uplink transmission because it strains the power amplifier.

2. **DFT-Spread Process**:
   - DFT-s-OFDM preprocesses data symbols using the DFT operation before mapping them onto the OFDM subcarriers.
   - This spreading reduces PAPR, making it suitable for power-efficient uplink communications.

3. **Advantages**:
   - Combines the low PAPR characteristics of single-carrier modulation.
   - Retains the robustness against multipath fading offered by OFDM.

4. **Applications**:
   - Used in LTE and 5G for uplink transmission.
   - Efficient for power-constrained devices.



### **DFT-s-OFDM Block Diagram**
Below is a simplified sketch of the system:

```plaintext
Input Data  --->  DFT  --->  Subcarrier Mapping  --->  IFFT  --->  Cyclic Prefix Addition  --->  Transmitter
                               (Mapping symbols on
                                 OFDM subcarriers)

Receiver --->  Cyclic Prefix Removal --->  FFT ---> Subcarrier Demapping ---> IDFT ---> Recovered Data
```

#### **Steps in DFT-s-OFDM:**
1. **Input Data**: The data symbols are taken from a modulation scheme (e.g., QPSK, 16-QAM).
2. **DFT Operation**:
   - A small DFT block spreads the input data symbols across the frequency domain.
3. **Subcarrier Mapping**:
   - The DFT output is mapped onto the subcarriers in the OFDM system.
4. **IFFT Operation**:
   - Converts the frequency-domain signal to the time domain.
5. **Cyclic Prefix Addition**:
   - A cyclic prefix is added to combat inter-symbol interference (ISI) caused by multipath propagation.
6. **Transmission**: The signal is transmitted over the channel.

On the receiver side, the process is reversed:
1. **Cyclic Prefix Removal**: The cyclic prefix is removed.
2. **FFT**: Converts the received signal back to the frequency domain.
3. **Subcarrier Demapping**: Extracts the data from mapped subcarriers.
4. **IDFT**: Recovers the original data in the time domain.




## **What are the Key Factors to Determining CP Length?**

The cyclic prefix (CP) is a crucial element in OFDM systems like 5G NR, helping mitigate the adverse effects of multipath propagation. The length of the CP is a critical parameter that influences system performance.

* **Multipath Delay Spread:** The length of the CP is directly proportional to the multipath delay spread of the channel. A longer delay spread, indicating a greater difference in arrival times for multipath components, requires a longer CP to prevent inter-symbol interference (ISI).
* **OFDM Symbol Length:** For a given OFDM symbol length, a longer CP reduces the proportion of the symbol dedicated to actual data transmission. This trade-off must be considered to balance ISI mitigation with overall data rate.
* **System Overhead:** A longer CP increases the overhead associated with each OFDM symbol, reducing the effective data rate.



## **Multipath Signal Transmission.**

**Multipath signal transmission** occurs when a transmitted signal arrives at the receiver through multiple paths. This phenomenon is prevalent in wireless communication environments due to reflections, diffraction, and scattering of radio waves by obstacles such as buildings, trees, and terrain.

**Characteristics of Multipath Transmission:**

* **Delayed Arrival:** Multipath components arrive at the receiver with different delays due to varying path lengths.
* **Amplitude Variations:** The amplitude of each multipath component can differ based on the attenuation experienced along the path.
* **Phase Shifts:** The phase of each multipath component can vary due to the different distances traveled.
* **Frequency Selectivity:** Multipath propagation can cause frequency selectivity, where certain frequency components of the signal experience more attenuation than others.

**Impact of Multipath on Communication:**

* **Inter-Symbol Interference (ISI):** Delayed multipath components can overlap with subsequent symbols, causing ISI and degrading signal quality.
* **Fading:** Multipath components can combine constructively or destructively at the receiver, leading to signal fading.

**Mitigation Techniques:**

* **Cyclic Prefix (CP) in OFDM:** Adding a CP to OFDM symbols helps mitigate ISI by providing a guard interval for delayed multipath components.
* **Equalization:** Equalization techniques at the receiver can compensate for the effects of multipath by adjusting the amplitude and phase of received signal components.
* **Diversity Techniques:** Diversity techniques, such as spatial diversity (using multiple antennas) or frequency diversity, exploit multiple signal paths to improve reliability.

## **5G Modulation Schemes: PSK & QAM**

In 5G communication systems, modulation schemes like **Phase Shift Keying (PSK)** and **Quadrature Amplitude Modulation (QAM)** are used to efficiently transmit data over wireless channels. These modulation techniques encode data into electromagnetic waves by altering properties like phase and amplitude.

![Screenshot 2024-12-03 224927](https://github.com/user-attachments/assets/2ef54372-c55a-49db-835c-275a12d8cf98)


### **1. Phase Shift Keying (PSK)**

**PSK** is a modulation scheme where the phase of the carrier signal is varied to represent data symbols. Each distinct phase corresponds to a unique symbol.

![Screenshot 2024-12-03 224910](https://github.com/user-attachments/assets/16e966b4-a5b2-41b1-a063-02f56954cec7)

#### **Types of PSK**:
1. **BPSK (Binary Phase Shift Keying)**:
   - Uses two phases (0° and 180°).
   - Transmits 1 bit per symbol.
   - High noise immunity, but low spectral efficiency.
   - Example: **Data: 0 → Phase: 0°**, **Data: 1 → Phase: 180°**.

2. **QPSK (Quadrature Phase Shift Keying)**:
   - Uses four phases (0°, 90°, 180°, 270°).
   - Transmits 2 bits per symbol.
   - Balanced between efficiency and noise resistance.
   - Example: **Data: 00 → 0°**, **01 → 90°**, **10 → 180°**, **11 → 270°**.

3. **Higher-Order PSK** (e.g., 8-PSK, 16-PSK):
   - Increases the number of phases to encode more bits per symbol.
   - Example: **8-PSK** transmits 3 bits per symbol using 8 phases.
   - More efficient but less robust against noise.

---

### **2. Quadrature Amplitude Modulation (QAM)**

**QAM** combines both phase and amplitude variations to encode data. It is widely used in 5G for its high spectral efficiency.
![Screenshot 2024-12-03 224834](https://github.com/user-attachments/assets/81277d58-05a8-4122-9aad-43486aa2f0d7)

![Screenshot 2024-12-03 224842](https://github.com/user-attachments/assets/b58bc0c5-3a49-4abb-88bc-12835d44557e)

#### **Key Features of QAM**:
1. **Amplitude & Phase Encoding**:
   - Data is encoded by altering both the phase and amplitude of the carrier wave.
   - Example: A symbol might have phase = 45° and amplitude = 2.

2. **Constellation Diagram**:
   - A visual representation of QAM symbols in the complex plane.
   - Each point (symbol) represents a unique combination of amplitude and phase.

#### **Common Types of QAM**:
1. **16-QAM**:
   - Uses 16 symbols (4 amplitude levels × 4 phases).
   - Transmits 4 bits per symbol.
   - Example: Data: **1010 → Symbol at (1, 1)** in the constellation.

2. **64-QAM**:
   - Uses 64 symbols (8 amplitude levels × 8 phases).
   - Transmits 6 bits per symbol.
   - Higher efficiency but more sensitive to noise.

3. **256-QAM**:
   - Uses 256 symbols (16 amplitude levels × 16 phases).
   - Transmits 8 bits per symbol.
   - Extremely high efficiency, used in good channel conditions.

---

### **Comparison: PSK vs. QAM**

| Feature             | PSK                       | QAM                          |
|---------------------|---------------------------|------------------------------|
| **Parameter Modified** | Phase only                | Both amplitude and phase     |
| **Spectral Efficiency** | Moderate (higher-order is better) | Very high (e.g., 256-QAM)     |
| **Noise Robustness** | High (e.g., BPSK, QPSK)   | Moderate (amplitude variation is sensitive to noise) |
| **Applications**     | Low to moderate data rates | High data rate requirements   |

