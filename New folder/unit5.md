## Propagation Channel Models

A propagation channel model, also known as a radio wave propagation model, characterizes radio wave propagation. **It helps predict how a radio signal will travel in a specific environment, considering factors like frequency, distance, and morphology (urban, suburban, rural)**. These models typically predict the path loss of a signal or a transmitter's effective coverage area.
![Screenshot 2024-12-03 152912](https://github.com/user-attachments/assets/b8475133-72df-40aa-bdea-723f0387bc88)

### Channel Models for 5G

5G cellular systems will operate at frequencies between 500 MHz to 100 GHz, exceeding the 6 GHz limit of previous LTE and Wi-Fi technologies and their corresponding channel models. **Therefore, accurate radio propagation models are necessary for these higher frequencies, demanding the development of new channel models**. 

The 3GPP (3rd Generation Partnership Project) has recognized this need and approved a study item to investigate channel models for frequencies from 6 GHz to 100 GHz.  This research involves identifying existing information on high frequencies, spectrum mapping, scenarios of interest, measurements, and channel model development.

![Screenshot 2024-12-03 152828](https://github.com/user-attachments/assets/ae48026a-017e-4250-93c7-cd7194d689c8)

## Channel Models in Wireless Communications

**Channel models** are used in wireless communications to characterize how radio waves propagate in different environments. They help predict signal behavior and design communication systems. Here are some common types of channel models and their characteristics:


### Objectives for New 5G Channel Models

New 5G channel models need to address the unique requirements of 5G operation, extending existing 3GPP channel models to meet the following needs:

*   **Support for Large Antenna Sets:** 5G will utilize large antenna sets, particularly at higher frequencies in millimeter wave bands. The model should support 2D and double polarized antennas in both the access point (AP) and user equipment (EU).
*   **Wide Range of Frequencies and Bandwidths:**  5G systems will operate across a wide range of frequencies and bandwidths, from hundreds of MHz to tens of GHz. The model should be scalable to these different ranges.
*   **Various Propagation Environments:** 5G will be deployed in diverse environments, including indoor, outdoor, urban, rural, high-speed trains, and more. The model needs to be adaptable to these different environments.
*   **Support for New Scenarios:** The model should be adaptable to scenarios like device-to-device (D2D) and vehicle-to-vehicle (V2V) communication. 
*   **Spatial, Temporal, and Frequency Coherence:** The new channel model must ensure spatial, temporal, and frequency coherence.
*   **Channel State Representation:**  The model should represent channel states like line-of-sight (LOS) and non-line-of-sight (NLOS) for different locations. 

##  5G Channel Hierarchy
**The detail structured hierarchy of channels within the 5G NR radio access network, designed for the efficient organization and transmission of data over the radio interface.** This hierarchy comprises three main types of channels:

*   **Logical Channels:** Situated at the highest level, logical channels categorize data based on the type of information being transported.  They are further classified into: 
    *   **Control Channels:**  These channels carry signaling and control information associated with the control plane. Examples include the Broadcast Control Channel (BCCH) for transmitting system information and the Paging Control Channel (PCCH) for locating UEs.
    *   **Traffic Channels:**  These channels transport user data belonging to the user plane. An example is the Dedicated Traffic Channel (DTCH), used to carry user information between a specific UE and the network.
*   **Transport Channels:** Acting as an intermediary, transport channels manage the multiplexing of logical data for transmission by the physical layer over the radio interface. They prepare the logical channel data for efficient physical transmission. 
*   **Physical Channels:** Occupying the lowest level of the hierarchy, physical channels are directly responsible for carrying information over the 5G radio interface. They handle the actual transmission of data through the RF signal. They also carry physical layer data, including modulation schemes, reference signals, and transmission power, necessary for maintaining and optimizing the radio link.

**The hierarchy functions by mapping or embedding higher-level channels within lower-level channels. ** This process continues until the physical layer transmits the packaged data over the RF signal. **This systematic approach ensures a logical and manageable flow of data from the top layers of the protocol stack to the physical transmission.**


## Mapping Logical Channels in 5G NR


This hierarchical structure involves mapping higher-level channels onto lower-level channels, ensuring efficient data flow from the protocol stack's top layers down to the physical layer where actual transmission occurs. 

**Channel mapping** in 5G NR involves associating logical channels with transport channels and then mapping those to physical channels for transmission over the air interface. This process is essential for efficient data transfer and resource management. However, 5G NR deployments present unique challenges:

### Challenges:

* **Wider Bandwidths:** 5G NR supports much wider bandwidths than previous generations, requiring more complex channel mapping schemes to accommodate the increased data rates.
* **Higher Frequencies:** The use of higher frequencies, particularly in the mmWave band, leads to more severe path loss and fading, making channel estimation and mapping more challenging.
* **Massive MIMO:** The use of massive MIMO with a large number of antennas increases the complexity of channel mapping and requires sophisticated beamforming techniques.
* **Dynamic Environment:** The 5G environment is highly dynamic, with user mobility and varying channel conditions, demanding adaptive channel mapping strategies.
* **Diverse Services:** 5G NR needs to support diverse services with different quality of service (QoS) requirements, such as eMBB, uRLLC, and mMTC, necessitating flexible channel mapping to meet these demands.

### Methods to Overcome Challenges:

* **Advanced Channel Estimation Techniques:** Utilize advanced channel estimation techniques that can handle the complexities of wideband, high-frequency channels and massive MIMO systems. Examples include:
    * Compressed sensing for efficient channel estimation with reduced pilot overhead.
    * Machine learning algorithms to predict channel dynamics and optimize mapping.
* **Beamforming Optimization:** Optimize beamforming strategies to mitigate path loss and improve signal quality for specific users or groups of users. This can involve:
    * Adaptive beamforming that dynamically adjusts beam directions based on channel conditions.
    * Multi-user beamforming that serves multiple users simultaneously with different beams.
* **Dynamic Channel Allocation:** Employ dynamic channel allocation schemes that adapt to changing channel conditions and user demands. This can involve:
    * Frequency-selective scheduling that assigns users to the best available frequency resources.
    * Time-domain resource allocation that dynamically adjusts transmission time slots.
* **Network Slicing:** Leverage network slicing to create dedicated virtualized network resources for different services. This allows for optimized channel mapping and resource allocation based on the specific requirements of each slice.
* **Edge Computing:** Utilize mobile edge computing (MEC) to process channel information and make mapping decisions closer to the user. This reduces latency and enables more responsive channel mapping adaptations.


### NR Logical Channels

**The NR Logical Channels are the highest level within this hierarchy, categorizing data based on its purpose.** They fall into two main categories:

*   **Control Channels:** These channels carry signaling and control information, which is essential for managing the communication link.  They handle tasks like system configuration, paging, and initial access procedures.
*   **Traffic Channels:** Responsible for transporting user data, these channels handle the actual payload information being exchanged between the user equipment (UE) and the network.

**Control Channels:**

*   **Broadcast Control Channel (BCCH):**  This downlink-only channel transmits system information from the network to UEs within the cell coverage area. Before a UE can access the network, it must acquire this system information to understand the network configuration. In standalone (SA) mode, the 5G NR network handles this. However, in non-standalone (NSA) mode, where 5G NR relies on an existing LTE network, the LTE cell provides this information, eliminating the need for a separate 5G NR BCCH.
*   **Paging Control Channel (PCCH):** Also a downlink channel, the PCCH helps locate UEs whose location is unknown to the network at the cell level. This necessitates transmitting paging messages across multiple cells.  Similar to the BCCH, the PCCH is only utilized in SA operation. In NSA operation, the LTE network handles paging, negating the need for a 5G NR PCCH. 
*   **Common Control Channel (CCCH):**  Used for both uplink and downlink communication, the CCCH transmits control information between the network and UEs that haven't established a radio resource control (RRC) connection yet. It handles the initial access procedures for UEs joining the network. 
*   **Dedicated Control Channel (DCCH):**  Operating on both uplink and downlink, the DCCH transmits dedicated control information between a specific UE and the network after the UE has established an RRC connection.  It handles the control signaling for an individual UE's communication link. 

**Traffic Channels:**

*   **Dedicated Traffic Channel (DTCH):** This bidirectional channel is dedicated to carrying user information (the actual payload) between a specific UE and the network.  It functions after the UE has established an RRC connection. 


 ### NR Transport Channels
 
 A transport channel is defined by how and with what characteristics the
 information is transmitted through the radio interface. From the physical
 layer, the MAC layer uses services in the form of transport channels. The
 data in a transport channel is organized in transport blocks.
 
*   **Broadcast Channel (BCH):**  This downlink-only channel transmits system information from the BCCH logical channel, specifically the Master Information Block (MIB).  It employs a fixed transport format defined in the 5G specifications. 
*   **Paging Channel (PCH):** A downlink channel designed to carry paging information from the PCCH logical channel, it helps locate UEs whose exact location within the cell is unknown. The PCH supports discontinuous reception (DRX) to help conserve battery power on UEs by scheduling specific times for receiving the PCH. The PCH transmits a single message to cover the entire cell or can use multiple instances with beamforming.
*   **Downlink Shared Channel (DL-SCH):** As the primary transport channel for downlink data transmission, it supports key 5G NR functionalities such as adaptive modulation, HARQ, channel-aware scheduling, and spatial multiplexing. It also carries some system information blocks (SIB) from the BCCH. Each UE has a dedicated DL-SCH for each cell it's connected to.
*   **Uplink Shared Channel (UL-SCH):**  Functioning as the counterpart to the DL-SCH, this channel handles uplink data transmission.
*   **Random-Access Channel (RACH):**  This unique transport channel doesn't transport blocks of data like the other channels.  Instead, it carries random access preambles, which help UEs coordinate their access attempts to the network and avoid message collisions. 

## NR Physical Layer Data Channels in 5G

**5G NR physical layer data channels are responsible for carrying information across the actual radio interface.** They carry the transport channels, which in turn carry logical channels, but they also include essential physical layer data required for maintaining and optimizing the radio link between the UE and the base station.  **The sources note that these physical channels share similarities with 4G LTE channels but with key updates:** PHICH and PCIICH have been removed, HARQ operation is more flexible, and the downlink control channel (PDCCH) is managed using layer 3 procedures.

![Screenshot 2024-12-03 152853](https://github.com/user-attachments/assets/4d1dc5e5-39df-4d2f-8cf8-8d4713c4a418)

## Downlink Physical Channels

*   **Physical Downlink Shared Channel (PDSCH):** PDSCH carries data that shares capacity based on time and frequency. This includes various data elements: user data, upper-layer control messages specific to the UE, system information blocks (SIBs), and paging messages.  
    *   **Key features:** 
        *   Adaptive modulation based on link conditions (signal-to-noise ratio) to optimize data rate and robustness.
        *   Flexible coding schemes for efficient data transmission.
        *   Combination of adaptive modulation and flexible coding enables dynamic adjustment of data rates based on channel quality.
*   **Physical Downlink Control Channel (PDCCH):** PDCCH carries control data for the downlink.
    *   **Key functions:**
        *   Schedules and configures downlink data transmissions on the PDSCH.
        *   Schedules and configures uplink data transmissions on the PUSCH.
    *   **Key features:** 
        *   Uses QPSK modulation for robustness. 
        *   Employs polar encoding for error correction, except for small data packets. 
*   **Physical Broadcast Channel (PBCH):**  PBCH transmits the Master Information Block (MIB) to UEs and is part of the synchronization signal block.
    *   **Key functions:**
        *   Provides UEs with essential system information (MIB). 
        *   Supports time and frequency synchronization in conjunction with the control channel.
        *   Aids in cell acquisition, selection, and reselection.
    *   **Key features:**
        *   Fixed data format for consistent transmission. 
        *   Transmits a block spanning 80 ms for reliable reception. 
        *   Utilizes QPSK modulation for robustness. 
        *   Transmits a cell-specific demodulation reference signal (DMRS) pattern that can be used to assist with beamforming.

## Uplink Physical Channels

*   **Physical Random Access Channel (PRACH):** PRACH is used by UEs for initial access to the network by transmitting a random access preamble. 
    *   **Key features:**
        *   Employs sequences of two different lengths: 
            *   Long sequences (839 symbols) for subcarrier spacings of 1.25 kHz and 5 kHz.
            *   Short sequences (139 symbols) for subcarrier spacings of 15 kHz and 30 kHz (FR1 bands) and 60 kHz and 120 kHz (FR2 bands).
*   **Physical Uplink Shared Channel (PUSCH):** PUSCH is the counterpart to PDSCH and carries data from the UL-SCH on a shared frequency and time basis.
    *   **Key features:**
        *   Similar to PDSCH, it uses a flexible format for efficient resource allocation.
        *   Frequency resource allocation is done using resource blocks. 
        *   Employs flexible coding and modulation based on the link's signal-to-noise ratio, similar to PDSCH.
        *   Includes DMRS signals to support channel estimation and demodulation. 
*   **Physical Uplink Control Channel (PUCCH):** PUCCH carries uplink control data.  
    *   **Key functions:**
        *   Transmits control information like acknowledgments (ACKs) and negative acknowledgments (NACKs).
        *   Can also carry scheduling requests from the UE.
    *   **Key features:**
        *   Designed for low-overhead control signaling.
        *   Resource allocation can allow for uplink control information to be sent on the PUSCH when necessary.



