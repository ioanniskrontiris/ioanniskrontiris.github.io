---
layout: page
title: ABC4Trust
description: FP7 project - A unified architecture for Anonymous Credentials
img: assets/img/abc4trust_logo.png
importance: 5
category: work
related_publications: 10538525, apf
---

[ABC4Trust](http://abc4trust.eu/) was a project that received research funding from the 7th Research Framework Program (FP7) of the  EU as part of the Trust & Security Program. 

The project took place during the period November 2010 – February 2015 and it was a collaborative effort involving [12 partners](https://abc4trust.eu/home/consortium) from industry, academia, research centres and data protection authorities.


### Anonymous Authentication with Anonymous Credentials
Anonymous authentication allows users to verify their identity or attributes without revealing personal information, ensuring privacy in digital interactions. However, traditional federated identity management has introduced increased security and privacy risks, since in this setup identity is shared across domains. More specifically, it is usually the case that when the certificates contain user-specific attributes they also require disclosure of all these attributes with every usage, which violates the privacy paradigm of data minimization (even though it can be avoided with Online IdPs or Single Sign-On (SSO) schemes). 

A common weakness through all solutions is the problem of linkability, meaning that the IdP typically learns which Service Provider the user is trying to access. This information is often provided to the IdP in order to protect the security token or to redirect the user to the right location. A related problem to linkability, is the problem of traceability, meaning that we now have a single party, the IdP, which will learn about every service provider that the user wishes to access. At the same time,  any two service providers that compare logs will also be able to identify if the same user has been using both services. 

One of the core requirement for privacy protection in identity management systems is to place the user in-between the Identity Provider and the Relying Party and make sure that any information flow goes through the user so that they can maintain control of their information.  Users are storing credentials locally and then they control what they share with others, by presenting ``claims''.

* Minimal Disclosure: Privacy-ABCs allow the users to derive authentic and verifiable tokens from their credentials that contain only the required information, therefore avoiding disclosure of all the attributes in the credentials.

* Unlinkability: Another key feature of Privacy-ABCs is unlinkability that comes in two different types, namely, unlinkability to their issuance, and unlinkability across different presentations. The IdP is only involved once, at credential issuance, but does not need to be contacted at every authentication request. This means that the issuance and the usage (presentation) of a credential cannot be correlated.

* Partial Identities and identifiers: The concept of Pseudonyms in Privacy-ABCs enable users to generate an unlimited number of unlinkable pseudonyms from their secret key and establish different profiles across different services.


Anonymous credentials provide a solution that satisfy the above properties. They enable users to authenticate with the minimum required information, protecting their identity and ensure that their actions cannot be traced back to them by service providers or third parties Anonymous credentials can be broadly categorized into two types: Multi-Use Anonymous Credentials and Single-Use Anonymous Credentials. ABC4Trust considered two specific schemes:

1.	**Idemix** (Identity Mixer): Idemix is a cryptographic protocol designed for multi-use anonymous credentials. It allows users to prove possession of certain attributes (like age or membership) without revealing their full identity. Idemix uses advanced cryptographic techniques, including zero-knowledge proofs and special digital signatures, enabling users to authenticate multiple times while ensuring that their interactions cannot be linked to each other. This makes it a powerful tool for scenarios requiring repeated authentication with strong privacy guarantees.
2.	**U-Prove**: U-Prove is an example of single-use anonymous credentials. It allows users to generate a credential for a specific purpose and use it only once, ensuring that even if multiple verifications occur, they cannot be linked back to the user. U-Prove achieves this based on blind cryptographic protocols designed by Stefan Brands, where the credential is issued in such a way that the issuer cannot later trace its use. This makes U-Prove highly efficient and ideal for applications like digital coupons, voting, or single-use tokens.

Both solutions implement selective disclosure using their underlying cryptographic primitives. The development of U-Prove and Idemix resulted in the ABC4Trust project that brought together both technologies and aimed to define a unified architecture for federating and interchanging different cryptographic primitivies to implement anonymous credentials. Both Idemix and U-Prove were integrated into its architecture.
	
### Waht ABC4Trust achieved

The ABC4Trust project achieved several key milestones in its efforts to enhance privacy and identity protection on the Internet through the use of cryptographic technologies:

1. **Development of a Unified Architecture**: ABC4Trust successfully defined a common, unified architecture for Attribute-Based Credential (ABC) systems. This architecture allows for the comparison of different ABC systems and facilitates their integration on common platforms[3].

2. **Open Reference Implementations**: The project delivered open reference implementations of selected ABC systems, which were deployed in real-world production pilots. These implementations demonstrated the practical application of privacy-preserving technologies in various contexts[3].

3. **Pilot Projects**: Two pilot sites were established at Patras University in Greece and Norrtullskolan secondary school in Sweden. These pilots tested privacy-enabling technology for school portals and electronic evaluation of university courses, allowing users to prove specific attributes without revealing their full identities[3].

4. **Interoperability of Technologies**: ABC4Trust contributed to standardization efforts by aligning with relevant ISO/IEC projects and contributing to drafts such as ISO/IEC 29101 (Privacy Architecture Framework) and ISO/IEC 29191 (Requirements for partially anonymous, partially unlinkable authentication). It also developed a metrics framework for comparing different ABC systems. This framework helps in assessing and ensuring the compatibility and interoperability of various ABC technologies.

5. **New Technology Adoption Model for PETs**: ABC4Trust was the first project to study the factors influencing adoption of PETs by end-users. It extended the traditional Technology Acceptance Model (TAM) and tailored it for privacy-enhancing technologies (PETs), making it more applicable to understanding user adoption in security and privacy contexts. Additionally, it is among the first to empirically test these constructs in a real-world trial, providing valuable insights into the factors that influence the acceptance of anonymous credentials in practical scenarios. 

