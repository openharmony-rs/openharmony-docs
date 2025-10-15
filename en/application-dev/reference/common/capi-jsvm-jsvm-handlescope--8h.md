# JSVM_HandleScope__*
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou; @string_sz-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

## Overview

Scope of the JavaScript value. It is used to control and modify the lifecycle of an object created in a specific scope. Typically, the JSVM-API value is created in the context of JSVM_HandleScope. When a native method is called from JavaScript, there is a default JSVM_HandleScope. If you do not explicitly create a new JSVM_HandleScope, JSVM-API values are created in the default JSVM_HandleScope. For any code call outside the execution of the native method (for example, during the libuv callback call), the module needs to create a scope before calling any function that may create JavaScript values. JSVM_HandleScope is created using OH_JSVM_OpenHandleScope and destroyed using OH_JSVM_CloseHandleScope. Closing the scope represents indicating to the GC that all JSVM_Values created during the lifecycle of JSVM_HandleScope will no longer be referenced from the stack frame of the current heap.

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)
