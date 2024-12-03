## Enabling Technologies

The sources highlight multi-tenancy support as a key enabling technology for 5G network slicing. This capability allows a single physical infrastructure to be divided into multiple logically isolated network slices, each tailored to specific service requirements and managed by different tenants.

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

SDM-O plays a crucial role in realizing multi-tenancy in 5G networks:

*   **Mapping Segment Templates and SLAs:** SDM-O maps segment templates representing the requirements of each slice, along with the SLAs (Service Level Agreements) of the corresponding tenants, to the available network resources.
*   **Decision-Making on Resource Sharing and Location:** SDM-O determines which network functions can be shared between slices and tenants, as well as their placement within the network. For example, SDM-O might place network functions closer to the edge for latency-sensitive slices and in the central cloud for slices with relaxed latency requirements.
*   **Enforcement of Sharing Rules and Policies:** SDM-O derives sharing rules from segment templates and implements SLAs as policies in the inter-slice broker. These policies are enforced by SDM-X and SDM-C within their respective domains.

##### Example of Multi-Tenancy
*   Multiple vMNOs (Virtual Mobile Network Operators) sharing the same infrastructure may have dedicated vEPC (virtualized Evolved Packet Core) implementations, but Gi-LAN (S) features like Firewall, Parental Control, and DPI can be shared among them.
    *   Each vMNO slice has its own SDM-C to enforce specific policies.
    *   Enforcement of policies for shared Gi-LAN (S) features is handled by SDM-X.



##  Physical Infrastructure 




### Multi-Access Edge Computing (MEC): Bringing the Cloud Closer

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

