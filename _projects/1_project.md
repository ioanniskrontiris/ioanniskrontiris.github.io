---
layout: page
title: TrustChain
description: with background image
img: assets/img/EUDIselectivedisclosure.png
importance: 1
category: work
related_publications: 10538525
---

Every project has a beautiful feature showcase page.
It's easy to include images in a flexible 3-column grid format.
Make your photos 1/3, 2/3, or full width.

1. Selective Disclosure with Unlinkability:
DOOR employs a modified version of the Direct Anonymous Attestation with Attributes (DAA-A) protocol, which allows users to selectively disclose only the necessary attributes during a transaction. Each attribute is cryptographically bound to the user's identity using a unique key, protected by hardware-based Roots of Trust (RoT). This ensures that the disclosed attributes cannot be linked across different transactions, even if they involve the same attribute or identity credential. By utilizing zero-knowledge proofs, DOOR guarantees that the identity provider and relying parties cannot collude to trace user activities.

1. Hardware-Backed Identity Assurance:
To meet the high Level of Assurance required by eIDAS 2.0, DOOR integrates hardware-based key management to securely store and manage the cryptographic keys associated with identity attributes. This approach prevents unauthorized access to identity credentials, ensuring that only the legitimate user can present their credentials. The hardware protection also ensures that even in the event of device compromise, the identity credentials remain secure and non-transferable.

1. The DOOR protocol achieves compatibility across different wallet implementations primarily through its use of the credential bridge concept. This concept enables DOOR to seamlessly integrate with a variety of identity wallets by acting as a mediator between the secure hardware components (like Trusted Platform Modules or cloud-based secure elements) and the identity credentials stored within the wallet. The credential bridge ensures that even if a wallet operates with different underlying technologies or storage methods, DOOR can securely manage and present credentials by linking them through this intermediary layer.