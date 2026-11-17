---
kits: ["ArkTS Kit"]
description: "Provides an overview of the basic capabilities and value of the ArkGuard source code obfuscation tool, which replaces variable names, function names, class names, and other identifiers with short identifiers. It also indexes subtopics such as obfuscation principles, configuration options, and keep options."
keywords: [ArkGuard, obfuscation, source code obfuscation, obfuscation overview, reverse engineering, identifier, package size]
doctype: guide
status: active
---

# Overview of ArkGuard for Source Code Obfuscation
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @oatuwwutao-->
<!--Designer: @oatuwwutao-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=17ae88719a2d37a0c07e3b6e33ddb120ebd3dbc5 translatedAt=2026-11-06T10:46:06.908Z pushedAt=2026-11-12T11:49:42.514Z nl=1 -->

ArkGuard is a source code obfuscation tool that converts variable, function, class, and file names into short, meaningless identifiers. This makes it harder to deduce code purposes through inspection. Additionally, the shortened names in obfuscated code help reduce package size.

This section describes how to use ArkGuard for source code obfuscation. It aims to assist you in efficiently applying obfuscation to your source code, thereby increasing its complexity and making reverse engineering more challenging.

- [ArkGuard Obfuscation Principles](./source-obfuscation.md): describes the scope of obfuscation capabilities, the obfuscation process mechanism, and the merging strategy for obfuscation rules.

- [ArkGuard Obfuscation Configuration Options](./source-obfuscation-rule-options.md): describes the purpose and usage of obfuscation configuration options.

- [ArkGuard Obfuscation Keep Options](./source-obfuscation-keep-options.md): describes the purpose and usage of obfuscation keep options.

- [Using ArkGuard for Source Code Obfuscation](./source-obfuscation-guide.md): offers step-by-step instructions on enabling source code obfuscation, setting custom obfuscation rules, and viewing obfuscation effects. It also explains how to perform stack trace deobfuscation in case of errors.

- [ArkGuard Obfuscation Practice Guide](./source-obfuscation-apply-code.md): introduces the purpose of source code obfuscation, the basic conditions for enabling obfuscation, HAR package build methods, an overview of obfuscation options, viewing obfuscation results, and using third-party hardening services.

- [Package-specific Source Code Obfuscation Recommendations](./source-obfuscation-practice.md): provides tailored obfuscation strategies for different package types, such as HAP, HAR, and HSP.

- [ArkGuard Obfuscation FAQ](./source-obfuscation-questions.md): summarizes common functional exception scenarios and their troubleshooting methods, and provides solutions for typical error cases to help developers quickly locate and resolve issues.
