# JSVM_PropertyDescriptor
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou; @string_sz-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

```c
typedef struct {...} JSVM_PropertyDescriptor
```

## Overview

Defines property descriptor.

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| const char* utf8name | Property key, which is an optional string in UTF-8 encoding. Either **utf8name** or **name** must be provided for a property.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) name | Optional JSVM value, which points to the JavaScript string or symbol used as the property key. Either **utf8name** or **name** must be provided for a property.|
| [JSVM_Callback](capi-jsvm-jsvm-callbackstruct8h.md) method | Method represented using the **value** property of the property descriptor object.|
| [JSVM_Callback](capi-jsvm-jsvm-callbackstruct8h.md) getter | Callback used to obtain a property.|
| [JSVM_Callback](capi-jsvm-jsvm-callbackstruct8h.md) setter | Callback used to set a property.|
| [JSVM_Value](capi-jsvm-jsvm-value--8h.md) value | Value retrieved by **getter** of the data property.|
| [JSVM_PropertyAttributes](capi-jsvm-types-h.md#jsvm_propertyattributes) attributes | Attributes associated with a specific property.|
