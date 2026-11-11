---
kits: ["ArkTS Kit"]
description: "Introduces the basic concepts, components, and use cases of OpenMP (Open Multi-Processing), a cross-platform API for multithreaded concurrent programming with shared memory. Covers scenarios such as scientific computing, image processing, and machine learning, and explains that the OpenHarmony OpenMP library uses the implementation in llvm 15.0.4."
keywords: ["OpenMP", "multithreaded concurrency", "shared memory", "parallel programming", "pragma directives", "llvm", "multicore parallelism", "compute-intensive", "data parallelism"]
doctype: guide
status: active
---


# OpenMP Overview

<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @da_wei_li11-->
<!--Designer: @liyiming13-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=235c2cef2c01aded2d0dcd8f4c12337fcc18fc53 translatedAt=2026-11-09T08:52:17.317Z nl=1 -->

[Open Multi-Processing (OpenMP)](https://www.openmp.org/) provides a set of APIs that support multi-platform shared memory multiprocessing programming. It consists of a set of compiler directives, library routines, and environment variables that influence runtime behavior. It provides high-level abstract description of parallel algorithms, making it suitable for developing parallel applications on multi-core processor devices. Based on the **pragma** directives added to the application, the compiler automatically processes the application segments in parallel. Using OpenMP can reduce the complexity of parallel programming.

## When to Use

OpenMP has been widely used in scientific computing, image processing, machine learning, financial computing, bioinformatics and other high-performance computing fields. It is particularly suitable for computing-intensive tasks and addressing data parallelism issues. By simplifying the development process of multi-core parallelization, OpenMP helps efficiently utilize the multi-core resources of modern processors and addresses traditional parallel programming challenges, such as complex thread management, uneven task loads, and performance bottlenecks. With the flexible scheduling mechanism and cross-platform support of OpenMP, applications can significantly enhance performance while maintaining code simplicity and portability. OpenMP is a crucial tool for improving both the development and computing efficiency.

## Version Description

Currently, OpenHarmony uses the OpenMP library implemented in [llvm 15.0.4](https://github.com/llvm/llvm-project/releases/tag/llvmorg-15.0.4). For details about the corresponding OpenMP API version, see [clang-OpenMPSupport](https://clang.llvm.org/docs/OpenMPSupport.html).

For details about how to use OpenMP in OpenHarmony apps, see [Building and Running Applications Using OpenMP](./openmp-guideline.md).
