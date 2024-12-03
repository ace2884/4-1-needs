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


## **Orthogonal Frequency Division Multiplexing (OFDM)**
OFDM is a widely used digital communication technique designed to transmit data efficiently and reliably over a range of challenging environments. It divides a wide frequency band into multiple closely spaced, orthogonal subcarriers, each carrying a portion of the overall data. 

### **Core Principles of OFDM**

1. **Multi-Carrier Transmission**: OFDM splits the available bandwidth into smaller subcarriers, each modulated independently.
2. **Orthogonality**: The subcarriers are mathematically orthogonal to each other, ensuring they do not interfere despite being closely spaced.
3. **Frequency Domain Modulation**: Data is modulated onto subcarriers in the frequency domain using techniques like QAM or PSK.
4. **Efficient Transformation**: Uses Inverse Fast Fourier Transform (IFFT) at the transmitter and Fast Fourier Transform (FFT) at the receiver for efficient signal processing.


### **How OFDM Works**

1. **Transmitter Side**:
   - **Input Data**: The input bitstream is divided into smaller blocks.
   - **Modulation**: Each block modulates a subcarrier in the frequency domain.
   - **IFFT**: Converts frequency-domain data into a time-domain signal.
   - **Cyclic Prefix**: Adds redundancy by appending a portion of the end of the signal to the beginning, mitigating inter-symbol interference (ISI).
   - **Transmission**: Sends the composite signal over the channel.

2. **Receiver Side**:
   - **Remove Cyclic Prefix**: Eliminates the cyclic prefix to restore the original signal.
   - **FFT**: Converts the time-domain signal back to the frequency domain.
   - **Demodulation**: Recovers the data from individual subcarriers.




