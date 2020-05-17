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
