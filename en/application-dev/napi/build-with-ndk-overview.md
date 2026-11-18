---
kits: ["ArkTS Kit"]
description: "Provides an overview of the OpenHarmony NDK build system. Describes common configuration parameters in ohos.toolchain.cmake (OHOS_STL, OHOS_ARCH, and OHOS_PLATFORM), their effects on Clang cross-compilation commands, and the basic concepts of building from source and using prebuilt libraries."
keywords: ["NDK project builds", "ohos.toolchain.cmake", "OHOS_STL", "OHOS_ARCH", "OHOS_PLATFORM", "cross-compilation", "CMake", "prebuilt libraries", "libc++_shared"]
doctype: guide
status: active
---

# Overview

<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @liyiming13-->
<!--Designer: @liyiming13-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=235c2cef2c01aded2d0dcd8f4c12337fcc18fc53 translatedAt=2026-11-09T08:52:17.284Z nl=1 -->

OpenHarmony NDK uses CMake as the default build system. The NDK package includes the base configuration file <!--RP2-->ohos.toolchain.cmake<!--RP2End-->, which is compliant with the OpenHarmony toolchain and predefines CMake variables to simplify your configuration.

Common NDK project build methods include:

- Building from source

  There are different ways to build from source:

  - Use the C++ app template provided by DevEco Studio and [compile and build with DevEco Studio](build-with-ndk-ide.md)

  - [Compile and build using command-line CMake](build-with-ndk-cmake.md)

- [Build with prebuilt libraries](build-with-ndk-prebuilts.md)

This section uses specific examples to describe how to use the NDK in a native project and how to write CMake scripts to build an NDK project.

<!--RP1-->

## Introduction to ohos.toolchain.cmake

`ohos.toolchain.cmake` is a toolchain script provided by OpenHarmony NDK for CMake. It predefines the compilation parameters required for building OpenHarmony apps, such as the cross-compilation target device and the linking mode of the C++ runtime library. When invoking CMake commands, you can pass these parameters from the command line to change the default compilation and linking behavior. The following table lists the commonly used parameters in this file.

| Name | Type | Description |
| -------- | -------- | -------- |
| OHOS_STL | c++_shared/c++_static | Linking mode of `libc++`. The default value is `c++_shared`.<br/>`c++_shared`: dynamically links `libc++_shared.so`. `c++_static`: statically links `libc++_static.a`.<br/>Because global variables exist in the C++ runtime, all native libraries in the same app must use the same linking mode. |
| OHOS_ARCH | armeabi-v7a/arm64-v8a/x86_64 | Target architecture for native cross-compilation. Supported architectures are armeabi-v7a, arm64-v8a, and x86_64. |
| OHOS_PLATFORM | OHOS | Platform. Currently, only the OpenHarmony platform is supported. |

These parameters ultimately control Clang's cross-compilation commands and generate appropriate command arguments.

- `--target={arch}-linux-ohos`: instructs the compiler to generate binary files that conform to the OpenHarmony ABI for the corresponding architecture.

- `--sysroot={ndk_root}/sysroot`: notifies the compiler of the location of the OpenHarmony header files.

<!--RP1End-->
