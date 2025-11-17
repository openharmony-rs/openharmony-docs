# JSVM_PropertyHandler
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou; @string_sz-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

## Overview

Defines the pointer to the callback function triggered when a class is called as a function, and the pointer collection of the callback function triggered when an instance object property is accessed.

**Since**: 18

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member Variables

| Name                                                                                                 | Description|
|-----------------------------------------------------------------------------------------------------| -- |
| [JSVM_PropertyHandlerCfg](capi-jsvm-jsvm-propertyhandlerconfigurationstruct8h.md) propertyHandlerCfg | Callback triggered when an instance object property is accessed.|
| [JSVM_Callback](capi-jsvm-jsvm-callbackstruct8h.md) callAsFunctionCallback                                                            | Callback triggered when an instance object is called as a function.|
