---
layout: page
title: project 4
description: another without an image
img:
importance: 2
category: work
---

Further advancements were achieved with the real-life implementations of ACs, U-Prove and Idemix, where authors tried to improve or implement them for a specific research field. U-Prove [26] is based on blind cryptographic protocols designed by Stefan Brands, focusing on user-centric identity management where digital identity is connected to tamper- resistant devices such as smart cards. Brands founded Creden- tica in 2004 and developed U-Prove. U-Prove was acquired by Microsoft in 2008 [27].
In 2002, Jan Camenisch and Els Van Herreweghen from IBM presented Idemix, built for the PRIME/PRIMELIFE project, an AC system based on the CL signature scheme that allows anonymous, yet authenticated and accountable, trans- actions [28,29]. Both solutions implement selective disclosure using their underlying cryptographic primitives, which will be explained in the following sections.
The development of U-Prove and Idemix resulted in an EU- funded project known as Attribute-based Credentials for Trust (ABC4Trust) 2010–2015 [30]. The project aimed to define a typical unified architecture for federating and interchang- ing different privacy ABC systems. ABCs are defined as a form of authentication mechanism that allows one to flexibly and selectively authenticate different attributes about an en- tity without revealing additional information about the entity. Privacy ABCs (pABCs) allow holders to reveal and prove the minimal information required. Both Idemix and U-Prove were integrated into its architecture. Besides them, further schemes were introduced. One of them is HM12 scheme [31] with discrete logarithm commitments. The other one is open source IRMA app (“I Reveal My Attributes”) known as the Yivi app [32], based on the Idemix ABC scheme which supports privacy-preserving features. Due to the popularity of Idemix, there are several papers discussing selective disclo- sure in specific credentials using CL signatures such as stan- dard Java Cards [33], auditing [34], e-health [35], electronic coupons [36].

Attribute-based Credentials for Trust (ABC4Trust) was an EU-funded project from 2010–2015 that defined a common, unified architecture and delivered open reference implementations of ABC (Anoncred) systems. Its consortium includes both Microsoft and IBM, and ABC4Trust integrates both U-Prove and Idemix into its architecture [SR14, RCS15]. It also included the two pilot projects in Patras, Greece and Söderhamn, Sweden. ABC4Trust promoted collaborations between the big players and accelerated advances in the field of Anoncreds. Its deliverables can be found here, and its Java source code is available in this repository.

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