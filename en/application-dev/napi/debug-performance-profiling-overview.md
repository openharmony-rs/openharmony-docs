# Overview
<!--Kit: Common-->
<!--Subsystem: Common-->
<!--Owner: @fang-jinxu-->
<!--Designer: @lingminghw-->
<!--Tester: @RayShih-->
<!--Adviser: @fang-jinxu-->

When building C/C++ projects with the NDK, you may encounter exceptions and performance issues common with native projects. To help you locate these issues, the NDK provides some popular debugging and profiling tools.

- The following methods are provided for debugging and profiling:

  - [C/C++ memory error detection](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-asan)
  - Debugging in DevEco Studio
    - [1. C/C++ reverse debugging](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-debug-native-reverse)
    - [2. Debugging on a real device](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-debug-device)
    > **NOTE**
    >
    > When [debugging on a real device](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-debug-device), if the .so file's source code path on the local compilation device does not match the configured C++ source code path, see [Debugging Third-Party Library Source Code](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-source-code-debugging).
