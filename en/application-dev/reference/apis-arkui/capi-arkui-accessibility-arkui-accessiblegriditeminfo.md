# ArkUI_AccessibleGridItemInfo
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhanghangkai10241-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->

```c
typedef struct {...} ArkUI_AccessibleGridItemInfo
```

## Overview

Configures attributes for specific components including **List**, **Flex**, **Select**, and **Swiper**.

**Since**: 13

**Related module**: [ArkUI_Accessibility](capi-arkui-accessibility.md)

**Header file**: [native_interface_accessibility.h](capi-native-interface-accessibility-h.md)

## Summary

### Member Variables

| Name| Description    |
| -- |--------|
| bool heading | Whether the item is a heading. **true** for heading, **false** for non-heading.|
| bool selected | Whether the item is selected. **true** for selected, **false** for unselected.|
| int32_t columnIndex | Row index of the item.  |
| int32_t rowIndex | Column index of the item.  |
| int32_t columnSpan | Number of rows that the item spans.  |
| int32_t rowSpan | Number of columns that the item spans.  |
