---
kits: ["ArkTS Kit / ArkTS Programming Language"]
description: "The ArkTS glossary summarizes and explains the core terms in ArkTS development, including definitions of concepts such as Ark Bytecode (abc artifacts), the ArkGuard code obfuscator, the ASON serialization tool, the es2abc compiler, and the Sendable shareable object mechanism, helping developers accurately understand the meaning and purpose of key terms in the ArkTS technology system."
keywords: [ArkTS terminology, Ark Bytecode, ArkGuard, ASON, es2abc, Sendable, code obfuscation, serialization and deserialization, concurrent shareable objects]
doctype: glossary
status: active
---

# ArkTS Terminology
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @vigavi-->
<!--Designer: @vigavi-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=8ab04f8e381777d336655e9a107b766140969d50 translatedAt=2026-11-06T10:16:55.068Z pushedAt=2026-11-09T09:02:37.195Z nl=1 -->

## A

### Ark Bytecode

The binary product generated after ArkTS/TS/JS source code is compiled by the compilation toolchain. The file extension is .abc, and it is loaded and executed by the ArkTS runtime on the device side.

### ArkGuard

ArkGuard is a code obfuscator in the ArkTS compilation toolchain, supporting both source code obfuscation and bytecode obfuscation modes. It transforms ArkTS/TS/JS code into a functionally equivalent but difficult-to-read-and-understand form, increasing the difficulty of reverse engineering.

### ASON

A serialization and deserialization tool for Sendable objects provided by ArkTS. Its functionality is similar to how JSON handles JS objects, supporting mutual conversion between JSON strings and Sendable objects. The generated Sendable objects can be passed between concurrent tasks with high performance.

## E

### es2abc

The compiler that compiles ArkTS source code into ArkTS bytecode (abc files). It is responsible for compiling ArkTS source code into Ark Bytecode and is one of the core components of the ArkCompiler compilation toolchain.

## S

### Sendable

A shareable object mechanism proposed by ArkTS that supports efficient sharing of objects between concurrent instances through reference passing, avoiding the deep copy overhead of traditional structured cloning.