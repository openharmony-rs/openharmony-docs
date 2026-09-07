# JSVM_CallbackInfo__*

<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=21434ce8d323ecbd7d67463989a2ef075be92cec translatedAt=2026-08-27T03:46:54.294Z pushedAt=2026-08-27T06:19:26.517Z -->

```c
typedef struct JSVM_CallbackInfo__* JSVM_CallbackInfo
```

## Overview

Defines an opaque data type passed to the callback. It can be used to obtain additional information about the context in which the function is called.

**Use scenario**: This type is used when a JavaScript callback function needs to be implemented in Native API development. For example, after a callback function is registered in the JSVM module, this type is used to obtain the parameter information and execution context of the callback invocation.

**Problem solved**: Provides the native layer with the capability to access the invocation context of JavaScript callback functions, solving the problem that native code cannot obtain the parameters and execution environment of callback functions.

**Benefits**: Simplifies the interaction between the native layer and the JavaScript layer, allowing developers to flexibly access and process parameters passed from JavaScript in native callback functions, thereby improving the flexibility and development efficiency of native-JavaScript interoperability.

**System capability:** SystemCapability.ArkCompiler.JSVM

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)