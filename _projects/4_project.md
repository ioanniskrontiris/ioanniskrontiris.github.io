---
layout: page
title: ABC4Trust
description: another without an image
img: assets/img/abc4trust.png
importance: 2
category: work
related_publications: 10538525, apf
---

Attribute-based Credentials for Trust (ABC4Trust) was an EU-funded project from 2010–2015 that defined a common, unified architecture and delivered open reference implementations of Anonymous Credential systems. Its consortium includes both Microsoft and IBM, and ABC4Trust integrates both U-Prove and Idemix into its architecture. It also included the two pilot projects in Patras, Greece and Söderhamn, Sweden. ABC4Trust promoted collaborations between the big players and accelerated advances in the field of Anonymous Credentials. Its deliverables can be found here, and its Java source code is available in this repository.

### The Problem: Anonymous Authentication with Anonymous Credentials
Anonymous authentication allows users to verify their identity or attributes without revealing personal information, ensuring privacy in digital interactions. However, traditional methods of authentication often expose more data than necessary, leading to privacy risks. Anonymous credentials provide a solution by enabling users to authenticate with the minimum required information, protecting their identity and ensuring that their actions cannot be traced back to them by service providers or third parties.

Anonymous credentials can be broadly categorized into two types: Multi-Use Anonymous Credentials and Single-Use Anonymous Credentials. ABC4Trust considered two specific schemes:

1.	**Idemix** (Identity Mixer): Idemix is a cryptographic protocol designed for multi-use anonymous credentials. It allows users to prove possession of certain attributes (like age or membership) without revealing their full identity. Idemix uses advanced cryptographic techniques, including zero-knowledge proofs and special digital signatures, enabling users to authenticate multiple times while ensuring that their interactions cannot be linked to each other. This makes it a powerful tool for scenarios requiring repeated authentication with strong privacy guarantees.
2.	**U-Prove**: U-Prove is an example of single-use anonymous credentials. It allows users to generate a credential for a specific purpose and use it only once, ensuring that even if multiple verifications occur, they cannot be linked back to the user. U-Prove achieves this based on blind cryptographic protocols designed by Stefan Brands, where the credential is issued in such a way that the issuer cannot later trace its use. This makes U-Prove highly efficient and ideal for applications like digital coupons, voting, or single-use tokens.

Both solutions implement selective disclosure using their underlying cryptographic primitives.
The development of U-Prove and Idemix resulted in the ABC4Trust project that brought together both technologies and aimed to define a unified architecture for federating and interchanging different cryptographic primitivies to implement anonymous credentials. Both Idemix and U-Prove were integrated into its architecture.
	
### Achievements

The ABC4Trust project achieved several key milestones in its efforts to enhance privacy and identity protection on the Internet through the use of cryptographic technologies:

1. **Development of a Unified Architecture**: ABC4Trust successfully defined a common, unified architecture for Attribute-Based Credential (ABC) systems. This architecture allows for the comparison of different ABC systems and facilitates their integration on common platforms[3].

2. **Open Reference Implementations**: The project delivered open reference implementations of selected ABC systems, which were deployed in real-world production pilots. These implementations demonstrated the practical application of privacy-preserving technologies in various contexts[3].

3. **Pilot Projects**: Two pilot sites were established at Patras University in Greece and Norrtullskolan secondary school in Sweden. These pilots tested privacy-enabling technology for school portals and electronic evaluation of university courses, allowing users to prove specific attributes without revealing their full identities[3].

4. **Interoperability of Technologies**: The project achieved interoperability between IBM’s Identity Mixer and Microsoft’s U-Prove technologies. This integration ensured that users' identities and personal attributes were protected when interacting with service providers[3].

5. **Interoperability of Technologies**: ABC4Trust contributed to standardization efforts by aligning with relevant ISO/IEC projects and contributing to drafts such as ISO/IEC 29101 (Privacy Architecture Framework) and ISO/IEC 29191 (Requirements for partially anonymous, partially unlinkable authentication). It also developed a metrics framework for comparing different ABC systems. This framework helps in assessing and ensuring the compatibility and interoperability of various ABC technologies.


Overall, ABC4Trust made significant contributions to the field of privacy and identity protection, advancing the state of the art in cryptographic technologies and demonstrating their applicability in real-world settings.

Citations:
[1] https://abc4trust.eu/announcements
[2] https://abc4trust.eu
[3] https://www.cryptoexperts.com/research/projects/abc4trust/
[4] https://abc4trust.eu/download/ABC4Trust-Project-Description.pdf
[5] https://cordis.europa.eu/article/id/33059-protecting-identities-and-privacy-with-innovative-eufunded-technology