---
layout: page
title: CONNECT
description: Assessing Trustworthiness of data and actors in CCAM
img: assets/img/CONNECT-Logo-4C-q.png
importance: 3
category: work
---


### Dynamic Trust Assessment of V2X messages and actors is now possible

The cornerstone of the CONNECT project is its Trust Assessment Framework (TAF), which enables continuous assessment and dynamic trust establishment, addressing both data trustworthiness and the trust level of entities within the CCAM ecosystem.
* Dynamic Trust Models: CONNECT’s Trust Model Manager (TMM) builds dynamic trust models that capture and maintain multiple trust relationships among different data sources and entities. These models adapt to real-time changes, ensuring that trust assessments remain relevant throughout system operation.
* Evidence-Based Trust Evaluation: The Trust Level Evaluation Engine (TLEE) leverages observable evidence and referral-based relationships to dynamically evaluate the trustworthiness of data sources and observations. This probabilistic approach ensures robust and accurate trust assessments, even under changing network and operational conditions.

### Runtime Monitoring and Trust-Based Security Claims

The CONNECT project integrates trusted computing capabilities directly into CCAM entities, creating a “network of trust” through continuous attestation and verification mechanisms.
* Roots of Trust for Vehicles: By embedding trusted computing bases within vehicle electronic control units (ECUs) and sensors, CONNECT enables runtime attestation of device integrity, configuration, and software execution. This capability ensures real-time verification of each component’s security status.
* Secure Evidence Sharing: Security claims generated during trust assessments are shared with other entities in a privacy-preserving manner, maintaining data integrity while mitigating risks associated with information exposure. Advanced cryptographic constructs, such as anonymous threshold signatures, enable zero-knowledge proofs of trust, preserving user privacy without compromising security.

### Applying Digital Twin Technology for Enhanced Trust and Efficiency

One of the biggest security challenges that Multi-Access Edge Computing (MEC) is facing today is the establishment of mutual trust between involved actors. Mutual trust establishment becomes much more complex considering multiple trust domains that are involved in order to establish a trustful collaborative and data sharing environment. More specifically, mutual trust between MEC Applications and MEC platforms is hard because 
* in principle the edge application from MNO A should be considered as if it would be running on an “hostile” environment (MNO B) and also vice-versa, i.e. 
* a platform operated by MNO B is hosting “unknown” applications which may endanger the system;

We need trustworthiness not only of the communicating parties, but also trustworthiness of the environment and the provenance of the services running. According to CONNECT, two kinds of technologies are nececcary to address the latter: 

* Importance of Runtime and Composable Attestation: Runtime attestation dynamically verifies the integrity of MEC nodes and applications during operation, ensuring they remain secure over time. However, it is still open how to elevate Runtime Attestation from a single device to a trustworthy service graph chain (composition of devices), featuring collaborative function service execution.
* Hardware Root of Trust (RoT): A hardware-based trust anchor (e.g., TPM or TEE) that enables tamper-proof verification of a system’s integrity and safeguards critical assets like cryptographic keys. RoT provides a secure foundation for runtime attestation, ensuring trustworthiness even across multi-stakeholder MEC domains. Interoperability and agility between RoT providers are already a concern in standardization activities like IETF (e.g. TDISP. RATS) 

<img src="/assets/img/CONNECT_MEC_Task_Offloading.png" width="700">

CONNECT investigates a representative automotive use case to exemplify its trust framework on the MEC: AI-driven slow-moving traffic detection (SMTD). In this scenario, vehicles capture video data and offload computationally intensive tasks, such as real-time video analytics, to nearby MEC nodes. The MEC nodes process the data using machine learning models and return actionable insights, like hazard detection, to the vehicles. This task requires dynamic collaboration between vehicles, MEC nodes, and infrastructure managed by multiple stakeholders. 

Challenges such as verifying the trustworthiness of MEC nodes before offloading and ensuring the integrity of processed data underscore the importance of secure, real-time trust assessment mechanisms in dynamic, federated environments.

CONNECT’s trust framework resolved these trust challenges by operating at both the vehicle and MEC nodes, leveraging evidence-based trust claims to evaluate the trustworthiness of entities before offloading tasks. This approach dynamically adapts to evolving trust contexts, ensuring seamless and secure interactions. Key security measures include the use of hardware-rooted secure elements, such as Trusted Execution Environments (TEEs), to protect applications and data from unauthorized access or modification, and Chip-to-Cloud assurances, where video frames are securely transmitted over TLS-encrypted channels. 