![Screenshot 2024-12-03 163413](https://github.com/user-attachments/assets/71447ae0-180f-41cc-ac0c-87db091d07d8)



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


## **Discrete Fourier Transforms (DFTs) in OFDM**

**Orthogonal Frequency Division Multiplexing (OFDM)** is a multi-carrier modulation technique used in modern wireless communication systems like Wi-Fi, LTE, and 5G. It divides the available spectrum into multiple closely spaced subcarriers, each modulated independently. 

The **Discrete Fourier Transform (DFT)** and its inverse (IDFT) are key components in OFDM systems, providing efficient implementation of modulation and demodulation. Here's an explanation:

### **How DFTs Work in OFDM**

1. **OFDM Transmission**:
   - **Input Data**: The input bitstream is divided into smaller blocks. Each block modulates a subcarrier using schemes like QAM or PSK.
   - **IDFT**: The modulated symbols are converted from the frequency domain to the time domain using the Inverse Discrete Fourier Transform (IDFT). This combines all subcarriers into a single time-domain signal.
   - **Cyclic Prefix**: To combat inter-symbol interference (ISI), a cyclic prefix (copy of the end of the signal) is added to the beginning of the time-domain signal.
   - **Transmission**: The time-domain signal is transmitted over the channel.

2. **OFDM Reception**:
   - **Remove Cyclic Prefix**: The receiver removes the cyclic prefix.
   - **DFT**: The received signal is converted back from the time domain to the frequency domain using the Discrete Fourier Transform (DFT).
   - **Demodulation**: The frequency-domain data is demodulated to retrieve the original symbols.



### **Key Features of DFT in OFDM**

1. **Orthogonality**: Ensures that subcarriers do not interfere with each other.
2. **Efficient Implementation**: Fast Fourier Transform (FFT), a computationally efficient algorithm, is used to perform DFT and IDFT.
3. **Multi-carrier System**: Enables simultaneous transmission of data across multiple subcarriers.



### **Advantages of DFT in OFDM**

1. **Spectral Efficiency**: Close spacing of subcarriers maximizes the use of available bandwidth.
2. **Resilience to Multipath Fading**: OFDM divides the channel into subcarriers, reducing the impact of fading on individual carriers.
3. **Simplified Equalization**: In the frequency domain, the equalization process is straightforward compared to the time domain.
4. **High Data Rates**: Suitable for high-speed data communication.


### **Disadvantages of DFT in OFDM**

1. **Sensitivity to Frequency Offset**: Small frequency mismatches can cause inter-carrier interference (ICI).
2. **High Peak-to-Average Power Ratio (PAPR)**: Leads to inefficient power amplification.
3. **Complexity**: Requires additional components like cyclic prefix insertion/removal and FFT operations.


##### **Example**

Consider an OFDM system with 4 subcarriers:

1. **Frequency Domain Data**:
   - Subcarrier 1: \( 1 + j \)
   - Subcarrier 2: \( -1 + j \)
   - Subcarrier 3: \( -1 - j \)
   - Subcarrier 4: \( 1 - j \)

2. **IDFT** (Time Domain Signal):
   The IDFT maps these subcarriers into a time-domain signal of 4 samples.

3. **Add Cyclic Prefix**:
   The cyclic prefix adds robustness to multipath effects.

4. **Channel Transmission**:
   The time-domain signal is transmitted and affected by the channel.

5. **DFT** (Receiver):
   At the receiver, the DFT reconstructs the original frequency-domain data.

## cyclic prefix (CP)

### *1. Mitigating Inter-Symbol Interference (ISI)*

- In wireless communication, signals reflect off objects like buildings or trees, causing *multipath propagation. Delayed versions of the transmitted signal may interfere with the next symbol, causing **Inter-Symbol Interference (ISI)*.

- A *cyclic prefix (CP)* is a copy of the last part of the symbol added to the beginning. This *guard interval* absorbs delayed signals from the previous symbol, ensuring they don’t interfere with the current one.

- Imagine typing letters on a line with a delay between strokes. If you start typing the next line too soon, letters from the previous line might overlap with the new line. Adding a blank space (CP) between lines prevents this overlap.



### *2. Maintaining Subcarrier Orthogonality*


- In OFDM, subcarriers are *orthogonal* to avoid interfering with each other. Delayed signals can disturb this orthogonality, leading to *Inter-Carrier Interference (ICI)*.


- CP ensures that the delayed signal aligns perfectly within the *FFT window*. This alignment ensures the orthogonality of subcarriers is maintained.

- Think of a group of synchronized swimmers (subcarriers) performing in harmony (orthogonality). If echoes from their movements disrupt timing, synchronization (orthogonality) is lost. CP is like a time adjustment ensuring the echoes align with the swimmers’ movements.



### *3. Simplified Equalization*


- Without CP, multipath effects make the signal processing at the receiver complex, requiring *time-domain equalization* to correct distortions.


- CP simplifies equalization by transforming the channel into a *circular convolution. This allows the receiver to apply a simple **frequency-domain multiplication* to equalize the signal.


- Imagine tuning a radio station with static. Without CP, you need to carefully adjust multiple dials (complex equalization). With CP, you just need to press a single button to cancel the static (simple equalization).



### *4. Adaptive CP Length*


- The length of the CP must be longer than the *maximum delay spread* of the channel to fully absorb reflected signals. However, longer CPs increase overhead, reducing spectral efficiency.


- In a dense city, signals reflect off many buildings, requiring a *longer CP* to handle delays. In an open field with fewer reflections, a *shorter CP* suffices, reducing overhead.



### *5. CP Overhead*


- The CP consumes time that could carry data, introducing overhead. The trade-off is between mitigating ISI/ICI and maximizing data transmission efficiency.


- If a delivery truck has a 10-hour window (symbol duration) but spends 1 hour at checkpoints (CP), only 9 hours are used for actual delivery (data transmission). Longer checkpoints (CP) ensure safe delivery but reduce efficiency.



### **What are the Key Factors to Determining CP Length?**

The cyclic prefix (CP) is a crucial element in OFDM systems like 5G NR, helping mitigate the adverse effects of multipath propagation. The length of the CP is a critical parameter that influences system performance.

* **Multipath Delay Spread:** The length of the CP is directly proportional to the multipath delay spread of the channel. A longer delay spread, indicating a greater difference in arrival times for multipath components, requires a longer CP to prevent inter-symbol interference (ISI).
* **OFDM Symbol Length:** For a given OFDM symbol length, a longer CP reduces the proportion of the symbol dedicated to actual data transmission. This trade-off must be considered to balance ISI mitigation with overall data rate.
* **System Overhead:** A longer CP increases the overhead associated with each OFDM symbol, reducing the effective data rate.




Imagine a 5G network streaming a live sports event to users in a city:  
1. *Mitigating ISI:* The CP absorbs delays caused by signals reflecting off skyscrapers, ensuring no frame overlaps with the next.  
2. *Maintaining Orthogonality:* The CP ensures each subcarrier (audio, video, subtitles) remains synchronized, avoiding interference.  
3. *Simplified Equalization:* The receiver easily compensates for channel effects, maintaining smooth playback.  
4. *Adaptive CP Length:* The system adapts the CP length for users in dense urban areas (longer CP) versus suburban areas (shorter CP).  
5. *Overhead Management:* The CP balances delay protection and bandwidth usage for optimal efficiency.


![Screenshot 2024-12-03 162630](https://github.com/user-attachments/assets/50a92ca1-01ed-4780-ae32-f42b7ec2700f)



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

