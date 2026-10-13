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

### The identity layer: wallet, attestation and registry

The journey has three phases. A government issues the travel document. Before the trip, the traveller enrols: the Digital Travel Credential (DTC) is extracted, checked against biometrics, and turned into a verifiable credential plus a travelling token. At the border, the wallet presents only what the border policy requires.

* **EUDI-aligned identity wallet.** The wallet follows the eIDAS 2.0 implementing acts and the EUDI Architecture and Reference Framework. Its core is a **Crypto Agility Layer** that supports two credential schemes: hash-based selective disclosure (SD-JWT) and BBS signatures, which allow unlinkable, zero-knowledge presentations. The scheme can change without redesigning the wallet.
* **Hardware-bound keys and proof of wallet integrity.** Holder keys live in a hardware root of trust. Attestation services prove that presentations come from the legitimate holder and from a wallet whose software is intact. This continues the line of work we started in [PRIVÉ](/projects/1_project/) {% cite Prive2024_10538525 %}.
* **Verifiable Data Registry.** A decentralised registry records trusted issuers and verifiers, credential schemas, revocation and travel policies. Trust in an issuer or a verifier is checked at each transaction, not assumed once. The wallet retrieves the verifier's policy and enforces locally what may be disclosed.
* **European Multi-Biometric Data Space.** Each Member State keeps the biometric data of its own nationals. Cross-border identity checks run without moving or revealing raw biometric data.

### The AI layer: fusing detector evidence into an explainable decision

At enrolment and at the border, several detectors examine the traveller: morphing detection, look-alike detection, makeup-attack detection, face verification and biometric matching against the data space. Each produces its own score. The officer needs one assessment, and needs to know why.

<img src="/assets/img/SafeTravellers_decision_pipeline.png" width="750">

The final design rests on a few deliberate choices.

* **Decision authority stays with an auditable model.** All detector outputs are normalised to a common risk scale. A deterministic, expert-calibrated fusion engine then computes the risk score. The same inputs always give the same output. Every score decomposes exactly into the contribution of each detector.
* **Machine learning explains; it does not decide.** A surrogate model is trained to mimic the fusion engine. SHAP is applied to the surrogate to show which signals are unusual for this specific traveller. A fidelity monitor compares surrogate and engine continuously. If they diverge, an alert is raised and explanations fall back to the exact decomposition.
* **Why not a learned classifier?** Real attack data at borders are scarce. Classifiers trained on synthetic attack data looked good on synthetic tests but proved brittle on real pilot inputs. Moving the learning task from "decide" to "mimic a known function" removed that problem.
* **Graded output, graded autonomy.** The system returns a risk score and the most likely attack type, not a yes/no. At pre-enrolment it drives the automated issuance of the travelling token, with flagged cases sent to a manual check. At the border it is decision support only; the officer decides. The same fusion logic runs in both settings, so a traveller is assessed consistently.

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
