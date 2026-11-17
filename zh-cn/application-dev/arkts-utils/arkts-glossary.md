---
kits: ["ArkTS Kit / 方舟编程语言"]
description: "ArkTS术语表汇总并解释ArkTS开发中的核心术语，包括方舟字节码（abc产物）、ArkGuard代码混淆器、ASON序列化工具、es2abc编译器及Sendable可共享对象机制等概念定义，帮助开发者准确理解ArkTS技术体系中各关键名词的内涵与用途。"
keywords: [ArkTS术语, 方舟字节码, ArkGuard, ASON, es2abc, Sendable, 代码混淆, 序列化反序列化, 并发共享对象]
doctype: glossary
status: active
---

# ArkTS术语
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @vigavi-->
<!--Designer: @vigavi-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->

## A

### Ark Bytecode；方舟字节码

ArkTS/TS/JS源码经编译工具链编译后生成的二进制产物，文件后缀为.abc，由ArkTS运行时在设备侧加载执行。

### ArkGuard

ArkGuard是ArkTS编译工具链中的代码混淆器，支持源码混淆与字节码混淆两种模式。它将ArkTS/TS/JS代码转换成功能上等价但难于阅读和理解的形式，增加逆向分析难度。

### ASON

ArkTS提供的Sendable对象序列化与反序列化工具，功能类似于JSON对JS对象的处理，支持JSON字符串与Sendable对象的互相转换，生成的Sendable对象可以在并发任务间高性能传递。

## E

### es2abc

ArkTS源码到ArkTS字节码（abc文件）的编译器。负责将ArkTS源代码编译生成方舟字节码，是ArkCompiler编译工具链的核心组件之一。

## S

### Sendable

ArkTS提出的一种可共享对象机制，支持对象在并发实例间通过引用传递进行高效共享，避免传统结构化克隆的深拷贝开销。