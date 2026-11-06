# ArkUI_AccessibleGridItemInfo

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyinhua-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=e98b791a1f57fab5012a75ce7d9ff0a0466dd410 translatedAt=2026-07-16T10:42:05.996Z pushedAt=2026-07-17T02:28:58.029Z -->

```c
typedef struct {...} ArkUI_AccessibleGridItemInfo
```

## Overview

Describes the accessibility attributes of a grid item in a grid component. This struct provides information such as the position, span, and selected state of a grid item to the accessibility service, enabling the accessibility service to obtain the layout information of the grid item.

**Since**: 13

**Related module**: [ArkUI_Accessibility](capi-arkui-accessibility.md)

**Header file**: [native_interface_accessibility.h](capi-native-interface-accessibility-h.md)

## Summary

### Member Variables

| Name| Description    |
| -- |--------|
| bool heading | Whether the item is a heading. **true** for heading, **false** for non-heading.|
| bool selected | Whether the item is selected. **true** for selected, **false** for unselected.|
| int32_t columnIndex | Column index. The value is an integer greater than or equal to 0. The setting does not take effect when 0 or a negative number is passed in. |
| int32_t rowIndex | Row index. The value is an integer greater than or equal to 0. The setting does not take effect when 0 or a negative number is passed in. |
| int32_t columnSpan | Column span. The value is an integer greater than 0. The setting does not take effect when 0 or a negative number is passed in. |
| int32_t rowSpan | Row span. The value is an integer greater than 0. The setting does not take effect when 0 or a negative number is passed in. |