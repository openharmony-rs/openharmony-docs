# ArkUI_AttributeItem
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @piggyguy; @xiang-shouxing; @yangfan229-->
<!--Designer: @piggyguy; @xiang-shouxing; @yangfan229-->
<!--Tester: @fredyuan912-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct {...} ArkUI_AttributeItem
```

## Overview

Defines the general input parameter structure of the [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute) function. Individual attribute-setting API can use appropriate member variables within it to store parameter data of specific types.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

## Summary

### Member Variables

| Name                                | Description|
|------------------------------------| -- |
| const [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md)* value | Numeric array, used to store parameters of the numeric array type.|
| int32_t size                       | Size of the numeric array. Used in conjunction with the **value** variable, it indicates the length of the **value** array.|
| const char* string                 | String, used to store parameters of the string type.|
| void* object                       | Object pointer, used to store parameters of the object type.|
