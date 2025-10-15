# JSVM_PropertyDescriptor
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou; @string_sz-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

## Overview

Property descriptor.

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| const char* utf8name | An optional string that describes the attribute key value, encoded in UTF-8. Either **utf8name** or **name** must be provided for a property.|
| JSVM_Value name | Optional JSVM_Value, which points to the JavaScript string or symbol used as the property key. Either **utf8name** or **name** must be provided for a property.|
| JSVM_Callback method | Method as the **value** property of the property descriptor object.|
| JSVM_Callback getter | Callback for getting a property.|
| JSVM_Callback setter | Callback for setting a property.|
| JSVM_Value value | Value retrieved by **getter** of the data property.|
| JSVM_PropertyAttributes attributes | Attributes associated with a specific property.|
