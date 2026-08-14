# ArkUI_GridItemSize

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @guozejun; @rongShao-Z-->
<!--Designer: @guozejun-->
<!--Tester: @leiyuqian-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=f8ecdb82f3ec053eb7dde21e27a6f047d194898a translatedAt=2026-07-17T09:24:27.353Z pushedAt=2026-07-17T10:59:45.626Z -->

```c
typedef struct {...} ArkUI_GridItemSize
```

## Overview

Defines the return value for the [OH_ArkUI_GridLayoutOptions_RegisterGetIrregularSizeByIndexCallback](capi-grid-h.md#oh_arkui_gridlayoutoptions_registergetirregularsizebyindexcallback) callback in **Grid** layout options, which is used to specify the row span and column span for an irregular grid item at the specified index.

**Since**: 22

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [grid.h](capi-grid-h.md)

**Sample**: <!--RP1-->[native_type_sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeType/native_type_sample)<!--RP1End-->

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t rowSpan | Number of rows occupied by a grid item, which is used to set the span of the grid item in the row direction. Value range: [1, +∞). If set to **0**, the value **1** is used. In a horizontal grid layout, if the value exceeds the actual number of rows, the actual number of rows is used. |
| uint32_t columnSpan | Number of columns occupied by a grid item, which is used to set the span of the grid item in the column direction. Value range: [1, +∞). If set to **0**, the value **1** is used. In a vertical grid layout, if the value exceeds the actual number of columns, the actual number of columns is used. |