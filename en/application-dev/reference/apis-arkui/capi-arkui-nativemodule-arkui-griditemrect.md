# ArkUI_GridItemRect

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @guozejun; @rongShao-Z-->
<!--Designer: @guozejun-->
<!--Tester: @leiyuqian-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct {...} ArkUI_GridItemRect
```

## Overview

Defines the return value for the [OH_ArkUI_GridLayoutOptions_RegisterGetRectByIndexCallback](capi-grid-h.md#oh_arkui_gridlayoutoptions_registergetrectbyindexcallback) callback in **Grid** layout options, which is used to specify the start row, start column, row span, and column span for the grid item in **Grid** at the specified index.

**Since**: 22

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [grid.h](capi-grid-h.md)

**Sample**: <!--RP1-->[native_type_sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeType/native_type_sample)<!--RP1End-->

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t rowStart | Start row of a grid item in **Grid**, which is counted from 0.|
| uint32_t columnStart | Start column of a grid item in **Grid**, which is counted from 0.|
| uint32_t rowSpan | Number of rows occupied by a grid item.|
| uint32_t columnSpan | Number of columns occupied by a grid item.|
