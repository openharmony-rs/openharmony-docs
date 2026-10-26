---
kits: ["ArkTS Kit / 方舟编程语言"]
description: "介绍OpenMP（Open Multi-Processing）跨平台共享内存多线程并发编程API的基本概念、组成结构和适用场景（科学计算、图像处理、机器学习等），说明OpenHarmony中OpenMP库基于llvm 15.0.4实现，帮助开发者了解OpenMP并行编程的基础知识。"
keywords: [OpenMP, 多线程并发, 共享内存, 并行编程, pragma指令, llvm, 多核并行, 计算密集型, 数据并行]
doctype: guide
status: active
---


# OpenMP简介
<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @da_wei_li11-->
<!--Designer: @liyiming13-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->

[OpenMP（Open Multi-Processing）](https://www.openmp.org/)是一套支持跨平台共享内存方式的多线程并发的编程API，由一套编译器指令、库和一些能够影响运行行为的环境变量构成，提供了对并行算法的高层抽象描述，适合在多核CPU机器上的并行程序设计。编译器根据程序中添加的pragma指令，自动将pragma指令标记的程序片段并行处理，使用OpenMP可以降低并行编程的复杂度。

## 使用场景

OpenMP广泛应用于科学计算、图像处理、机器学习、金融计算、生物信息学等需要高性能计算的领域，尤其适合解决计算密集型任务和数据并行问题。它通过简化多核并行化的开发流程，帮助开发者高效利用现代处理器的多核资源，解决了传统并行编程中线程管理复杂、任务负载不均、性能瓶颈等问题。借助OpenMP的灵活调度机制和跨平台支持，程序能够显著提升性能，同时保持代码的简洁性和可移植性，是提高开发效率和计算效率的关键工具。

## 版本说明

当前OpenHarmony中的OpenMP库采用[llvm 15.0.4](https://github.com/llvm/llvm-project/releases/tag/llvmorg-15.0.4)中的实现，对应OpenMP API版本请参考[clang-OpenMPSupport](https://clang.llvm.org/docs/OpenMPSupport.html)。

OpenHarmony应用中使用OpenMP请参考[OpenMP应用构建和运行指南](./openmp-guideline.md)。
