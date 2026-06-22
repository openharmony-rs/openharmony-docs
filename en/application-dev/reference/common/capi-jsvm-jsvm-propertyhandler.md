# JSVM_PropertyHandler

<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=93671cc034f483d1b8e032e6aa319b90dbbd1186 translatedAt=2026-06-18T08:22:01.359Z pushedAt=2026-06-22T03:21:12.880Z -->

```c
typedef struct {...} JSVM_PropertyHandler
```

## Overview

Defines the pointer to the callback function triggered when a class is called as a function, and the pointer collection of the callback function triggered when an instance object property is accessed.

**Use scenario**: Intercepting and customizing the function call behavior of objects to enable custom logic for property access.

**Features**: Triggering custom callbacks when an instance object is called as a function; triggering the corresponding callback function when instance object properties are accessed.

**Problems solved**: Implementing the proxy pattern for objects and customizing function call behavior. Providing an interception mechanism for property access to enhance code flexibility and extensibility.

**System capability:** SystemCapability.ArkCompiler.JSVM

**Since**: 18

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member Variables

| Name                                                                                                 | Description|
|-----------------------------------------------------------------------------------------------------| -- |
| [JSVM_PropertyHandlerCfg](capi-jsvm-jsvm-propertyhandlerconfigurationstruct8h.md) propertyHandlerCfg | Callback triggered when an instance object property is accessed.|
| [JSVM_Callback](capi-jsvm-jsvm-callbackstruct8h.md) callAsFunctionCallback                                                            | Callback triggered when an instance object is called as a function.|