---
layout: page
title: TrustChain
description: with background image
img: assets/img/EUDIselectivedisclosure.png
importance: 1
category: work
related_publications: 10538525
---

[PRIVE]([https://](https://trustchain.ngi.eu/prive/)) was funded as a sub-grantee of [TrustChain]([https://](https://trustchain.ngi.eu/)) (Open Call 1 – Decentralised Digital Identity) during the period October 2023 - April 2024. TrustChain is part of the European Commission’s Next Generation Internet (NGI) initiative. 

PRIVE designs and demonstrates a solution that uses anonymous credentials in [EU Digital Identity Wallet (EUDI)]([https://](https://ec.europa.eu/digital-building-blocks/sites/display/EUDIGITALIDENTITYWALLET/EU+Digital+Identity+Wallet+Home)). Through this cryptographic mechanism, EUDI achieves secure and privacy-preserving authentication and identification. 

Private key 

Selective disclosure
Anonymous credentials enable selective disclosure. The user may choose to reveal a subset of his credential attributes, or nothing at all other than the fact that his attributes satisfy a given policy. The user then convinces the verifier, via a zero-knowledge proof, of the authenticity of the disclosed information.


How can someone be sure that they really belong to the claimed entity? On a technical level, this translates into Holders having control of their own VCs and DIDs through their Wallets, which can ensure that credentials and (private) keys can only become available to this specific Holder as the actual owner of the issued Wallet credentials. Since it is only the Holder (as the Identity Owner) that knows the (private) key associated with a DID, the level of control and credential management assurance relies solely on possessing and controlling the private key, which in current designs is a software-based key. However, the use of a software keystore introduces many security risks and raises trustworthiness issues [5], [6]. So the above challenge translates into the more technical question: How can a Verifier be sure that the respective key of the Holder presenting a VC remains under her control, and cannot be used by any other unauthorized entity?

One of the necessary measures to solve such security gaps, and reach LoA “high”, is to isolate the keys from the Holder while still being stored in the user’s domain. There are several types of isolation defined in the literature that can be achieved through the incorporation of trusted computing technologies, i.e., Hardware Secure Module (HSM), Trusted Platform Module (TPM), or Trusted Execution Environment (TEE). All such trusted anchors provide reliable, tamper- evident, and secure processing units (including support for crypto operations, key storage, and authentication) that offer a trustworthy environment for executing applications

Another requirement to achieve LoA ”high” is the binding of identity data to the Holder (Holder Binding). This binding is based on a unique identifier representing the Holder, i.e., a secret key. One way to have high confidence is to make sure that the secret key is bound to the Wallet managing the identity data. For instance, DIF defines this property as Device Binding, that is, “a building block that enables a differential credential security model by anchoring a hardware-generated key (e.g., TPM Key) to the credential.”

1. Selective Disclosure with Unlinkability:
DOOR employs a modified version of the Direct Anonymous Attestation with Attributes (DAA-A) protocol, which allows users to selectively disclose only the necessary attributes during a transaction. Each attribute is cryptographically bound to the user's identity using a unique key, protected by hardware-based Roots of Trust (RoT). This ensures that the disclosed attributes cannot be linked across different transactions, even if they involve the same attribute or identity credential. By utilizing zero-knowledge proofs, DOOR guarantees that the identity provider and relying parties cannot collude to trace user activities.

1. Hardware-Backed Identity Assurance:
To meet the high Level of Assurance required by eIDAS 2.0, DOOR integrates hardware-based key management to securely store and manage the cryptographic keys associated with identity attributes. This approach prevents unauthorized access to identity credentials, ensuring that only the legitimate user can present their credentials. The hardware protection also ensures that even in the event of device compromise, the identity credentials remain secure and non-transferable.

## Implementation 

The DOOR protocol achieves compatibility across different wallet implementations primarily through its use of the credential bridge concept. This concept enables DOOR to seamlessly integrate with a variety of identity wallets by acting as a mediator between the secure hardware components (like Trusted Platform Modules or cloud-based secure elements) and the identity credentials stored within the wallet. The credential bridge ensures that even if a wallet operates with different underlying technologies or storage methods, DOOR can securely manage and present credentials by linking them through this intermediary layer.

## Real-world Use Case and Demonstration

PRIVE project has implemented and integrated anonymous credentials in a real-world Wallet. A big part of the project was to implement also a Use Case scenario to demontrate the selective disclosure functionality in a real scenario. More specifically, PRIVE's Use Case focused on educational credentials, such as diplomas. ARF points to the use case where digital diploma attestations can be shared across borders in a format that is verifiable, trusted, and easy to use for another educational or training institution or a prospective employer. Towards this direction, one major initiative currently in Europe is the development of [European Digital Credentials for Learning (EDC)]([https://](https://europass.europa.eu/en/stakeholders/european-digital-credentials)), which provides a standardized way to issue, share, and verify educational qualifications and achievements across Europe. EDC facilitates the digital transformation of learning credentials, ensuring they are portable, verifiable, and interoperable across different systems and borders. 

The integration of selective disclosure within [European Digital Credentials for Learning (EDC)]([https://](https://europass.europa.eu/en/stakeholders/european-digital-credentials)) allows learners to present only the necessary credentials to various stakeholders, such as potential employers or other educational institutions, without revealing their entire educational history. In this work, we take the specific example of job application process. In this context, selective disclosure becomes a powerful tool for enabling blind recruitment, which aims to reduce biases in hiring by concealing certain applicant attributes that could lead to discrimination. For example, the National Bureau of Economic Research (NBER) has shown that revealing age information during the recruitment process can lead to significant age discrimination. In a study comparing age-blind and non-age-blind hiring procedures, it was found that age-blind procedures resulted in higher interview rates for older applicants, although the job offer rates remained lower once the age was revealed during in-person interviews~\cite{neumark2024age}. This evidence underscores the need for mechanisms that allow job applicants to hide sensitive attributes such as age, thereby promoting fairer hiring practices.

![Alt text](/assets/img/PRIVEUseCase.png "a title")


## User Acceptance of Selective Disclosure in EUDI  

The European Commission sets a very ambition goal: at least 80% of citizens should be able to use a digital ID solution to access key public services by 2030. To achieve this goal, we need to start talking about the factors that affect users’ adoption of the technology. 

Trust plays a crucial role in the user adoption of the EU Digital Identity Wallet. It is essential for ensuring that users feel confident in using the wallet to store and manage their digital identities and credentials. Trust in digital systems is rooted in the perceived reliability and protective role of the institutions behind them. For the EU Digital Identity Wallet to be widely adopted, it must address users' expectations and concerns, particularly regarding privacy and data security

To evaluate our model, we conducted a comprehensive user trial focusing on the job application scenario using eIDAS and European Digital Credentials for Learning. This trial aimed to gather empirical data on user interactions with the EUDI Wallet and their perceptions of its features, particularly those related to selective disclosure and privacy protection.

The user trial involved a diverse group of participants, including recent graduates and professionals. Participants were recruited through an open call, ensuring a broad representation of potential users. The trial was designed as a hands-on experience, providing participants with our own implementation of a digital identity wallet. During the trial, users had to download and install the wallet on their mobile devices. 

After downloading the wallet on their mobile phones, users had only one pre-loaded credential containing information about a specific work experience and was provided to the user from their old employer. Then the users had to populate their wallet with two additional VCs: one about their identity and one about their education diploma. For our user trial we specifically setup two credential issuers. First, an eIDAS test node that provided users with a comprehensive set of identity information. Second, an issuer mimicking real-world Education and Training Certificates issued under the European Digital Credentials Initiative (EDCI). 

## Other Digital Signature Schemes Compatible with Anonymous Credentials
BBS/BBS+ 

