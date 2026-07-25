# ArkUI_AccessibleGridItemInfo
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyinhua-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct {...} ArkUI_AccessibleGridItemInfo
```

## 概述

用于描述网格组件内某个网格项的无障碍属性。该结构体用于向无障碍服务提供网格项的位置、跨度、选中状态等信息，支持无障碍服务获取网格项的布局信息。

**起始版本：** 13

**相关模块：** [ArkUI_Accessibility](capi-arkui-accessibility.md)

**所在头文件：** [native_interface_accessibility.h](capi-native-interface-accessibility-h.md)

## 汇总

### 成员变量

| 名称 | 描述     |
| -- |--------|
| bool heading | 是否是标题。true表示是标题，false表示不是标题。 |
| bool selected | 是否被选中。true表示被选中，false表示未被选中。 |
| int32_t columnIndex | 列下标。取值范围为大于等于0的整数。传入0或负数时该字段不生效。 |
| int32_t rowIndex | 行下标。取值范围为大于等于0的整数。传入0或负数时该字段不生效。 |
| int32_t columnSpan | 列跨度。取值范围为大于0的整数。传入0或负数时该字段不生效。 |
| int32_t rowSpan | 行跨度。取值范围为大于0的整数。传入0或负数时该字段不生效。 |


