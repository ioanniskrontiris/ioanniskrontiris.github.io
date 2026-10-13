---
layout: page
title: SafeTravellers
description: Trustworthy digital identity and explainable AI decision support at Europe's borders
img: assets/img/SafeTravellers_logo.png
importance: 1.5
category: work
related_publications: Prive2024_10538525, icics25, ouattara2026patas
---

- **Project Name:** SafeTravellers – Secure and Frictionless Identity for EU and Third Country National Citizens
- **Duration:** January 2024 – December 2026
- **Links:** [Project website](https://safetravellers-project.eu/) • [CORDIS entry](https://cordis.europa.eu/project/id/101121269)
- **Funding:** Horizon Europe Innovation Action (Grant 101121269), €7.48M total, €6.08M EU contribution
- **Programme & call:** **Horizon Europe — Cluster 3 (Civil Security for Society)**, topic **HORIZON-CL3-2022-BM-01-02** (Enhanced security of, and combating the frauds on, identity management and identity and travel documents)
- **Consortium:** 23 partners (Coordinator: INOV; partners include IDEMIA, Vision-Box, iProov, AIT, CEA, VUB, UBITECH, and ministries and law-enforcement authorities of Finland, Portugal and Slovakia)
- **My Role:** Senior Researcher in the UBITECH team (January 2025 – February 2026)

---

Identity fraud at borders is getting more sophisticated. Faces in passports are morphed from two people. Look-alikes travel on someone else's document. Makeup is used to defeat face recognition. SafeTravellers asks how to stop these attacks without making travel slower.

The project's answer has two parts. Travellers carry a verifiable digital version of their travel document in an identity wallet. Border authorities get a set of AI-based attack detectors whose outputs are fused into one explainable risk assessment. The goal is a border crossing where honest travellers barely stop, and officers spend their attention where the evidence says it is needed.

UBITECH led the work package on improved identification of citizens. This covered the identity wallet, the verifiable data registry, multi-biometric fusion and the explainable-AI recommendation engine. I worked with the UBITECH team, led by Thanassis Giannetsos, on the architecture and technical design of these components (deliverable D3.2), and on the review of the attack-detection work.

### Two kinds of trust at the border

A border check has to answer two different questions.

1. **Can I trust this traveller's identity data?** This is a question of cryptography, hardware and governance.
2. **Can I trust the AI's judgement about this traveller?** This is a question of evidence fusion, explanation and human oversight.

SafeTravellers treats both as first-class design problems. Neither is allowed to rely on assumed trust. Every actor and every piece of evidence is verified, in the spirit of zero trust.

### The identity layer: a wallet you can trust, and a registry that says whom to trust

<img src="/assets/img/SafeTravellers_identity_architecture.png" width="750">

The journey has three steps. The wallet reads the passport chip and receives a Digital Travel Credential. Before the trip, the traveller enrols and receives a travel token. At the border, the traveller taps the wallet at the eGate and walks through.

The wallet follows eIDAS 2.0 and the EUDI Architecture and Reference Framework. Three properties make it trustworthy:

* **Keys locked in hardware.** Every credential is bound to keys inside the phone's secure hardware. A copied credential is useless. This continues the line of work we started in [PRIVÉ](/projects/1_project/) {% cite Prive2024_10538525 %}.
* **Show only what's needed.** The wallet discloses only the attributes a policy asks for. Single-use credentials, each with its own hardware key, stop colluding verifiers from linking presentations. The final version uses ISO mDL, which border eGates already support, also offline.
* **Proof the wallet is untampered.** Attestation evidence travels with each presentation. Runtime checks at random times also protect the attestation itself against time-of-check/time-of-use attacks.

The **trust registry** is the other half. It is built on a blockchain and curated by governmental bodies. It answers three questions: who may issue, who may verify, and what a traveller must show for a given trip. Travel rules live there as machine-readable policies, so a new rule changes one policy and not every system. A compliance token records the checks passed at enrolment; it is burned after the crossing, so no trace of the trip stays on chain.

The **European Multi-Biometric Data Space** completes the picture. Each Member State keeps the biometric data of its own nationals. Cross-border checks run without moving raw biometric data.

### The AI layer: one auditable score, explained

<img src="/assets/img/SafeTravellers_decision_pipeline.png" width="750">

Five detectors examine the traveller: morphing, look-alike, makeup, face match and biometric match. Each gives its own score. The officer needs one assessment, and needs to know why.

* **One auditable score.** The detector outputs are fused by a deterministic, expert-calibrated engine. The same evidence always gives the same result. Every score splits exactly into the contribution of each detector.
* **A shadow model explains it; it does not decide.** A machine-learning model is trained to mimic the score. SHAP on this shadow model shows which signals stand out for this traveller. It is always checked against the real score. If the two drift apart, an alert is raised and the exact contributions are shown instead.
* **Why not let a classifier decide?** Real attack data at borders are scarce. Classifiers trained on synthetic attacks looked good in tests but were brittle on real pilot inputs. Learning to mimic a known function avoids that trap.
* **The officer decides.** The output is a graded risk and the most likely attack, not a yes/no. At enrolment it drives the automated token issuance, and flagged cases go to a manual check. At the border it only supports the officer.

### What I take from SafeTravellers

The project sits in two areas the EU AI Act lists as high-risk: biometrics, and migration, asylum and border control management. It is a good test case for what trustworthy AI means in practice. Four lessons stay with me.

* **Missing evidence is not evidence of safety.** In a multi-partner system, some detector outputs arrive late, fail or are absent. A single scalar score has to fill these gaps with default values. Subjective Logic keeps belief, disbelief and uncertainty apart, so "we do not know" remains visible to the decision maker. This is the core idea of the trust assessment framework in [CONNECT](/projects/3_project/) and of our work on trust propagation in neural networks {% cite ouattara2026patas %}.
* **Explain the decision you made, not a model of it.** Post-hoc explanations are only as good as their fidelity to the system that decides. Fidelity should be measured, monitored and reported. It is evidence about the AI system itself.
* **Regulation is a design input.** Human oversight, record keeping and transparency to deployers (AI Act Articles 12–14) became concrete design decisions here: deterministic reproducibility, decision logs, and officer-facing explanations. This is the bridge I work on in CEN/CENELEC JTC 21.
* **The same trust stack applies to AI agents.** A border verifier asks: who issued this credential, is the wallet intact at runtime, and which policy applies here? A service facing an AI agent acting for a person must ask the same questions. Verifiable credentials, runtime attestation and policy registries carry over directly {% cite icics25 %}.

### Pilots

SafeTravellers is validated in four pilot scenarios defined with border authorities:

* attacks on biometrics at airports;
* fraudulent identity and travel documents at sea and land borders;
* identification of drivers and passengers in vehicles at land borders;
* identification on railway premises during cross-border train services.

The final pilot demonstration, an airport scenario, took place in September 2026 at the Academy of the Police Force in Bratislava, hosted by the Slovak Bureau of Border and Foreign Police.
