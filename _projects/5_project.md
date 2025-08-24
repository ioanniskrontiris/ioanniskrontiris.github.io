---
layout: page
title: V2X-DAA
description: Direct Anonymous Attestation (DAA) as an alternative trust model for V2X security
img: assets/img/v2xdaalogo3.png
importance: 6
category: work
related_publications:
  - 10136316
---


**Project Name:** V2X-DAA — DAA-enabled Security for Cooperative, Connected & Automated Mobility (CCAM)  
**Duration:** 2022–2023 *(internal bilateral R&D)*  
**Funding:** Bilateral industry collaboration (Huawei Technologies Europe – UBITECH)  
**Consortium:** Huawei Technologies Düsseldorf GmbH (European Research Center, Munich), UBITECH (Digital Security & Trusted Computing Group, Athens)  
**My Role:** Co-PI / Technical lead for architecture & evaluation

---

## About

- **Goal.** Investigate Direct Anonymous Attestation (DAA) as an alternative (or complement) to PKI for V2X, focusing on **scalability, privacy, revocation, and pseudonym lifecycle**.  
- **What we built.** An end-to-end **DAA-based credentialing flow** on V2X-grade hardware (TPM-backed keys) and a **PKI baseline**, both integrated with an ETSI-aligned V2X communication stack (CAM/DENM) to enable like-for-like measurements.  
- **How we evaluated.** Methodological comparison on a realistic testbed (multiple simulated vehicles and message rates): crypto cost (sign/verify), **E2E network latency under load**, **pseudonym issuance/reloading**, and **revocation**.  
- **Key findings.**
  - DAA enables **local self-issuance of pseudonyms** under hardware key-use policies, eliminating periodic “refill” trips to a PCA.  
  - **Revocation in DAA** can invalidate *all* of a vehicle’s pseudonyms in one action (no CRLs or per-pseudonym resolution), offering operational advantages at scale.  
  - At high channel loads, **network/stack bottlenecks dominate**; DAA’s heavier crypto becomes less decisive for E2E latency—supporting a **hybrid/combined** approach rather than “PKI vs DAA” as a binary choice.  
  - Full details and results are published in our IEEE VNC paper {% cite 10136316 %}.  
- **Outcome.** The project delivered the **first implementation and experimental comparison** of DAA vs. PKI for V2X, informing standards discussions and future **hybrid trust models**.

**Links:** [IEEE VNC 2023 paper](https://ieeexplore.ieee.org/document/10136316) {% cite 10136316 %} • [UBITECH project announcement](https://ubitech.eu/ubitech-has-been-awarded-a-research-grant-on-v2x-communication-security-from-a-multinational-technology-company/)

---