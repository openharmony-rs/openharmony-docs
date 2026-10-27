# ARKUI_TextPickerCascadeRangeContent

```c
typedef struct ARKUI_TextPickerCascadeRangeContent {...} ARKUI_TextPickerCascadeRangeContent
```

## Overview

Defines a multi-column text cascade picker, which describes the hierarchical data structure of the multi- column text cascade picker. This struct forms a tree structure through children members to support multi-level cascade selection. It is suitable for scenarios that require displaying hierarchical data such as province/city/ district and year/month/day, and can simplify the development of the multi-level text cascade picker.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [picker.h](capi-picker-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const char* text |  |
| [const ARKUI_TextPickerRangeContent*](capi-arkui-nativemodule-arkui-textpickerrangecontent.md) children |  |
| int32_t size |  |


