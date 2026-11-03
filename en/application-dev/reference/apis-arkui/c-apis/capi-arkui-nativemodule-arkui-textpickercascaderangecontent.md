# ARKUI_TextPickerCascadeRangeContent

```c
typedef struct ARKUI_TextPickerCascadeRangeContent {...} ARKUI_TextPickerCascadeRangeContent
```

## Overview

Defines a multi-column text cascade picker, which describes the hierarchical data structure of the multi- column text cascade picker. This struct forms a tree structure through children members to support multi-level cascade selection. It is suitable for scenarios that require displaying hierarchical data such as province/city/ district and year/month/day, and can simplify the development of the multi-level text cascade picker.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-others-arkui-nativemodule.md)

**Header file**: [picker.h](capi-picker-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const char* text | Pointer to the text content, which is a C string ending with `\0`. The value can be **NULL**, and the default value is `nullptr`; when `nullptr` is passed through [OH_ArkUI_TextPickerRangeContentArray_SetTextAtIndex](capi-picker-h.md#oh_arkui_textpickerrangecontentarray_settextatindex), the setting does not take effect. An empty string `""` is valid and indicates that no text is displayed. Specific text content is used to display a hint (chosen when a text description is required), an empty string is used to explicitly display no text (chosen when only an icon is displayed), and **NULL** is the default value ( you should set it to a specific value or an empty string through the **Set** method; retaining **NULL** is not recommended). If the parameter is not set through the **Set** method, an empty string is displayed by default, consistent with the ArkTS documentation.<br>**Since**: 12 |
| [const ARKUI_TextPickerRangeContent*](capi-arkui-nativemodule-arkui-textpickerrangecontent.md) children | Pointer to the child-level cascade data array, which points to the cascaded data array of the next level. When this option is selected at the current level, the array content corresponding to children is displayed as the options of the next level. Set it to **NULL** when there is no child-level data. The array pointer passed must remain valid during the use of the picker, and the caller is responsible for managing the array memory.<br>**Since**: 12 |
| int32_t size | Number of elements in the children array, that is, the number of options at the current level. The value must be greater than or equal to 0 and must be consistent with the actual number of elements in the children array passed. When **children** is **NULL**, set this parameter to **0**. A parameter error exception is thrown when a negative number or an inconsistent value is passed in.<br>**Since**: 12 |


