---
layout: page
title: CONNECT
description: Assessing Trustworthiness of data and actors in Cooperative, connected and automated mobility (CCAM)
img: assets/img/CONNECT-Logo-4C-q.png
importance: 4
category: work
related_publications: icics25, ifip23, 5gaa2024_trust_cav
---

- **Project Name:** CONNECT – Continuous and Efficient Cooperative Trust Management for Resilient CCAM  
- **Duration:** September 2022 – August 2025
- **Links:** [Project website](https://horizon-connect.eu/) • [CORDIS entry](https://cordis.europa.eu/project/id/101069688) • [CCAM Association project page](https://www.ccam.eu/projects/connect/)  
- **Funding:** Horizon Europe (Grant 101069688), €5.66M  
- **Programme & call:** Funded under **Horizon Europe — CCAM (Cluster 5)**, topic group **HORIZON-CL5-2021-D6-01 (Cyber-secure & resilient CCAM)**. 
- **Consortium:** 16 partners across 8 countries (Coordinator: TECHNIKON; core partners include UBITECH, University of Ulm, Huawei Technologies Duesseldorf GmbH)  
- **My Role:** Project Proposal Author & Internal Project Manager for Huawei  

---

CONNECT uses a mathematical model that builds a comprehensive Trust Assessment Framework for CCAM and C-ITS on top of subjective logic and trust network analysis. The biggest achievement of the project is that it addresses the convergence of security and safety in CCAM by assessing dynamic trust relationships and defining a trust model and trust reasoning framework based on which involved entities can establish trust for cooperatively executing safety-critical functions. 

### Dynamic Trust Assessment of V2X messages and actors is now possible

The cornerstone of the CONNECT project is its Trust Assessment Framework (TAF), which enables continuous assessment and dynamic trust establishment, addressing both data trustworthiness and the trust level of entities within the CCAM ecosystem.

* Dynamic Trust Models: CONNECT’s Trust Model Manager (TMM) builds dynamic trust models that capture and maintain multiple trust relationships among different data sources and entities. These models adapt to real-time changes, ensuring that trust assessments remain relevant throughout system operation.
* Evidence-Based Trust Evaluation: The Trust Level Evaluation Engine (TLEE) leverages observable evidence and referral-based relationships to dynamically evaluate the trustworthiness of data sources and observations. This probabilistic approach ensures robust and accurate trust assessments, even under changing network and operational conditions.

More information can be found in our papers {% cite icics25 %}, {% cite ifip23 %}, and {% cite 5gaa2024_trust_cav %}, as well as [CONNECT Deliverables](https://horizon-connect.eu/public-deliverables/).

### Runtime Monitoring and Trust-Based Security Claims

We need trustworthiness not only of the communicating parties, but also trustworthiness of the environment and the provenance of the services running. The CONNECT project integrates trusted computing capabilities directly into CCAM entities, creating a “network of trust” through continuous attestation and verification mechanisms.

* Importance of Runtime and Composable Attestation: Runtime attestation dynamically verifies the integrity of MEC nodes and applications during operation, ensuring they remain secure over time. However, it is still open how to elevate Runtime Attestation from a single device to a trustworthy service graph chain (composition of devices), featuring collaborative function service execution.
* Roots of Trust for Vehicles: A trust anchor (e.g., TPM or TEE) that enables tamper-proof verification of a system’s integrity and safeguards critical assets like cryptographic keys. RoT provides a secure foundation for runtime attestation, ensuring trustworthiness even across multi-stakeholder MEC domains. Interoperability and agility between RoT providers are already a concern in standardization activities like IETF (e.g. TDISP. RATS) 

### The ATL and RTL Methodology

The output of the trust assessment is an opinion, which is calculated dynamically, since evidence is constantly changing. 
We call this the Actual Trust Level (ATL) compared to the Required Trust Level (RTL), which quantifies the level of trustworthiness that is desired or indeed required in order to proceed with the act of trust. 

<img src="/assets/img/ATL_and_RTL_methodology.png" width="350">

* The ATL reflects the result of an evaluation of a specific proposition for a specific scope. It quantifies the extent to which a certain node or data can be considered trustworthy based on the available evidence.
* The RTL reflects the amount of trustworthiness of a node or data that an application considers required in order to characterize this object as trusted and rely on its output during its execution. 

### Trustworthiness on the MEC 

One of the biggest security challenges of Multi-Access Edge Computing (MEC) is the establishment of mutual trust between involved actors. Mutual trust establishment becomes much more complex considering multiple trust domains that are involved in order to establish a trustful collaborative and data sharing environment. More specifically, mutual trust between MEC Applications and MEC platforms is hard because 
* in principle the edge application from MNO A should be considered as if it would be running on an “hostile” environment (MNO B) and also vice-versa, i.e. 
* a platform operated by MNO B is hosting “unknown” applications which may endanger the system;

<img src="/assets/img/CONNECT_MEC_Task_Offloading.png" width="550">

CONNECT investigates a representative automotive use case to exemplify its trust framework on the MEC: AI-driven slow-moving traffic detection (SMTD). In this scenario, vehicles capture video data and offload computationally intensive tasks, such as real-time video analytics, to nearby MEC nodes. The MEC nodes process the data using machine learning models and return actionable insights, like hazard detection, to the vehicles. This task requires dynamic collaboration between vehicles, MEC nodes, and infrastructure managed by multiple stakeholders.

Challenges such as verifying the trustworthiness of MEC nodes before offloading and ensuring the integrity of processed data underscore the importance of secure, real-time trust assessment mechanisms in dynamic, federated environments. CONNECT’s trust framework resolved these trust challenges by operating at both the vehicle and MEC nodes, leveraging evidence-based trust claims to evaluate the trustworthiness of entities before offloading tasks. This approach dynamically adapts to evolving trust contexts, ensuring seamless and secure interactions. Key security measures include the use of hardware-rooted secure elements, such as Trusted Execution Environments (TEEs), to protect applications and data from unauthorized access or modification, and Chip-to-Cloud assurances, where video frames are securely transmitted over TLS-encrypted channels. 

