### 5G Multiple Access Schemes

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

**CP-OFDM** adds a higher level signal known as a **cyclic prefix** to the beginning of the **OFDM symbol**. 

* **CP-OFDM** suppresses inter-symbol interference (ISI) and inter-carrier interference (ICI) by inserting data from the end of the OFDM symbol as the cyclic prefix to the beginning of the OFDM symbol for a specific period of time.

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


## Cyclic Prefix OFDM (CP-OFDM) in 5G

**CP-OFDM** is the specific version of **OFDM** used in the **5G NR downlink**, the same waveform that **LTE** adopted for its downlink signal. 


In **CP-OFDM**, the **last part of the OFDM frame data** is added to the **beginning of the OFDM frame**. The **cyclic prefix (CP)** length is chosen to be **greater than the channel delay propagation**.  This technique **overcomes the inter-symbol interference** (ISI) that can result from delays and reflections.  

The **length of the channel delay** is **dependent on the frequency**, and the chosen CP must be long enough to account for both **interferences**. Therefore, the **CP length is adaptive** based on the link conditions.


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
