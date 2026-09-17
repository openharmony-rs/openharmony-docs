# JSVM_PropertyHandler

<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=21434ce8d323ecbd7d67463989a2ef075be92cec translatedAt=2026-08-27T03:48:59.179Z pushedAt=2026-08-27T06:43:47.511Z -->

```c
typedef struct {...} JSVM_PropertyHandler
```

## Overview

Defines the pointer to the callback function triggered when a class is called as a function, and the pointer collection of the callback function triggered when an instance object property is accessed.

**Use scenario:** Used to intercept and customize the function call behavior of an object, and to implement custom logic for property access.

**Features:** Supports triggering a custom callback when an instance object is called as a function, and triggering the corresponding callback function when an instance object property is accessed.

**Problems solved:** Implements the proxy pattern for objects and customizes the function call behavior. Provides an interception mechanism for property access, enhancing code flexibility and extensibility.

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