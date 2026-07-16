# ArkUI_GridItemSize

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @guozejun; @rongShao-Z-->
<!--Designer: @guozejun-->
<!--Tester: @leiyuqian-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct {...} ArkUI_GridItemSize
```

## 概述

定义Grid布局选项[OH_ArkUI_GridLayoutOptions_RegisterGetIrregularSizeByIndexCallback](capi-grid-h.md#oh_arkui_gridlayoutoptions_registergetirregularsizebyindexcallback)回调返回值结构体，用于通过GridItem索引指定不规则GridItem占用的行数和列数。

**起始版本：** 22

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [grid.h](capi-grid-h.md)

**相关示例：** <!--RP1-->[native_type_sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeType/native_type_sample)<!--RP1End-->

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t rowSpan | GridItem占用的行数，用于设置GridItem在行方向上的跨度。 |
| uint32_t columnSpan | GridItem占用的列数，用于设置GridItem在列方向上的跨度。 |


