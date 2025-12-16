# JSVM_HandleScope__*
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou; @string_sz-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

```c
typedef struct JSVM_HandleScope__* JSVM_HandleScope
```

## Overview

Defines the scope of the JavaScript value. It is used to control and modify the lifecycle of an object created in a specific scope. Typically, the JSVM-API value is created in the context of **JSVM_HandleScope**. When the native method is called from JavaScript, the default **JSVM_HandleScope** exists. If the user does not explicitly create a new **JSVM_HandleScope**, the JSVM-API value is created in the default **JSVM_HandleScope**. For any code call other than native method execution (for example, libuv callback), the module needs to create a scope before calling any function that may create a JavaScript value. **JSVM_HandleScope** is created using **OH_JSVM_OpenHandleScope** and destroyed using **OH_JSVM_CloseHandleScope**. Closing the scope indicates to the GC that all **JSVM_Values** created during the lifecycle of **JSVM_HandleScope** will no longer be referenced from the stack frame of the current heap.

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)
