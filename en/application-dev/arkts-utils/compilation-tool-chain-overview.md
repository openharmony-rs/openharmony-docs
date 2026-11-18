---
kits: ["ArkTS / Ark Programming Language"]
description: "The ArkTS compilation toolchain compiles application source code into Ark bytecode, covering syntax check, UI transformation, source code obfuscation, custom bytecode modification, and disassembly, helping developers understand the HAP build process."
keywords: [ArkTS, Hvigor, syntax check, UI transformation, ArkGuard source code obfuscation, Ark bytecode, custom bytecode modification, Disassembler disassembly, HAP build]
doctype: guide
status: active
---

# Overview of the ArkTS Compilation Toolchain
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @luchenxu; @calyx1111-->
<!--Designer: @luchenxu; @calyx1111-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=3983c2e63ae5991b63a2e4ecd06ac86253005522 translatedAt=2026-11-06T10:27:51.050Z pushedAt=2026-11-12T02:46:08.106Z nl=1 -->

The ArkTS SDK provides a comprehensive toolchain for compiling ArkTS applications. Integrated with the [Hvigor](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-hvigor) task orchestration tool, this toolchain compiles ArkTS/TS/JS source code into Ark bytecode files (*.abc).

During compilation, the toolchain first performs syntax transformation, including syntax checking and UI transformation. To ensure source code security, it uses [ArkGuard](source-obfuscation.md) for source code obfuscation. Before the bytecode is written to disk, the toolchain checks whether [custom bytecode modifications](customize-bytecode-during-compilation.md) are required. If modifications are required, custom modification code is loaded and executed. After generating the bytecode file, the [Disassembler](tool-disassembler.md) tool is used to inspect the file content. For details about the bytecode, see [Ark Bytecode File Format](arkts-bytecode-file-format.md).

The ArkTS compiler toolchain currently provides the following features:

1. Syntax check: checks whether the ArkTS/TS syntax is correct.

2. UI transformation: converts UI declarative paradigm syntax to standard TS syntax.

3. Source code obfuscation: uses the ArkGuard tool to obfuscate the source code. You can enable this feature based on service requirements.

4. Generate the Ark bytecode file: uses the Ark compiler to generate the Ark bytecode file (\*.abc).

5. Custom bytecode modification: provides an entry for you to modify bytecode before it is written to disk.

6. Disassembly: uses the Disassembler tool to disassemble the Ark bytecode file into readable assembly instructions.

The process of the ArkTS compilation toolchain participating in HAP build is shown in the following figure:

![compilation-tool-overview](figures/compilation-tool-overview.png)

