# ArkUI_AccessibleGridItemInfo
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyinhua-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=33898b66eb6c0bf66810bb0d90faa36b55a4ad07 translatedAt=2026-11-09T11:38:23.470Z pushedAt=2026-11-10T01:56:46.692Z nl=1 -->

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
| int32_t columnIndex | Column index. The value is an integer greater than or equal to 0. The setting does not take effect when a negative number is passed in. |
| int32_t rowIndex | Row index. The value is an integer greater than or equal to 0. The setting does not take effect when a negative number is passed in. |
| int32_t columnSpan | Column span. The value is an integer greater than 0. The setting does not take effect when 0 or a negative number is passed in. |
| int32_t rowSpan | Row span. The value is an integer greater than 0. The setting does not take effect when 0 or a negative number is passed in. |


