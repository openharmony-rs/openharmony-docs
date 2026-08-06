# ArkUI_AccessibleGridInfo

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyinhua-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=e98b791a1f57fab5012a75ce7d9ff0a0466dd410 translatedAt=2026-07-16T10:41:58.935Z pushedAt=2026-07-17T02:24:06.008Z -->

```c
typedef struct {...} ArkUI_AccessibleGridInfo
```

## Overview

Describes the overall layout attributes of a grid component. This struct is used to provide information such as the row count, column count, and selection mode of the grid component to the accessibility service, enabling the accessibility service to obtain the overall layout information of the grid.

**Since**: 13

**Related module**: [ArkUI_Accessibility](capi-arkui-accessibility.md)

**Header file**: [native_interface_accessibility.h](capi-native-interface-accessibility-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int32_t rowCount | Number of rows in the grid. The value range is a positive integer greater than 0. If a non-positive integer is passed, the setting does not take effect. |
| int32_t columnCount | Number of columns in the grid. The value range is a positive integer greater than 0. If a non-positive integer is passed, the setting does not take effect. |
| int32_t selectionMode | Selection mode. The value 0 means that only one row in the grid is selected, and a non-zero value means that multiple rows in the grid are selected. |