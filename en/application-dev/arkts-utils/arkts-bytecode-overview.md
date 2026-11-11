---
kits: ["ArkTS Kit"]
description: "Provides an overview of Ark Bytecode as the binary artifact compiled from ArkTS/TS/JS, and indexes subtopics such as the bytecode file format, basic principles, function naming rules, and compile-time custom modification to help developers quickly get started with bytecode learning."
keywords: [Ark Bytecode, bytecode overview, bytecode file format, bytecode basic principles, function naming rules, compile-time bytecode modification, abc]
doctype: guide
status: active
---

# Overview of Ark Bytecode

<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @jokerxd-liu-->
<!--Designer: @huyunhui1; @zmw1; @oatuwwutao-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=f2cb5494a82278dc546d60569b7e6ff61b7065a7 translatedAt=2026-11-06T10:14:06.191Z pushedAt=2026-11-09T08:47:37.852Z nl=1 -->

The Ark bytecode file is a binary output generated from compiling ArkTS/TS/JS source code. This topic describes the Ark bytecode file format, helping you understand the structure and content of Ark bytecode files, thereby effectively analyzing and modifying bytecode.

- [ArkByte Bytecode File Format](arkts-bytecode-file-format.md): Describes the structural information of each part contained in the bytecode file, as well as the storage methods and mapping relationships of various structures.

- [ArkByte Bytecode Fundamentals](arkts-bytecode-fundamentals.md): Describes the important concepts that constitute instructions in bytecode, as well as the specific instruction formats and meanings, helping developers understand ArkByte bytecode instructions and perform feature development related to instructions.

- [ArkByte Function Naming Rules](arkts-bytecode-function-name.md): Describes the naming rules for function name strings in the bytecode file.

- [Customizing ArkByte Bytecode at Compile Time](customize-bytecode-during-compilation.md): Describes how to modify the content of the bytecode file.
