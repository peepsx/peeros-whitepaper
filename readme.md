# PeerOS - The Hybrid Operating System 
**By:** Jared Rice Sr.
**Authored On:** May 15th, 2020

**NOTE:** ***Citations appear within brackets [], containing the first four-letters of the author's name and two numbers indicating the year the source was authored. (Example: [RICE20])***

## Abstract
An operating system (OS) designed around a decentralized software development framework like [Arisen](https://github.com/arisenio/technical-whitepaper) and P2P network protocols like [dWeb](https://github.com/distributedweb/whitepaper), would not only allow for improved security mechanisms surrounding user authentication, data integrity and confidentiality, but would also bring forth an ecosystem for developing truly decentralized applications (dApps) that utilize a hybrid of a local computing environment and outside, decentralized multicomputer systems (DMS). PeerOS brings to life the first iteration of a "hybrid operating system" or "hybrid OS", a program designed to authenticate and control the execution of applications across a hybrid computing environment. A hybrid OS like PeerOS also provides multiple interfaces (ISA, ABI and API) between local and decentralized computing environments, so that applications can ultimately be designed for the direct utilization of local and decentralized computing hardware and resources, based on the needs of an application itself.

While typical users of an operating system are generally not concerned with the details of computer hardware and typically view a computer system in terms of a set of applications [STAL17], they are on the other hand concerned with the security and privacy implications of these systems. Due to the centralized nature of modern-day operating systems and their incompatibility with decentralized multicomputer systems, once an OS and its local computing environment are compromised, most if not all of the applications (centralized and decentralized) running on top of it, are typically compromised as a result. A hybrid OS, like PeerOS, relies on an outside DMS for asymmetric cryptography-based user authentication and its own universal authentication layer (UAL) known as PeepsID, that utilizes account-based permissions, each with their own cryptographic identity, when executing applications within its application layer. If PeerOS were compromised, the applications on top of the system would not be compromised if the attacker were unable to sign a particular application-related execution with the cryptographic identity related to the permission-level required by the execution itself, since PeerOS-based application executions require a specific permission-level in order to execute via Arisen's DMS. This ultimately births an operating system that provides significantly improved security and private features when compared to other operating systems, as well as many other economic, trust and performance-based enhancements that are extensively covered in this paper.

## Contents
[Abstract](#abstract)
[Contents](#contents)
[Introduction](#introduction)
[The Evolution Of The OS](#the-evolution-of-the-os)
[The Hybrid OS](#the-hybrid-os)
[System Architecture](#system-architecture)
- [Architecture Overview](#architecture-overview)
- [Universal Authentication Layer (UAL)](#universal-authentication-layer-ual)
- [Application Layer](#application-layer)
- [Application Framework Layer](#application-framework-layer)
- [Hybrid API Layer](#hybrid-api-layer)
- [Hybrid IPC Layer](#hybrid-ipc-layer)
- [Local Runtime Layer](#local-runtime-layer)
- [System Layer](#system-layer)
- [Kernel Layer](#kernel-layer)
[System Features](#system-features]
- [Universal-User-Authentication](#universal-user-authentication)
- [Multi-DMCS Architecture](#multi-dmcs-architecture)
- [DMCS Dispatch](#dmcs-dispatch)
- [Hybrid File System](#hybrid-file-system)
- [Decentralized Application Marketplace](#decentralized-application-marketplace)
- [The Decentralized Web & P2P Networking Protocols](#the-decentralized-web-and-p2p-networking-protocols)
- [Decentralized ADT (Application Development Tools)](#decentralized-adt)
- [Secure Key Vault](#secure-key-vault)
[PeerOS Stock Applications](#peeros-stock-applications)
- [dBrowser](#dbrowser)
- [dBnk](#dbnk)
- [dPay](#dpay)
- [dMessenger](#dmessenger)
- [dTalk](#dtalk)
- [dBox](#dbox)
- [dTunes](#dtunes)
- [dSocial](#dsocial)
- [dAppStore](#dappstore)
- [Nucleus IDE](#nucleus-ide)
- [Calendar](#calendar)
- [Calculator](#calculator)
- [Camera](#camera)
- [Photos](#photos)
- [Videos](#videos)
- [Settings](#settings)
[Advantages Of PeerOS](#advantages-of-peeros)
- [A Completely Decentralized Ecosystem & Economy](#a-completely-decentralized-ecosystem-economy)
- [The Single Account Model (SAM)](#the-single-account-model-sam)
- [Trustworthy, Secure & Highly Available Applications](#trustworthy-secure-and-highly-available-applications)
- [Integrated & Secure Payment Networks](#truly-secure-payment-systems)
- [Application and Data Transparency](#application-and-data-transparency)
- [Complete Privacy](#complete-privacy)
- [More Than Just An Operating System](#more-than-just-an-operating-system)
[Conclusion](#conclusion)

## Introduction
The operating systems used today are full of security issues, privacy concerns and centralized applications that will never be able to protect their user's data. Thankfully, decentralized applications were conceptualized and have proven to be far more secure, trusted and reliable than their centralized counterparts. One could even make the argument that dApps are mathematically impossible to hack and their users are mathematically impossible to exploit as well, that is, if dApps enable their users to securely store and utilize private keys in the process of signing transactions. The problem is, decentralized applications are either available insecurely through an easily exploitable web browser or an OS packed with malicious software, both of which were never designed as a proper venue for the deployment of decentralized applications. Even worse, today's operating systems are not architecturally sound when it comes to properly and securely handling the signing of transactions on a dApp's behalf. 

The computer that signs a dApp-related transaction, on behalf of a DMCS, must have unlocked private keys loaded into memory [WOOD19]. This creates many potential security issues on most traditional operating systems. Malicious software (malware) has been known to destroy files and data in main memory, bypassing controls to ultimately give intruders privileged access, thus, providing a means for intruders to bypass access controls [STALL17], thereby potentially giving an attacker access to private keys stored in memory, as well as all the digital assets and control mechanisms that can be accessed through the use of private keys that could be stolen during an attack. Despite today's operating systems lacking processes that allow for users to securely identify themselves with dApps and the DMCS where validation ultimately takes place, they also lack secure processes for managing user authentication on their own systems. This is also problematic, considering an operating system's fundamental building block and primary line of defense against attacks to its system is "user authentication" [STALL17] defined by [RFC 4949] (The Internet Security Glossary), as "a process of verifying an identity claimed by or for a system entity". Typical operating systems utilize a combination of four methods for authenticating a user's identity [STALL17]:

1. Something the individual knows (password, pin number or prearranged set of questions)
2. Something the individual possesses (electronic key cards, smart cards and physical keys)
3. Something the individual is (static biometrics such as recognition by fingerprint, retina and face)
4. Something the individual does (dynamic biometrics such as voice pattern, handwriting characteristics and typing rhythm)

All of the methods mentioned above, when properly implemented and used, can provide secure authentication, however, each of the above methods have their issues. Passwords are easily guessable or easily forgotten and keycards or smart cards (tokens) are easily stolen or lost. With respect to biometric authenticators, there are an assortment of issues including false positives, false negatives, user acceptance, convenience and of course, cost. Above all, it is nearly impossible to manage and secure passwords or tokens properly on these systems, since authentication comes from the local system itself [STALL17] or, as has been seen recently with Google's ChromeOS, via a centralized user database which has been proven time and time again to be easily exploitable. This is especially the case, if the local system where the user is being authenticated is being monitored by a "masquerader" [ANDE80]. The next line of defense for operating systems is access controls, like discretionary access control (DAC), mandatory access control (MAC), role-based access control (RBAC) or attribute-based access control (ABAC) where a "policy" dictates what types of access are permitted, under what circumstances and by who. 

Even with access-control mechanisms, these mechanisms and their authentication processes take place on a local system, which if exploited, could be controlled by rogue processes that gain power via various attack vectors (i.e. buffer overflow). The state of the art for a hybrid operating system like PeerOS, is that it utilizes a combination of local authentication methods (static biometrics) and a specialized system for "offline transaction signing", to authenticate its users via a decentralized multicomputer system (DMCS) like Arisen, instead of handling authentication solely on the end-user's local computer system or via a centralized database. Since the DMCS handles user authentication and account management, it is also responsible for handling access-control mechanisms as well. In essence, PeerOS could be considered a massive, monolithic dApp, that powers other dApps, since it, as well as the dApps within it, utilize a decentralized network of computers for much of their functionality. Although, PeerOS still utilizes a microkernel for interacting with the end-user's local computer hardware via its own hardware abstraction layer (HAL), which makes it much more than just a dApp. From a computer science perspective, it's a decentralized operating system but considering it handles executions between two different computer systems by way of API/IPC-based methods via the respective operating systems on these systems, the proper scientific terminology for such system, would be "hybrid operating system".

As a result of the PeerOS architecture, the OS uses what is known as a [Single Account Model (SAM](#single-account-model-sam) meaning, the same account used to login to the operating system itself, is the same account used for the applications installed on top of it (ex. if the @jared user is logged into PeerOS, @jared is also logged into dApps installed on the system like dSocial). Although, for a user (i.e. @jared) to execute "actions" from within these applications, these actions must be signed with a private key, matching the specific access-role (permission-level) of a user. Private keys on PeerOS are designed to be stored within an "air-gapped", offline system layer, known as a "Secure Key Vault" (SKV) where cryptographic identities pertaining to a user's various access-roles are securely stored for offline transaction signing. The SKV can only be communicated with via the "dMemo" messaging protocol, available via the dMemo system service, which in-turn is only able to communicate serialized unsigned transactions to the SKV when a user gains access to the dMemo service via the successful validation of static biometric details (retina, facial or fingerprint recognition). Upon the dMemo service sending an unsigned transaction to the SKV, the SKV returns a digital signature and the serialized transaction data associated with it, which is then broadcasted to a DMCS via PeerOS' hybrid IPC layer for validation. This process ensures that a user's private keys are properly secured even if the local computer environment is exploited through various attack vectors. 

Since dApps are executed via a DMCS, the data associated with these executions are stored on the DMCS as well, rather than having to be stored in a central database somewhere or within the end-user's local environment where data can easily be altered or manipulated. dApps built for PeerOS can retrieve data related to the application and an associated account on the DMCS via its "hybrid API layer" which like the "hybrid IPC layer" connects to communication interfaces of local hardware components, as well as the communication mechanisms provided by the DMCS (ex. aOS RPC-based API). A more in-depth description of both layers can be found in [System Architecture](#system-architecture).  Even though dApp related data is for the most part stored on the DMCS, PeerOS can still operate offline, where users are able to "queue" actions pertaining to specific dApps (i.e. posting to dSocial), where a queue of signed transactions are stored by the dMemo service, so that they can be broadcasted at a later time, when the local computer system comes online. Also, as dApps are used, PeerOS provides a cache mechanism which allows dApps to store an immutable copy of the data it retrieves via its hybrid API layer for performance purposes and to keep dApps from having to constantly query DMCS nodes for data. PeerOS users also have the option to keep a local copy of the entire state of a DMCS, so that the entire state of any dApp on the system can be reproduced without an internet connection. Of course, once the local system comes back online, it will download updates to the DMCS' state that occurred while the local system was offline. 

A user's personal data, on the other hand, including messages, contacts, calendar data, location data and other miscellaneous types of data is still stored on the local computer system's block devices. Although, an attacker must still authenticate themselves, just as authentication takes place with dApp-based executions, in order to gain access to or manipulate data on the local system itself. Because of this authentication process, an attacker would have to bypass both the local system (biometrics and offline-key signing), as well as the DMCS (ECDSA math and consensus algorithms), to authenticate themselves through PeerOS' [Universal Authentication Layer (UAL)](#universal-authentication-layer), which is not only virtually impossible, Arisen (PeerOS' DMCS of choice) is governed by elected "block producers", who by a 15/21 vote, can reverse rogue executions, freeze accounts and change the cryptographic keys associated with a hijacked account on the DMCS [RICE19 and LARI19], further securing PeerOS' local computer environment as a result, without centralizing or subjecting the system to irreversible abuse.

Lastly, PeerOS and its stock dApps such as dBnk and dPay, enable other dApps, made available via its decentralized application marketplace (dAppStore), to provide economic functionality to dApp developers, centered around the native cryptographic currencies available via Arisen's DMCS. As a result, the end-user does not have to worry about attackers having the ability to steal their "financial resources" thanks to how PeerOS' user authentication process and its UAL. This also makes PeerOS much more than just an operating system. Thus, PeerOS could give birth to a decentralized economy that has the potential to kick start a decentralized software revolution, that will allow us to re-imagine everything from banking systems, to how we conduct scientific research. More importantly, it allows us to do these things securely, from the secure signing of transactions by the end-user themselves, to the immutable executions that happen on the DMCS. 

The intention of this paper is to thoroughly explain how a hybrid operating system like PeerOS works, its system architecture, features, stock applications, as well as its obvious advantages and benefits when compared to traditional operating systems.
