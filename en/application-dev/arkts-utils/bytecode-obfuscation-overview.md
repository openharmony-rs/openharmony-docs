# Overview of ArkGuard for Bytecode Obfuscation
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @oatuwwutao; @Graceunderpressure-->
<!--Designer: @oatuwwutao-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=21434ce8d323ecbd7d67463989a2ef075be92cec translatedAt=2026-11-04T09:10:02.502Z pushedAt=2026-11-04T09:35:59.910Z nl=1 -->

Starting from API version 20, ArkGuard provides basic bytecode obfuscation capabilities, which turn names such as function names, class names, and file names in the code into short, meaningless names, making it harder to guess their purposes by reading the code. Since identifier names are shortened, obfuscation can effectively reduce the package size.

**Applicable scenarios**: suitable for projects with high requirements for **security and anti-reverse engineering**, especially applications involving **sensitive business logic**, key algorithms, or proprietary interface implementations. It is recommended to enable it as needed in release builds.

This section describes how to use ArkGuard. It aims to assist you in efficiently applying obfuscation to your bytecode, thereby increasing its complexity and making reverse engineering more challenging.

Compared with source code obfuscation, bytecode obfuscation targets bytecode files.

- [ArkGuard Principles and Capabilities for Bytecode Obfuscation](bytecode-obfuscation.md): describes the scope of obfuscation capabilities (including default obfuscation features), obfuscation process, usage of various obfuscate and keep options, and strategies for merging obfuscation rules. It also discusses the limitations of ArkGuard in different language environments.

- [Using ArkGuard for Bytecode Obfuscation](bytecode-obfuscation-guide.md): offers step-by-step instructions on enabling bytecode obfuscation, setting custom obfuscation rules, and viewing obfuscation effects. It also explains how to perform stack trace deobfuscation in case of errors.

- [Package-specific Bytecode Obfuscation Recommendations](bytecode-obfuscation-practice.md): provides tailored obfuscation strategies for different package types, such as HAP, HAR, and HSP.

- [Common Issues with ArkGuard in Bytecode Obfuscation](bytecode-obfuscation-questions.md): describes the [differences between bytecode obfuscation and source code obfuscation](bytecode-obfuscation-questions.md#differences-between-bytecode-obfuscation-and-source-code-obfuscation), summarizes common issues encountered during obfuscation, along with troubleshooting methods and solutions for typical error cases. It aims to help you quickly identify and resolve problems that arise during obfuscation.
