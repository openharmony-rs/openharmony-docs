# ArkUI_ColorStop
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct {...} ArkUI_ColorStop
```

## Overview

Defines a gradient color stop.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_type.h](capi-native-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| const uint32_t* colors | Pointer to the color array. The elements in this array correspond to the elements in the **stops** array in pairs, that is, each color corresponds to the position of a gradient stop. The array length must be the same as the value of **size**.|
| float* stops | Pointer to the color stop array. The value ranges from 0.0 to 1.0, indicating the position offset of a gradient stop. The array length must be the same as the value of **size**.|
| int size | Array length, that is, the actual number of elements in the **colors** or **stops** arrays.|
