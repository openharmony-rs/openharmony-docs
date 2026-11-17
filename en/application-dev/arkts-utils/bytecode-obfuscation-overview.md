---
kits: ["ArkTS Kit / Ark Programming Language"]
description: "Provides an overview of the capabilities and applicable scenarios of the ArkGuard bytecode obfuscation tool, explains its differences from source code obfuscation, and indexes subtopics such as obfuscation principles and the getting-started guide to help developers quickly begin learning bytecode obfuscation."
keywords: [ArkGuard, obfuscation, bytecode obfuscation, obfuscation overview, obfuscation tool, anti-reverse engineering, package size, bytecode obfuscation principles]
doctype: guide
status: active
---

# Overview of ArkGuard for Bytecode Obfuscation
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @oatuwwutao; @Graceunderpressure-->
<!--Designer: @oatuwwutao-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=17ae88719a2d37a0c07e3b6e33ddb120ebd3dbc5 translatedAt=2026-11-06T10:26:39.422Z pushedAt=2026-11-11T08:03:51.544Z nl=1 -->

Starting from API version 20, ArkGuard provides basic bytecode obfuscation capabilities, which turn names such as function names, class names, and file names in the code into short, meaningless names, making it harder to guess their purposes by reading the code. Since identifier names are shortened, obfuscation can effectively reduce the package size.

**Applicable scenarios**: suitable for projects with high requirements for **security and anti-reverse engineering**, especially applications involving **sensitive business logic**, key algorithms, or proprietary interface implementations. It is recommended to enable it as needed in release builds.

This section describes how to use ArkGuard. It aims to assist you in efficiently applying obfuscation to your bytecode, thereby increasing its complexity and making reverse engineering more challenging.

Compared with source code obfuscation, bytecode obfuscation targets bytecode files.

- [ArkGuard Principles and Capabilities for Bytecode Obfuscation](bytecode-obfuscation.md): describes the scope of obfuscation capabilities (including default obfuscation features), obfuscation process, usage of various obfuscate and keep options, and strategies for merging obfuscation rules. It also discusses the limitations of ArkGuard in different language environments.

- [Using ArkGuard for Bytecode Obfuscation](bytecode-obfuscation-guide.md): offers step-by-step instructions on enabling bytecode obfuscation, setting custom obfuscation rules, and viewing obfuscation effects. It also explains how to perform stack trace deobfuscation in case of errors.

- [Package-specific Bytecode Obfuscation Recommendations](bytecode-obfuscation-practice.md): provides tailored obfuscation strategies for different package types, such as HAP, HAR, and HSP.

- [Common Issues with ArkGuard in Bytecode Obfuscation](bytecode-obfuscation-questions.md): describes the [differences between bytecode obfuscation and source code obfuscation](bytecode-obfuscation-questions.md#differences-between-bytecode-obfuscation-and-source-code-obfuscation), summarizes common issues encountered during obfuscation, along with troubleshooting methods and solutions for typical error cases. It aims to help you quickly identify and resolve problems that arise during obfuscation.
