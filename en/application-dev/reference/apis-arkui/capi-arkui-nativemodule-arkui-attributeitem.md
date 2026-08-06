# ArkUI_AttributeItem
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @piggyguy; @wangyang2022-->
<!--Designer: @piggyguy; @wangyang2022-->
<!--Tester: @fredyuan912-->
<!--Adviser: @Brilliantry_Rui-->

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
| const [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md)* value | Pointer to the numeric type array, used to store parameters of the numeric array type. The array length is specified by **size**.|
| int32_t size                       | Length of the **value** array, which must be used together with the **value** variable.|
| const char* string                 | String pointer, used to store parameters of the string type.|
| void* object                       | Object pointer, used to store parameters of the object type.|
