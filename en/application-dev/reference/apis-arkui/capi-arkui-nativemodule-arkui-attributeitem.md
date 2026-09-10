# ArkUI_AttributeItem

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @piggyguy; @wangyang2022-->
<!--Designer: @piggyguy; @wangyang2022-->
<!--Tester: @fredyuan912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=e7bbac8df342a3329dc5f8c5db3d9883d3c9dda2 translatedAt=2026-08-19T04:16:42.846Z pushedAt=2026-08-19T06:56:33.951Z -->

```c
typedef struct {...} ArkUI_AttributeItem
```

## Overview

Defines the [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute) function. This is a general input parameter struct. Individual attribute-setting API can use appropriate member variables within it to store parameter data of specific types.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

## Summary

### Member Variables

| Name                                | Description|
| ---------------------------------- | --- |
| const [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md)* value | Pointer to the numeric array used to store attribute parameters of the numeric type. The array length is specified by **size**. |
| int32_t size                       | Length of the **value** array, which must be used together with the **value** variable.|
| const char* string                 | Pointer to the string used to store attribute parameters of the string type. |
| void* object                       | Pointer to the object data used to store attribute parameters of the object type. |