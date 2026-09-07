# JSVM_HandleScope__*

<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=21434ce8d323ecbd7d67463989a2ef075be92cec translatedAt=2026-08-27T03:48:37.296Z pushedAt=2026-08-27T06:39:17.713Z -->

```c
typedef struct JSVM_HandleScope__* JSVM_HandleScope
```

## Overview

Defines the scope of the JavaScript value. It is used to control and modify the lifecycle of an object created in a specific scope. Typically, the JSVM-API value is created in the context of **JSVM_HandleScope**. When the native method is called from JavaScript, the default **JSVM_HandleScope** exists. If the user does not explicitly create a new **JSVM_HandleScope**, the JSVM-API value is created in the default **JSVM_HandleScope**. For any code call other than native method execution (for example, libuv callback), the module needs to create a scope before calling any function that may create a JavaScript value. **JSVM_HandleScope** is created using **OH_JSVM_OpenHandleScope** and destroyed using **OH_JSVM_CloseHandleScope**. Closing the scope indicates to the GC that all **JSVM_Values** created during the lifecycle of **JSVM_HandleScope** will no longer be referenced from the stack frame of the current heap.

**Paired calls:** **OH_JSVM_OpenHandleScope()** and **OH_JSVM_CloseHandleScope()** must be called in pairs. After each call to **OH_JSVM_OpenHandleScope()**, **OH_JSVM_CloseHandleScope()** must be called to release resources when they are no longer needed.

**Consequences of violation:** If you forget to call **OH_JSVM_CloseHandleScope()**, memory leaks and unreleased resources will occur.

**Usage scenario:** This scope is used to create JSVM-API values in native methods, call functions that may create JavaScript values during the execution of non-native methods such as libuv callbacks, and precisely control the lifecycle of JavaScript objects.

**Benefits:** Avoid memory leaks: manage the object lifecycle through scopes to prevent unnecessary memory usage. Improve GC efficiency: explicitly indicate to the GC which objects can be reclaimed, reducing garbage collection overhead.

**System capability:** SystemCapability.ArkCompiler.JSVM

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)