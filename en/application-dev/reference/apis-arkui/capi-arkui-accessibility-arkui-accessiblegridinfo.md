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

## Overview

Configures the grid layout attributes of a specific component (such as [List](arkui-ts/ts-container-list.md), [Flex](arkui-ts/ts-container-flex.md), [Select](arkui-ts/ts-basic-components-select.md), or [Swiper](arkui-ts/ts-container-swiper.md)).

**Since**: 13

**Related module**: [ArkUI_Accessibility](capi-arkui-accessibility.md)

**Header file**: [native_interface_accessibility.h](capi-native-interface-accessibility-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int32_t rowCount | Number of rows of the component. The value is an integer greater than 0.|
| int32_t columnCount | Number of columns of the component. The value is an integer greater than 0.|
| int32_t selectionMode | Selection mode. If the value is **0**, only a single row in the grid can be selected. If the value is not 0, multiple rows can be selected.|
