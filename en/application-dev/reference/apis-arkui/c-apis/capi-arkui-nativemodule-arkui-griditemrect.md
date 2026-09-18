# ArkUI_GridItemRect

```c
typedef struct ArkUI_GridItemRect {...} ArkUI_GridItemRect
```

## Overview

Defines the return value for the **onGetRectByIndex** callback in **Grid** layout options.

**Since**: 22

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [grid.h](capi-grid-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t rowStart | Starting row position of the **GridItem** component. |
| uint32_t columnStart | Starting column position of the **GridItem** component. |
| uint32_t rowSpan | Number of rows occupied by the **GridItem** component. |
| uint32_t columnSpan | Number of columns occupied by the **GridItem** component. |


