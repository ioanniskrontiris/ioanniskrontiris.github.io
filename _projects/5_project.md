---
layout: page
title: V2X-DAA
description: Direct Anonymous Attestation (DAA) as an alternative trust model for V2X security
img: assets/img/v2xdaalogo3.png
importance: 5
category: work
related_publications:
  - vnc2023
  - wisec21
  - krontiris2019ares
---


- **Project Name:** V2X-DAA — DAA-enabled Security for Cooperative, Connected & Automated Mobility (CCAM)  
- **Duration:** 2022–2023 *(internal bilateral R&D)*  
- **Funding:** Bilateral industry collaboration (with UBITECH)   
- **Links:** [UBITECH announcement](https://ubitech.eu/ubitech-has-been-awarded-a-research-grant-on-v2x-communication-security-from-a-multinational-technology-company/)
- **My Role:** Project Initiator / Technical lead for architecture & evaluation

---

### TL;DR 

- **Problem:** PKI-based V2X scales poorly and strains privacy: bulk pseudonym provisioning, CRLs, and backend dependency. {% cite krontiris2019ares %}
- **Idea:** Move trust to the **vehicle** using **Direct Anonymous Attestation (DAA)** + TPM. Vehicles **self-issue** unlinkable pseudonyms; revocation is **device-enforced** (no CRLs). {% cite wisec21 %}
- **Evidence:** We built both **PKI** and **DAA** pipelines on an ETSI-aligned V2X stack and measured them head-to-head. Under realistic channel loads, end-to-end latency **converges**, while DAA delivers **cleaner revocation** and **no refill logistics**. {% cite vnc2023 %}

---

### Why PKI struggles at scale
Modern SCMS/CCMS deployments rely on central authorities to mint and refresh thousands of short-lived pseudonyms per vehicle and to distribute revocation state. This is operationally heavy, connectivity-sensitive, and creates privacy pressure even with separation-of-duties. {% cite krontiris2019ares %}

### Our approach: vehicle-centric trust with DAA
We designed a V2X security architecture that anchors trust **in the vehicle**:

- **On-board pseudonym self-issuance.** A TPM creates and protects pseudonym keys; messages are signed with **anonymous, unlinkable** DAA signatures. {% cite wisec21 %}
- **Hardware-enforced policies.** A **revocation index** inside the TPM binds each pseudonym to two states:
  - **Soft revocation:** disable a specific pseudonym.
  - **Hard revocation:** disable **all** pseudonyms of a vehicle in one shot. {% cite wisec21 %}
- **Privacy-preserving control plane.** Vehicles register only cryptographic **revocation hashes** (“Proof of Registration”); **no identity resolution** is needed to revoke. {% cite wisec21 %}

<p align="center">
  <img src="/assets/img/DAA-daanym.png" width="400">
</p>

### What we actually built
- A full **DAA pipeline** (JOIN → self-issuance → sign/verify → soft/hard revocation) on V2X-grade hardware, and a **PKI baseline** (OpenSSL/ECDSA), both integrated with an ETSI-aligned CAM/DENM stack for like-for-like measurement. {% cite vnc2023 %}
- A testbed exercising **crypto cost**, **end-to-end latency** under increasing message rates, **pseudonym lifecycle**, and **revocation workflows**. {% cite vnc2023 %}

### Key results (what changed)
- **Revocation becomes practical.** One signed broadcast from the RA triggers **local** (TPM-enforced) revocation, either a single pseudonym or the entire set. **No CRLs, no identity resolution.** {% cite wisec21 %}{% cite vnc2023 %}
- **Self-issuance removes refill logistics.** Pseudonyms are generated on-board under TPM policy; back-end load and connectivity assumptions drop dramatically. {% cite vnc2023 %}
- **Latency remains viable.** Although DAA signatures are heavier than ECDSA in isolation, under realistic channel loads the **network/stack dominates**, and **DAA ≈ PKI** in end-to-end latency, so DAA is **practically deployable** for safety messaging. {% cite vnc2023 %}

### Why this matters
- **Scalability:** Eliminates bulk certificate manufacturing, distribution, and storage at fleet scale. {% cite krontiris2019ares %}
- **Privacy by design:** Unlinkable, on-device credentials minimize tracking risk while preserving verifiability. {% cite wisec21 %}
- **Operational security:** A **device kill-switch** for misbehavior (hard revoke) with immediate effect, without revealing or resolving long-term identity. {% cite wisec21 %}

