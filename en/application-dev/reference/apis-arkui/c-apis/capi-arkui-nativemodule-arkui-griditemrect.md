# ArkUI_GridItemRect

```c
typedef struct ArkUI_GridItemRect {...} ArkUI_GridItemRect
```

## Overview

Defines the return value for the [OH_ArkUI_GridLayoutOptions_RegisterGetRectByIndexCallback](capi-grid-h.md#oh_arkui_gridlayoutoptions_registergetrectbyindexcallback) callback in **Grid** layout options, which is used to specify the start row, start column, row span, and column span for the grid item in **Grid** at the specified index.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 22

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [grid.h](capi-grid-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t rowStart | Start row of a grid item in **Grid**, which is counted from 0. |
| uint32_t columnStart | Start column of a grid item in **Grid**, which is counted from 0. |
| uint32_t rowSpan | Number of rows occupied by a grid item, which is used to set the span of the grid item in the row direction. Value range: [1, +∞). If set to **0**, the value **1** is used. In a horizontal grid layout, if the value exceeds the actual number of rows, the actual number of rows is used. |
| uint32_t columnSpan | Number of columns occupied by a grid item, which is used to set the span of the grid item in the column direction. Value range: [1, +∞). If set to **0**, the value **1** is used. In a vertical grid layout, if the value exceeds the actual number of columns, the actual number of columns is used. |


