# ArkUI_GridItemRect

```c
typedef struct ArkUI_GridItemRect {...} ArkUI_GridItemRect
```

## 概述

Defines the return value for the **onGetRectByIndex** callback in **Grid** layout options.

**起始版本：** 22

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [node_grid.h](capi-node-grid-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t rowStart | Starting row position of the **GridItem** component. |
| uint32_t columnStart | Starting column position of the **GridItem** component. |
| uint32_t rowSpan | Number of rows occupied by the **GridItem** component. |
| uint32_t columnSpan | Number of columns occupied by the **GridItem** component. |


