# ArkUI_AccessibleGridItemInfo

```c
typedef struct ArkUI_AccessibleGridItemInfo {...} ArkUI_AccessibleGridItemInfo
```

## Overview

Defines a struct for the accessible grid item information.

<!--Device-typedef struct ArkUI_AccessibleGridItemInfo {...} ArkUI_AccessibleGridItemInfo--><!--Device-typedef struct ArkUI_AccessibleGridItemInfo {...} ArkUI_AccessibleGridItemInfo-End-->

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 13

**Related module**: [ArkUI_Accessibility](capi-arkui-arkui-accessibility.md)

**Header file**: [native_interface_accessibility.h](capi-native-interface-accessibility-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| bool heading | Whether it is a header. |
| bool selected | Whether it is selected. |
| int32_t columnIndex | Column index. |
| int32_t rowIndex | Row index. |
| int32_t columnSpan | Column span. |
| int32_t rowSpan | Row span. |


