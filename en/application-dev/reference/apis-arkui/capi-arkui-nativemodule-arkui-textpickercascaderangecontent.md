# ARKUI_TextPickerCascadeRangeContent

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @luoying_ace_admin-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=b4709760ee6eeea5b831c4c09fdf9dcdc3a0d77d translatedAt=2026-08-21T01:44:21.769Z pushedAt=2026-08-21T02:45:31.080Z -->

```c
typedef struct {...} ARKUI_TextPickerCascadeRangeContent
```

## Overview

Defines a multi-column text cascade picker, which describes the hierarchical data structure of the multi-column text cascade picker. This struct forms a tree structure through children members to support multi-level cascade selection. It is suitable for scenarios that require displaying hierarchical data such as province/city/district and year/month/day, and can simplify the development of the multi-level text cascade picker.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [picker.h](capi-picker-h.md)

## Summary

### Member Variables

| Name                                              | Description|
|--------------------------------------------------| -- |
| const char* text | Pointer to the text content to be displayed in the multi-column text cascade picker, used to represent the display text of this option. The default value is **NULL**. This parameter can be set to an empty string to indicate no text. For the value principles, see the API description.<br>**Note:** When no text is set, it is recommended to set this parameter to **NULL**. |
| const [ARKUI_TextPickerRangeContent](capi-arkui-nativemodule-arkui-textpickerrangecontent.md)* children | Pointer to the child-level cascade data array, which points to the cascaded data array of the next level. When this option is selected at the current level, the array content corresponding to children is displayed as the options of the next level. Set it to **NULL** when there is no child-level data. The array pointer passed must remain valid during the use of the picker, and the caller is responsible for managing the array memory. |
| int32_t size | Number of elements in the children array, that is, the number of options at the current level. The value must be greater than or equal to 0 and must be consistent with the actual number of elements in the children array passed. When **children** is **NULL**, set this parameter to **0**. A parameter error exception is thrown when a negative number or an inconsistent value is passed in. |