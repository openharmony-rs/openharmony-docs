# ArkUI_AccessibleGridInfo
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhanghangkai10241-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct {...} ArkUI_AccessibleGridInfo
```

## 概述

用于配置特定组件（如List、Flex、Select、Swiper组件）的网格布局属性。

**起始版本：** 13

**相关模块：** [ArkUI_Accessibility](capi-arkui-accessibility.md)

**所在头文件：** [native_interface_accessibility.h](capi-native-interface-accessibility-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int32_t rowCount | 组件的行数。 |
| int32_t columnCount | 组件的列数。 |
| int32_t selectionMode | 值为0时表示仅选中网格的一行，非0值时表示选中网格的多行。 |


