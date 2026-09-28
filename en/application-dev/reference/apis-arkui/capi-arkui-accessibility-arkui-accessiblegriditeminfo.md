# ArkUI_AccessibleGridItemInfo
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyinhua-->
<!--Designer: @dutie123-->
<!--Tester: @fredyuan0912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=c18a4e1567d098b4c6780d709d006d4ba2f2faab translatedAt=2026-09-18T11:16:53.031Z pushedAt=2026-09-20T07:13:54.682Z -->

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


