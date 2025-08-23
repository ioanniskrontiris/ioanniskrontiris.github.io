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

## Facts

- Awarded under an **open call of NGI eSSIF-Lab** as a sub-grant project.  [Project description at eSSIF-Lab](https://essif-lab.eu/hardware-roots-of-trust-as-an-enabler-of-trustworthiness-in-digital-transactions-by-ubitech/)
- Objective: **increase trust in digital transactions** by integrating a **hardware-based root of trust** into the Self-Sovereign Identity (SSI) ecosystem.  
- Designed a **wallet-side hardware component** for secure key management and for binding **Verifiable Credentials (VCs)** to the wallet.  
- Supports **higher assurance levels** in SSI systems, ensuring credential provenance and integrity.  
- Developed as a **wallet-agnostic solution**, interoperable across different SSI frameworks (e.g. W3C, Hyperledger Indy).  
- Demo Implementation: The project produced a **demo implementation** showcasing the integration of hardware roots of trust into Digital Identity wallets.  
[View the DOOR demo artifact on GitHub](https://github.com/Door-project/videos/releases/tag/Demo)
---

## Description of the innovation
  
In the case of Europe, the eIDAS regulation clearly defines the requirements for authentication factors to achieve a certain level of assurance (LoA). Bare proof-of-possession of a private key does not achieve even the lowest level of assurance in eIDAS, since it involves only a single authentication factor. The SSI eIDAS Bridge, which was developed within the H2020 NGI ESSIF Lab project, makes eIDAS available as a trust framework for the SSI ecosystem. The aim of the SSI eIDAS Bridge is precisely to get, at least, eIDAS LoA Substantial. That means working in the DID control keys, possible aligned with the eIDA eSign/eSeal regulation. So, it is an approach to make eIDAS available as a trust framework for the SSI ecosystem.

However, it is limited to eIDAS applications and therefore it focuses on the trust domain of national legal electronic identification and trust services in the European context. As an alternative, Kubach et al.~\cite{train} proposed a trust management infrastructure called TRAIN, which leverages the global Domain Name System (DNS) and is based on the project LIGHTest~\cite{LIGHTest}. 

<img src="/assets/img/DOOR_essif.png" width="700">

A core challenge in SSI is the verification of the integrity and origin of the presented Verifiable Credentials (VCs): How can someone be sure that the presented VCs (for a specific DID) really belong to the claimed entity?  On a technical level, this translates to users having control of their own VCs and DIDs through their Wallets which can ensure that credentials and (private) keys can only become available to this user or another actor that acts on behalf of this principal. However, since it is only the user (as the Identity Owner) that knows the (private) key associated with a DID, the level of control and assurance over a DID (and a VC) relies solely on possessing a software-based key, creating trustworthiness issues: How can a Verifier be sure of the correctness of the User/Holder that presents a VC that the respective key has not been compromised?

DOOR project proposes a comprehensive solution for establishing trust across multiple stakeholders in the SSI ecosystem by leveraging decentralized Roots-of-Trust such as secure elements including Trusted Platform Modules (TPMs), Trusted Execution Environments (TEEs), DICE, etc. It is based on the use of advanced crypto primitives, namely Direct Anonymous Attestation (DAA), generating hw-based keys to be binded to a Holder’s VC (Wallet) that can provide verifiable evidence and assurances about the presented VC's origin and integrity.

DOOR enables the use of crypto operations of the DAA (ECC, Blind Signatures, Zero Knowledge Proofs) towards providing additional trust assurances on the use of VCs: As can be seen in Figure~\ref{fig:daabridge}, issued VCs are binded to a specific Wallet and can only be used if our DAA-Bridge Extension can verify the correctness of the Wallet which, in turn, translates to the respective (private) key of this VC not been compromised. A DAA scheme enables a signer to prove the possession of the issued credential to a verifier by providing a signature, which allows the verifier to authenticate the signer without revealing the credential and signer’s identity.


DAA's ECC keys, attestation services and key hierarchy (supported by the underlying secure element and its Endorsement Key that acts as the ID of the Wallet) can support the provision of verifiable evidence on the correct configuration state and/or execution of the Wallet. Essentially, the DAA-Bridge Extension will not allow the use of a key for signing a Verifiable Credential or a Verifiable Presentation unless no compromise has been detected (Device Correct State). Only then a signature can be produced based on ECC built on pairing-friendly elliptic curves. Different from a Public-Key Infrastructure (PKI) which is based on a trusted centralized Certificate Authority (CA) to bind public key pairs to identities, DAA certifies identities locally on the Holder's Device.