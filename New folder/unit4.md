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



###  Prefix OFDM (CP-OFDM) in 5G

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

#### Advantages of Using OFDM Waveforms:

Using **OFDM waveforms** offers several advantages:

* **Less implementation complexity**, as compared to other waveforms considered for 5G.
* **Well-understood** waveform due to its use in 4G and other wireless systems.

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
