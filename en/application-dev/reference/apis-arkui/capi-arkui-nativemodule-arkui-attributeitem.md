# ArkUI_AttributeItem
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @piggyguy; @wangyang2022-->
<!--Designer: @piggyguy; @wangyang2022-->
<!--Tester: @fredyuan912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=1f9dad1f3e6c22cc389887f8092a3a1fbc7dc9a2 translatedAt=2026-09-18T11:24:23.095Z pushedAt=2026-09-20T07:47:57.563Z -->

```c
typedef struct {...} ArkUI_AttributeItem
```

## Overview

Defines the [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute) function. This is a general input parameter struct. Individual attribute-setting APIs can use appropriate member variables within it to store parameter data of specific types.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

## Summary

### Member Variables

| Name                                | Description|
|------------------------------------| -- |
| const [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md)* value | Pointer to the numeric array used to store attribute parameters of the numeric type. The array length is specified by **size**. |
| int32_t size                       | Length of the **value** array, which must be used together with the **value** variable. |
| const char* string                 | Pointer to the string used to store attribute parameters of the string type. |
| void* object                       | Pointer to the object data used to store attribute parameters of the object type. |
