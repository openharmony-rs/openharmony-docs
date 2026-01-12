# JSVM_EnvScope__*
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou; @string_sz-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

```c
typedef struct JSVM_EnvScope__* JSVM_EnvScope
```

## Overview

Defines the environment scope of the current VM instance. The environment is available to the VM instance of the thread only after the thread enters **JSVM_EnvScope** of the environment through **OH_JSVM_OpenEnvScope**.

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)
