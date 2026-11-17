# ArkUI_AccessibleRangeInfo
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyinhua-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct {...} ArkUI_AccessibleRangeInfo
```

## 概述

用于表示特定组件（如[Slider](arkui-ts/ts-basic-components-slider.md)、[Rating](arkui-ts/ts-basic-components-rating.md)、[Progress](arkui-ts/ts-basic-components-progress.md)）的范围值信息，包含当前值、最大值和最小值，供无障碍服务读取并向障碍用户播报。

**起始版本：** 13

**相关模块：** [ArkUI_Accessibility](capi-arkui-accessibility.md)

**所在头文件：** [native_interface_accessibility.h](capi-native-interface-accessibility-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| double min | 组件的最小值。 |
| double max | 组件的最大值。 |
| double current | 组件的当前值。 |


