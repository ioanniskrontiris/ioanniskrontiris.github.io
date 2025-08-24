---
layout: page
title: ESSIF-Lab Project - DOOR 
description: Hardware Roots of Trust as an Enabler of Trustworthiness in Digital Transactions
img: assets/img/DOOR_logo.png
importance: 2
category: work
giscus_comments: false
---
 
**Project Name:** DOOR – Hardware Roots of Trust as an Enabler of Trustworthiness in Digital Transactions
**Duration:** October 2021 – June 2022  
**Funding:** EU H2020, NGI eSSIF-Lab (Cascading Grant)  
**Consortium:** UBITECH (Greece), Huawei Research Munich (Germany), Verifiable Credentials Ltd (UK)  
**Role:** Proposal Author & Project Partner   

---

## About

- Awarded under an **open call of NGI eSSIF-Lab** as a sub-grant project.  [Project description at eSSIF-Lab](https://essif-lab.eu/hardware-roots-of-trust-as-an-enabler-of-trustworthiness-in-digital-transactions-by-ubitech/)
- Objective: **increase trust in digital transactions** by integrating a **hardware-based root of trust** into the Self-Sovereign Identity (SSI) ecosystem.  
- Designed a **wallet-side hardware component** for secure key management and for binding **Verifiable Credentials (VCs)** to the wallet.  
- Supports **LoA High** for digital identity wallets, ensuring credential provenance and integrity.  
- Developed as a **wallet-agnostic solution**, interoperable across different SSI frameworks (e.g. W3C, Hyperledger Indy).  
- Demo Implementation: The project produced a **demo implementation** showcasing the integration of hardware roots of trust into Digital Identity wallets.  [View the DOOR demo artifact on GitHub](https://github.com/Door-project/videos/releases/tag/Demo)

---

## Description of the innovation
  
In Europe, the **eIDAS regulation** defines authentication factors required to achieve specific Levels of Assurance (LoA). A plain proof-of-possession of a private key along constitutes only a single factor—insufficient even for the lowest eIDAS LoA.

The **[SSI eIDAS Bridge](https://essif-lab.eu)**, developed under the H2020 NGI ESSIF-Lab project, brings eIDAS as a trust framework into the Self-Sovereign Identity (SSI) ecosystem. It aims to reach at least **eIDAS LoA Substantial** by incorporating control mechanisms over DIDs (aligned with eIDAS eSign/eSeal standards) into DID control keys. This approach strengthens trust by extending legal electronic identification into the SSI domain.

That said, the SSI eIDAS Bridge remains limited to eIDAS-specific applications and the broader European trust domain. As an alternative, [TRAIN](https://ngi.eu/funded_solution/essi_ioc_38/) proposed a lightweight trust management infrastructure, which leverages the global Domain Name System (DNS). TRAIN enables **decentralized, policy-driven trust decisions** within SSI ecosystems.

A core challenge in SSI is verifying the **integrity and origin** of Verifiable Credentials (VCs): how can a verifier be certain that the credentials truly belong to the claimed entity? Technically, users (as Identity Owners) control their VCs and DIDs through their wallets—but since the private key resides solely with them, this implies **sole reliance on software-based key control**. That raises trustworthiness concerns: how can a verifier know that a wallet’s key hasn't been compromised?

<img src="/assets/img/DOOR_essif.png" width="700">

The **DOOR project** (Hardware Roots of Trust as an Enabler of Trustworthiness in Digital Transactions) offers a robust solution. It strengthens trust in the SSI ecosystem by incorporating **hardware-based Roots of Trust**, such as TPMs, TEEs, DICE, and similar secure elements. At its core, DOOR uses advanced cryptographic primitives (**Direct Anonymous Attestation (DAA)**) to generate hardware-based keys that are **tightly bound to a wallet’s VC**. This binding provides verifiable evidence of a credential's origin and integrity.

Through DOOR, crypto operations intrinsic to DAA—like ECC key generation, blind signatures, and zero-knowledge proofs, enable additional trust assurances: issued VCs are bound to specific wallets, and only usable if the **DAA-Bridge Extension** confirms wallet correctness (i.e., that the private key hasn't been compromised). A DAA scheme lets a signer prove possession of a credential without revealing identity, enhancing both privacy and trust.

DAA’s built-in key hierarchy, supported by the secure element’s **Endorsement Key**, allows verifiers to assess the wallet’s configuration and execution state. Essentially, the DAA-Bridge Extension prohibits use of a VC or Verifiable Presentation unless the device is in a **correct, uncompromised state**. Only then is a valid, pairing-friendly elliptic curve (ECC) signature produced—distinct from traditional PKI where a centralized CA binds identities to keys.



### References

- SSI eIDAS Bridge — [NGI eSSIF-Lab Project Description](https://essif-lab.eu)  
- TRAIN: A lightweight trust management infrastructure for SSI — Kubach & Roßnagel (2021)  [oai_citation:5‡oid2021.compute.dtu.dk](https://oid2021.compute.dtu.dk/Kubach%20Rossnagel%20OID%202021%20Trust%20Infrastructure%20for%20SSI.pdf?utm_source=chatgpt.com) [oai_citation:6‡ioanniskrontiris.github.io](https://ioanniskrontiris.github.io/projects/2_project/?utm_source=chatgpt.com)  
- TRAIN Infrastructure Overview — Fraunhofer IAO  [oai_citation:7‡hci.iao.fraunhofer.de](https://www.hci.iao.fraunhofer.de/de/identity-management/identity-und-accessmanagement/TRAIN_EN.html?utm_source=chatgpt.com)  
- Verifying Credentials with TRAIN — NGI blog  [oai_citation:8‡Next Generation Internet](https://ngi.eu/blog/2022/07/28/verifying-identity-management-credentials-with-train/?utm_source=chatgpt.com)