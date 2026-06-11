# JSVM_EnvScope__*
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

```c
typedef struct JSVM_EnvScope__* JSVM_EnvScope
```

## 概述

表示用于控制附加到当前虚拟机实例的环境。只有当线程通过OH_JSVM_OpenEnvScope进入该环境的JSVM_EnvScope后，该环境才对线程的虚拟机实例可用。

**使用场景：** 在多线程环境下需要访问和操作JavaScript环境时，用于管理和切换环境作用域。

**解决的问题：** 解决多线程环境下对同一虚拟机实例的环境访问和隔离问题。

**带来的收益：** 为开发者提供线程安全的环境管理机制，确保多线程访问的正确性和隔离性。

**系统能力：** SystemCapability.ArkCompiler.JSVM

**起始版本：** 11

**相关模块：** [JSVM](capi-jsvm.md)

**所在头文件：** [jsvm_types.h](capi-jsvm-types-h.md)

