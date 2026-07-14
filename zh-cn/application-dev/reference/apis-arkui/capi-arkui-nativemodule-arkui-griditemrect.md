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

## 概述

定义Grid布局选项[OH_ArkUI_GridLayoutOptions_RegisterGetRectByIndexCallback](capi-grid-h.md#oh_arkui_gridlayoutoptions_registergetrectbyindexcallback)回调返回值结构体，用于通过GridItem索引指定该GridItem在Grid中的起始行列位置和占用的行列数。

**起始版本：** 22

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [grid.h](capi-grid-h.md)

**相关示例：** <!--RP1-->[native_type_sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeType/native_type_sample)<!--RP1End-->

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t rowStart | GridItem行起始位置，从0开始计数，用于确定GridItem在Grid中的起始行。 |
| uint32_t columnStart | GridItem列起始位置，从0开始计数，用于确定GridItem在Grid中的起始列。 |
| uint32_t rowSpan | GridItem占用的行数，用于设置GridItem在行方向上的跨度。 |
| uint32_t columnSpan | GridItem占用的列数，用于设置GridItem在列方向上的跨度。 |

