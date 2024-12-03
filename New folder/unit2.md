## Mobile Network Technologies of 5G

In preparation for the deployment of 5G mobile communication networks, it's important to address not just wireless networks but also fixed networks and the overall communication network architecture. One crucial aspect of this is network softwarization and slicing.

#### Network Softwarization and Slicing 

*   **Network Softwarization:** Involves managing and controlling network functions and components through software programming, enabling greater flexibility and speed in network configuration and management. This approach allows for rapid adaptation to changing traffic patterns and the dynamic allocation of resources based on specific application requirements.
*   **Slicing:** Creates logically isolated network partitions within the shared physical infrastructure. These slices can be tailored with specific network characteristics, such as bandwidth, latency, and security, to meet the unique needs of different applications and services. For example, one slice could be optimized for low-latency communication for autonomous driving, while another slice could be configured for high bandwidth video streaming.



![Screenshot 2024-12-03 144934](https://github.com/user-attachments/assets/5c0a444a-6ffa-4a93-88a6-7e4b5798b373)

**Figure** illustrates the network softwarization view of 5G systems. It shows how slices are created within a physical infrastructure using "network management and orchestration". Each slice consists of interconnected virtual or physical network functions, forming an end-to-end network system. In the figure, Slice A comprises a radio access network (RAN), a mobile packet core, UE/device, and cloud, all made up of virtual or physical network functions.

#### Benefits of Network Softwarization and Slicing

Network softwarization significantly enhances flexibility in the design, implementation, deployment, operation, and maintenance of network functions and components. It also accelerates service delivery by leveraging the programmability of software. The application of **slicing** further improves efficiency and dynamics in 5G systems by enabling the just-in-time assembly of network functions and components for service delivery.

#### The Need for Advanced Slicing in 5G

Given the wide range of application domains in the 5G or IMT-2020 network, extending the concept of slicing beyond the capabilities of current SDN/NFV technologies is crucial. This requires addressing how to effectively utilize slices created on a programmable software-defined infrastructure. 

The 5G network must accommodate various traffic types with diverse requirements, ranging from high-bandwidth video downloads to low-latency remote control applications and low-data-rate IoT communications.  Slicing enables the configuration of different network types for individual users based on their specific needs, allowing the same hardware to provide, for example, low latency for one user and voice communication for another, using different software configurations. 



## Understanding the 5G Next Generation Core Network

While initial 5G deployments relied on existing core LTE or even 3G networks, the **5G Next Generation Core Network (NGCN)** represents a significant departure, essential for achieving the high data capacity and low latency promised by 5G.  It plays a crucial role in enabling the overall performance of the 5G mobile communication system to meet its ambitious performance goals.

The development and definition of the NGCN architecture is the responsibility of the 3GPP System Architecture Technical Specification (SA) Group, which works within the framework of Service and System Aspects.

#### Addressing the Diverse Demands of 5G Applications

One of the primary challenges in developing the 5G NGCN is accommodating the diverse requirements of various applications. The 5G network needs to support a wide range of traffic types, each with distinct needs:

*   **Very high bandwidth communications:**  For applications like ultra-high definition video streaming and large file downloads.
*   **Extremely low latency communications:** Essential for time-sensitive applications such as remote surgery, industrial automation, and autonomous driving.
*   **Low data rate communications:** For machine-to-machine (M2M) and IoT applications, often involving a massive number of devices with low bandwidth requirements.
*   **Conventional applications:** Including voice calls, internet browsing, and other familiar services that users have come to expect.

* To achieve the requirements for the 5G network, various techniques are being employed.
 This will make the 5G network considerably more scalable, flexible, and
 efficient.

- **Software defined networking, SDN**:   Using software defined
 networks; it is possible to run the network using software instead of
 hardware. This provides significant improvements in terms of
 flexibility and efficiency..
- **Network functions virtualisation, NFV:**   When using software
 defined networks, it is possible to execute the different network
 functions using only software. This means that generic hardware can be
 reconfigured to provide different functions and can be deployed as
 needed on the network
- **Network slicing:**   Since 5G will require very different network types
 for different applications, a scheme known as network segmentation
 has been devices. Using SDN and NFV it will be possible to configure
 the type of network that an individual user will require for their
 application. In this way, the same hardware using different software
 can provide a low latency level for one user, while providing voice
 communications for another using different software, and other users
 may want other types of network performance and each You can have a
 portion of the network with the required Performance




## 5G Standardization

*   Like other widely adopted systems, 5G mobile communications rely on a set of standards governed by the **3rd Generation Partnership Project (3GPP)**. 
*   3GPP, building upon the standards of previous generations (2G GSM, 3G UMTS, and 4G LTE), establishes the standards for 5G. 
*   3GPP consists of various working groups, each focusing on different aspects of the standard and involving industry experts from various mobile communication companies. This collaborative approach ensures:
    *   Stakeholders can contribute to the development of the standards.
    *   Different companies can work on different components of the system, knowing they will seamlessly integrate.
    *   Users can experience interoperability and roaming capabilities.
*   New versions of 3GPP standards encompass updates and new functionalities for previous systems, ensuring backward compatibility and a smooth transition.

## Cellular Systems Overview

*   **First Generation (1G):** Analog phones, revolutionary for their time, but limited in spectrum efficiency and security.
*   **Second Generation (2G):** Introduced digital technology, improving spectrum efficiency, security, and offering features like text messaging and low data rate communications.
*   **Third Generation (3G):**  Further enhanced data rates, enabling multimedia services and mobile internet access.
*   **Fourth Generation (4G):** Focused on high-speed data, improved mobile broadband experience, and supported applications like video streaming.
*   **Fifth Generation (5G):** Represents a paradigm shift, driven by specific application requirements, offering:
    *   **High speed and capacity:** To support data-intensive applications like video downloads and high-definition streaming.
    *   **Low latency:** Critical for real-time applications like remote control and autonomous driving.
    *   **IoT capacity:**  To connect a massive number of devices and sensors.
    *   **Ubiquitous connectivity:** To provide seamless network access across various environments.

## Basics of 5G New Radio (NR)

5G NR, the new radio access network for 5G, introduces significant improvements in flexibility, scalability, and efficiency. Here are some key characteristics of 5G NR:

*   **New Radio Spectrum:**
    *   5G requires a significant increase in spectrum to accommodate the growing demand for mobile data.
    *   Utilizes both existing and newly allocated spectrum bands, ranging from 2.5 GHz to 40 GHz and beyond.
    *   Higher frequency bands (mmWave) offer wider bandwidths for higher data rates but have shorter ranges.
*   **Unified Design Across Frequencies:**
    *   5G NR utilizes a wide range of frequencies, requiring a common interface to ensure seamless operation.
    *   This unified design simplifies network deployment and management across different frequency bands.
*   **Small Cells:**
    *   Network densification through the use of small cells is crucial to meet 5G's capacity and coverage requirements.
    *   Small cells are low-power base stations that can be deployed in dense urban areas to enhance network capacity.
    *   Small cell networks can coordinate to share the load and overcome physical obstructions, particularly with mmWave frequencies.


## Enabling Technologies

 Programmable virtualized infrastructure is considered a primary supporting
 technology for cutting. In principle, cutting could be accomplished without
 such infrastructure, however it would lack the considerable benefit of
dynamically installing custom architectures. To this end, the 5GPP effort has
 made significant progress in the field of virtualization and cloud
 technologies. In particular, work has been done to incorporate the plug-n-play
 implementation of clouds over physical infrastructure. Towards scheduling
 capacity, SDN has been extended to add multi-tenant support. Multi-tenancy
 support in infrastructure is key to supporting multiple possibly isolated
 sectors at the same time.

###  Multi-Tenancy Support

*   **Business Model for Slicing:** Multi-tenancy support is fundamental to the business model of providing services based on network slicing. It allows a 5G operator to offer diverse services simultaneously, catering to various customer needs and industry verticals. Without this capability, the concept of network slicing becomes impractical.
*   **Dynamic and Customizable Architectures:** Multi-tenancy support enables the dynamic installation of customized architectures on a shared physical infrastructure. This flexibility allows the network to be adapted to the specific requirements of each tenant and their respective services.

*    the following three aspects of multiclient are considered for 5G with respect to the Network Slicing design paradigm:
*   **Isolated Management and Orchestration:**  The platform can execute management and orchestration code specific to each tenant's services and functions in isolation. This ensures that each tenant's network slice operates independently without interference from others.
*   **Resource Sharing and Reuse:** Services and functions can be configured to indicate whether they have multi-tenant capabilities and can be reused between tenants. This allows for efficient resource utilization and minimizes the need for duplicate infrastructure.
*   **Network Slicing Design Paradigm:**  The sources identify three key aspects of multi-tenancy within the context of 5G network slicing:
         ![Screenshot 2024-12-03 143409](https://github.com/user-attachments/assets/6bd19500-dc03-4a88-aa46-44e1a618e4c1)

     *   **Infrastructure Sharing:** Addresses scalability concerns and provides fast resource provisioning times through cloud computing. The SDN concept is applied to enable infrastructure sharing between multiple operators.
    *   **Spectrum Sharing:** Leverages dynamic spectrum access to enhance spectrum efficiency and mitigate spectrum shortages. This involves cooperative spectrum sharing mechanisms and incentive-based approaches to optimize spectrum allocation and pricing.
    *   **RAN Sharing:** Utilizes hypervisor-based solutions to create virtual eNBs that share the physical infrastructure and resources of existing eNBs. This allows multiple operators to share RAN resources efficiently.
*   **SDN-Based Controller Paradigms:** The underlying SDN technology is extended with controller paradigms such as SDM-O (Software Defined Mobile Network Orchestrator), SDM-C (Software Defined Mobile Network Controller), and SDM-X (Software Defined Mobile Network Coordinator) to manage shared network resources and functions.
    *   **SDM-X** controls shared network resources and functions. 
    *   **SDM-C** enforces specific policies for each tenant's slice. 
    *   **SDM-O** manages and orchestrates network slices across different tenants.

### The Role of SDM-O in Multi-Tenancy

*   **Mapping Segment Templates and SLAs:** SDM-O maps segment templates representing the requirements of each slice, along with the SLAs (Service Level Agreements) of the corresponding tenants, to the available network resources.
*   **Decision-Making on Resource Sharing and Location:** SDM-O determines which network functions can be shared between slices and tenants, as well as their placement within the network. For example, SDM-O might place network functions closer to the edge for latency-sensitive slices and in the central cloud for slices with relaxed latency requirements.
*   **Enforcement of Sharing Rules and Policies:** SDM-O derives sharing rules from segment templates and implements SLAs as policies in the inter-slice broker. These policies are enforced by SDM-X and SDM-C within their respective domains.

##### Example of Multi-Tenancy
*   Multiple vMNOs (Virtual Mobile Network Operators) sharing the same infrastructure may have dedicated vEPC (virtualized Evolved Packet Core) implementations, but Gi-LAN (S) features like Firewall, Parental Control, and DPI can be shared among them.
    *   Each vMNO slice has its own SDM-C to enforce specific policies.
    *   Enforcement of policies for shared Gi-LAN (S) features is handled by SDM-X.



##  Physical Infrastructure 

### Multi-Access Edge Computing (MEC): 

*   Multi-access edge computing (MEC), formerly known as mobile edge computing, is a pivotal infrastructure enhancement in 5G.
*   It involves positioning cloud computing capabilities and an IT service environment at the edge of the mobile network, closer to users and devices. 
*   **This strategic placement offers ultra-low latency and high bandwidth, along with real-time access to localized network information and services.**
*   MEC fosters a new ecosystem where mobile network operators can open their network edges, such as the Radio Access Network (RAN), to authorized third parties like application providers. 
*   **This openness allows for rapid deployment of innovative applications and services tailored to subscribers, businesses, and specific industry verticals.** 
*   The sources provide examples of MEC use cases:

    *   Video analytics
    *   Location services
    *   Internet-of-Things (IoT)
    *   Augmented reality
    *   Optimized local content distribution 
    *   Data caching

*   By implementing services and caching content at the network edge, **MEC alleviates congestion on core networks, enabling them to efficiently serve local needs**.
![Screenshot 2024-12-03 143941](https://github.com/user-attachments/assets/7f8c6314-b6c5-4c81-951b-eec1ad305144)

### Traffic Offloading Function (TOF): Optimizing Data Flow

*   A key feature of MEC is the **Traffic Offloading Function (TOF)**. 
*   TOF enhances infrastructure to redirect traffic from a global perspective to a local one. 
*   **This localized traffic management reduces latency and improves the efficiency of data delivery.**

### Functional Splits: Flexibility in RAN Deployment

*   The close relationship between MEC and the RAN depends on how the RAN is deployed and the functional split between the Remote Unit (RU) and Central Unit (CU), also referred to as the edge cloud.
*   **Functional splits influence the fronthaul network and affect the data rate, latency, and synchronization requirements of the Next Generation Fronthaul Interface (NGFI).** 
*   **They also determine the information accessible by MEC.**
*   The sources describe a generic RAN signal processing chain with three functional divisions:

    *   **Division A:** Places antenna processing in the RU, offering scalability for 5G technologies like Massive MIMO in existing CPRI-based C-RAN architectures.
    *   **Division B:**  Involves transporting frequency domain symbols, allowing for statistical multiplexing gains and varying data rates based on cell load, unlike CPRI. 
    *   **Division C:**  Represents a higher-layer split, similar to PDCP, and can support backhaul-type interfaces.



## Cell Clustering

*   **Cell clustering** is a technique used in 5G to improve mobility and capacity, particularly in deployments utilizing millimeter wave (mmWave) frequencies.
*   In cell clustering, a group of Access Points (APs) work together to serve users, with one AP designated as the group leader or Cluster Head (CH).
*   **The CH manages the control plane and the interface to the Core Network (CN), and it can configure which APs are part of the cluster.**

### RRC-Driven and RRC-Free Mobility: Two Levels of Handover

*   5G supports two levels of mobility: **RRC-driven and RRC-free**.
*   **RRC-driven mobility** operates similarly to LTE, where the User Equipment (UE) reports measurements from neighboring cells. If a neighboring cell offers better signal quality, the network reconfigures the UE's RRC connection to handover to that cell.
*   **RRC-free mobility** handles measurements at the PHY or MAC layer, using signals like CSI-RS (Channel State Information Reference Signals) or CQI (Channel Quality Indicators). The UE can switch to a different beam from a different AP without involving the RRC layer.

### Benefits of Cell Clustering:

*   **Improved Capacity:** Cell clustering enables load balancing among APs in the cluster, improving overall network capacity.
*   **Seamless Mobility:**  Users can seamlessly transition between APs within the cluster without experiencing service interruptions.
*   **Enhanced Coverage:**  By coordinating APs, cell clustering can provide better coverage, especially in challenging environments where mmWave signals have limited range.

### Integration with Lower Frequencies: Ensuring Reliability

*   In scenarios where mmWave coverage is unreliable due to signal blockage, the network can leverage the wider coverage of lower frequency RATs, like LTE-A, to ensure connectivity within the cluster. 
*   **The lower frequency RAT can transmit traffic and control signals from the CH to the UE, supporting mobility within the cluster.**

### Transparency for User Equipment:

*   **The UE remains unaware of the cell clustering configuration, including the CH and the APs within the cluster.** 
*   The network dynamically manages the UE's connection to the most suitable AP based on factors like signal quality, transport capacity between nodes, and processing/storage capabilities of the target node.

### Latency Considerations:

*   While cell clustering enhances mobility and capacity, the use of techniques like wireless backhaul for inter-node communication within the cluster can introduce additional latency. 
*   **These latency implications need careful consideration, especially for latency-sensitive applications.**

