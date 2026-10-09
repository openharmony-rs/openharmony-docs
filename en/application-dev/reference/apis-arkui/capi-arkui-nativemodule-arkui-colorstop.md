# ArkUI_ColorStop

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=39ca26def5c22dc659f3dc0b76ef62a29421e77a translatedAt=2026-08-19T04:17:03.357Z pushedAt=2026-08-19T07:03:11.293Z -->

```c
typedef struct {...} ArkUI_ColorStop
```

## Overview

Defines a gradient color stop, which is used to configure the gradient effect of a component. It supports defining various gradient styles by combining a color array with a stop array.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_type.h](capi-native-type-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| const uint32_t* colors | Pointer to the color array. The elements in this array correspond to the elements in the **stops** array by index, that is, each color corresponds to the position of a gradient stop. The array length must be the same as the value of **size**. |
| float* stops | Pointer to the stop array. The elements in this array correspond to the elements in the **colors** array in pairs. The value ranges from 0.0 to 1.0, indicating the position offset of the gradient color. The array length must be the same as the value of **size**. If a value less than 0 is set, it is automatically corrected to 0. |
| int size | Array length, which must be the same as the actual number of elements in the **colors** and **stops** arrays. Before setting this value, determine the actual number of elements in the **colors** and **stops** arrays. |