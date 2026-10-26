# ARKUI_TextPickerRangeContent

```c
typedef struct ARKUI_TextPickerRangeContent {...} ARKUI_TextPickerRangeContent
```

## Overview

Defines the image resource supported by a single-column text picker. This struct is used to display both images and text in the **TextPicker** component, and is suitable for scenarios where icons and text combinations need to be displayed in a single-column text picker. It supports custom icon paths and text content. Each item can be set with an independent icon and text, or only one of them, helping you implement flexible image-text picker configurations.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [picker.h](capi-picker-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const char* icon |  |
| const char* text |  |


