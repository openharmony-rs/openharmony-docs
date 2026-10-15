# ArkUI_AttributeItem

```c
typedef struct ArkUI_AttributeItem {...} ArkUI_AttributeItem
```

## Overview

Defines the [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute) function. This is a general input parameter struct. Individual attribute-setting API can use appropriate member variables within it to store parameter data of specific types.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [common_type.h](capi-common-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [const ArkUI_NumberValue*](capi-arkui-nativemodule-arkui-numbervalue.md) value | Pointer to the numeric array used to store attribute parameters of the numeric type. The array length is specified by **size**.<br>**Since**: 12 |
| int32_t size | Length of the **value** array, which must be used together with the **value** variable.<br>**Since**: 12 |
| const char* string | Pointer to the string used to store attribute parameters of the string type.<br>**Since**: 12 |
| void* object | Pointer to the object data used to store attribute parameters of the object type.<br>**Since**: 12 |


