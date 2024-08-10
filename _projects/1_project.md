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

Anonymous credentials enable selective disclosure. The user may choose to reveal a subset of his credential attributes, or nothing at all other than the fact that his attributes satisfy a given policy. The user then convinces the verifier, via a zero-knowledge proof, of the authenticity of the disclosed information.

## The problem statement 

However this is not enough. How can someone be sure that the verifiable presentation of credential attributes really belong to the claimed entity? We need to ensure that credentials and (private) keys can only become available to this specific Holder as the actual owner of the issued Wallet credentials. That means the level of control and credential management assurance relies solely on possessing and controlling the private key, which in current designs is a software-based key. However, the use of a software keystore introduces many security risks and raises trustworthiness issues. 

One of the necessary measures to solve such security gaps, is to isolate the keys from the Holder while still being stored in the user’s domain. There are several types of isolation defined in the literature that can be achieved through the incorporation of trusted computing technologies, i.e., [Hardware Secure Module (HSM)]([https://](https://en.wikipedia.org/wiki/Hardware_security_module)), [Trusted Platform Module (TPM)]([https://](https://en.wikipedia.org/wiki/Trusted_Platform_Module)), or [Trusted Execution Environment (TEE)]([https://](https://en.wikipedia.org/wiki/Trusted_execution_environment)). All such trusted anchors provide reliable, tamper-evident, and secure processing units (including support for crypto operations, key storage, and authentication) that offer a trustworthy environment for executing applications

And still, this is not enough. What is still missing is the binding of identity data to the Holder (Holder Binding). This binding is based on a unique identifier representing the Holder, i.e., a secret key. One way to have high confidence is to make sure that the secret key is bound to the Wallet managing the identity data. For instance, DIF defines this property as Device Binding, that is, “a building block that enables a differential credential security model by anchoring a hardware-generated key (e.g., TPM Key) to the credential.”

## Cryptographic solution: the DOOR protocol
is the first to propose a protocol leveraging an enhanced variant of Direct Anonymous Attestation (DAA) [12] where each one of the attributes can be represented as a key, bound to the Holder’s unique identifier, which in turn is bound to the underlying trusted component. This allows the user to create privacy-preserving attribute claims (disclosing only those at- tributes needed to be checked against service access control policies) with strong trust guarantees on the correctness and origin of the attributes.

DOOR proposes an enhanced variant of an anonymous signature scheme, namely Attribute-based DAA (DAA-A) [13], to achieve this: DAA-A is a strong privacy- preserving authentication scheme that enables the construction of VPs with selective disclosure through the representation of attributes as keys, hence, enabling the encoding and sharing of complex structures as key hierarchies. To overcome the current limitation of traditional crypto schemes that do not consider VC/VP linkability issues leading to Holder profil- ing, we have designed an enhanced variant of DAA-A with “credential blinding” capabilities.

## Implementation: The Trusted Component (TC) Bridge

The Trusted Component (TC) Bridge is the main artifact delivered by PRIVE, which embodies the implementation of the solution and offers an API so that it can be seamlessly integrated with any EUDI wallet implementation. From an engineering perspective, the TC Bridge is a mechanism that allows seamless interaction between the secure hardware components of a user’s device (such as a Trusted Platform Module, or TEEs) and the various services and applications of the EUDI that need to utilize the cryptographic operations and privacy properties offered by PRIVE solution.

The TC Bridge has been engineered in order to offer the following properties:

1. **Mediation between Software and Hardware:** The TC Bridge acts as an intermediary layer that connects the software components of a digital identity system (such as the digital wallet application) with the hardware-based security features offered by the Trusted Component. The TC Bridge abstracts the complexity of direct hardware interactions, providing a standardized interface through which the software can request cryptographic operations, such as signing, encryption, or key management, without needing to handle the low-level details of the hardware.
2. **Credential Handling and Attestation:** The TC Bridge is responsible for facilitating the secure handling of credentials. For example, when a credential needs to be signed or verified, the TC Bridge routes these requests to the Trusted Component, which performs the necessary cryptographic operations in a secure environment. Additionally, the TC Bridge handles the generation and management of attestation certificates, such as the Direct Anonymous Attestation (DAA) certificates, which are used to prove the integrity and authenticity of the credentials without compromising user privacy.
3. **Key Management and Usage Policies:** A critical role of the TC Bridge is enforcing key management and usage policies as defined by the system’s security architecture. The Trusted Component typically holds cryptographic keys in a highly secure manner, and the TC Bridge ensures that these keys are only used according to predefined policies. This includes restrictions on how and when keys can be used, ensuring that they cannot be misused or accessed by unauthorized software or processes.
4. **Interoperability with Multiple Trusted Components:** The TC Bridge is designed to be interoperable with various types of Trusted Components, including different versions of TPMs, secure enclaves, or other hardware security modules. This flexibility allows the digital identity system to function across a range of devices and platforms, ensuring broad compatibility and adoption. The TC Bridge abstracts the differences between these components, providing a consistent API that the application layer can rely on.


## Real-world Use Case and Demonstration

PRIVE project has implemented and integrated anonymous credentials in a real-world Wallet. A big part of the project has been to also implement  a Use Case scenario, in order to demontrate the selective disclosure functionality in a real scenario. More specifically, PRIVE's Use Case focused on educational credentials, such as diplomas. Towards this direction, one major initiative currently in Europe is the development of [European Digital Credentials for Learning (EDC)]([https://](https://europass.europa.eu/en/stakeholders/european-digital-credentials)), which provides a standardized way to issue, share, and verify educational qualifications and achievements across Europe. EDC facilitates the digital transformation of learning credentials, ensuring they are portable, verifiable, and interoperable across different systems and borders. 

The integration of selective disclosure within [European Digital Credentials for Learning (EDC)]([https://](https://europass.europa.eu/en/stakeholders/european-digital-credentials)) allows learners to present only the necessary credentials to various stakeholders, such as potential employers or other educational institutions, without revealing their entire educational history. In this work, we take the specific example of job application process. 

Selective disclosure for the job application process becomes a powerful tool, because it can enable blind recruitment, which aims to reduce biases in hiring by concealing certain applicant attributes that could lead to discrimination. For example, the National Bureau of Economic Research (NBER) has shown that revealing age information during the first stages of recruitment process can lead to significant age discrimination. 

<img src="/assets/img/PRIVEUseCase.png" width="600">

PRIVE demonstrated the cryptographic solution in a real-world demonstrator with EUDI and EDCs for Learning. The scenario is the following: a job applicant is required to apply for a position as a mid-level software engineer through a job portal. The applicant must provide proof of their identity, educational qualifications, and work experience—all of which are managed and presented through their mobile wallet.

1. Credential Issuers:

* Previous Employer: The user has a credential issued by their previous employer that details their work experience. This credential is securely stored in the mobile wallet.
* eIDAS Node: The eIDAS node acts as an issuer of the electronic identification (eID) credential, which verifies the user’s identity in accordance with EU regulations. This eID is also stored within the mobile wallet.
* EDC Issuer (Educational Credential): The user’s educational background, such as a diploma or degree certificate, is issued by an educational institution that complies with the European Digital Credentials for Learning (EDC) framework. This credential is stored alongside others in the mobile wallet.

2. Mobile Wallet:

The user’s mobile wallet is the central repository where all verifiable credentials are stored. The wallet leverages the PRIVÉ solution, which supports hardware-backed security features to ensure the integrity and authenticity of the credentials. The wallet allows the user to manage these credentials and selectively disclose only the necessary attribute values.  

3. Application Process:

* Verifiable Presentation: When applying for the software engineering position, the user generates a Verifiable Presentation (VP) from their mobile wallet. This VP selectively discloses only the credential attributes (e.g. educational qualifications, and work experience) required by the job portal. These are described in a policy sent by the the job portal to the user. 
* Policy Enforcement: The job portal through a policy dictates what kind of credentials and attributes are necessary for the application. The mobile wallet ensures that only the relevant credentials that meet this policy are shared, maintaining the user’s privacy.

## User Acceptance of Selective Disclosure in EUDI  

The European Commission sets a very ambition goal: at least 80% of citizens should be able to use a digital ID solution to access key public services by 2030. To achieve this goal, we need to start talking about the factors that affect users’ adoption of the technology. In the PRIVÉ project, a comprehensive user adoption analysis was conducted to understand the factors influencing the adoption of EUDI Wallets, particularly focusing on the secure and privacy-preserving aspects offered by PRIVÉ's solution. 

Given that Identity Wallets is a new technology that most users have not experience using before, trust plays a crucial role in their decision to adopt it. 

To evaluate our model, we conducted a comprehensive user trial focusing on the above job application scenario using eIDAS and European Digital Credentials for Learning. This trial gathered empirical data on user interactions with the EUDI Wallet and their perceptions of its features, particularly those related to selective disclosure and trust. 

The user trial for the PRIVÉ project involved recruiting a diverse group of participants through an open call, ensuring representation across various demographics, technological proficiency levels, and geographic regions. During the trial, the users installed the identity wallet on their mobile phones and tried it out in a hypothetical scenario of applying for a job. At the end, feedback was collected through a questionnaire that users had to answer. 

The PRIVÉ project utilized the Technology Acceptance Model (TAM) as the foundational framework for collecting feedback and analyzing user adoption factors. The TAM model had to be extended to capture how much different aspects of trust affect their decision to adopt the technology. 


## Other Digital Signature Schemes Compatible with Anonymous Credentials
BBS/BBS+ 

