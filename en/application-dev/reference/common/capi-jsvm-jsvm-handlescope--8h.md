# JSVM_HandleScope__*

<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=93671cc034f483d1b8e032e6aa319b90dbbd1186 translatedAt=2026-06-18T08:21:44.228Z pushedAt=2026-06-22T06:06:49.691Z -->

```c
typedef struct JSVM_HandleScope__* JSVM_HandleScope
```

## Overview

Defines the scope of the JavaScript value. It is used to control and modify the lifecycle of an object created in a specific scope. Typically, the JSVM-API value is created in the context of **JSVM_HandleScope**. When the native method is called from JavaScript, the default **JSVM_HandleScope** exists. If the user does not explicitly create a new **JSVM_HandleScope**, the JSVM-API value is created in the default **JSVM_HandleScope**. For any code call other than native method execution (for example, libuv callback), the module needs to create a scope before calling any function that may create a JavaScript value. **JSVM_HandleScope** is created using **OH_JSVM_OpenHandleScope** and destroyed using **OH_JSVM_CloseHandleScope**. Closing the scope indicates to the GC that all **JSVM_Values** created during the lifecycle of **JSVM_HandleScope** will no longer be referenced from the stack frame of the current heap.

**Paired calls:** **OH_JSVM_OpenHandleScope()** and **OH_JSVM_CloseHandleScope()** must be called in pairs. After each call to **OH_JSVM_OpenHandleScope()**, **OH_JSVM_CloseHandleScope()** must be called to release resources when they are no longer needed.

**Consequence of violation:** Forgetting to call **OH_JSVM_CloseHandleScope()** will cause memory leaks and prevent resources from being released.

**Use scenario:** Creating JSVM-API values in native methods; calling functions that may create JavaScript values during non-native method execution such as libuv callbacks; precisely controlling the lifecycle of JavaScript objects.

**Benefits:** Avoiding memory leaks: managing object lifecycles through scopes to prevent unnecessary memory usage. Improving GC efficiency: explicitly indicating to the GC which objects can be reclaimed, reducing garbage collection overhead.

**System capability:** SystemCapability.ArkCompiler.JSVM

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)