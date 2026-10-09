# ARKUI_TextPickerRangeContent

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @luoying_ace_admin-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=b4709760ee6eeea5b831c4c09fdf9dcdc3a0d77d translatedAt=2026-08-21T01:44:35.215Z pushedAt=2026-08-21T02:58:00.059Z -->

```c
typedef struct {...} ARKUI_TextPickerRangeContent
```

## Overview

Defines the image resource supported by a single-column text picker. This struct is used to display both images and text in the **TextPicker** component, and is suitable for scenarios where icons and text combinations need to be displayed in a single-column text picker. It supports custom icon paths and text content. Each item can be set with an independent icon and text, or only one of them, helping you implement flexible image-text picker configurations.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [picker.h](capi-picker-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| const char* icon | Pointer to the icon path, which is a C string ending with `\0`. The value can be **NULL**. When not set through an API, the parameter remains at the default value `nullptr`; when set to `nullptr` through [OH_ArkUI_TextPickerRangeContentArray_SetIconAtIndex](capi-picker-h.md#oh_arkui_textpickerrangecontentarray_seticonatindex), the setting does not take effect (the API ignores it). An empty string `""` is valid and indicates that no icon is displayed. A specific path is used to display a custom icon (chosen when an icon hint is required), an empty string is used to explicitly display no icon (chosen when only text is displayed), and **NULL** is the default value (you should set it to a specific value or an empty string through the **Set** method; retaining **NULL** is not recommended). The path format is an in-application resource path, for example, `"/common/hello.png"`, consistent with [TextPickerRangeContent](arkui-ts/ts-basic-components-textpicker.md#textpickerrangecontent10) of ArkTS. URIs are also supported. The image format is not specifically restricted. Images are loaded through **ImageSourceInfo**, and the supported formats are consistent with those of the [Image](arkui-ts/ts-basic-components-image.md) component (such as PNG, JPG, and WebP). The display size is fixed at 24 vp × 24 vp and cannot be configured through this struct. No upper limit on the file size is specified in the source code. |
| const char* text | Pointer to the text content, which is a C string ending with `\0`. The value can be **NULL**, and the default value is `nullptr`; when `nullptr` is passed through [OH_ArkUI_TextPickerRangeContentArray_SetTextAtIndex](capi-picker-h.md#oh_arkui_textpickerrangecontentarray_settextatindex), the setting does not take effect. An empty string `""` is valid and indicates that no text is displayed. Specific text content is used to display a hint (chosen when a text description is required), an empty string is used to explicitly display no text (chosen when only an icon is displayed), and **NULL** is the default value (you should set it to a specific value or an empty string through the **Set** method; retaining **NULL** is not recommended). If the parameter is not set through the **Set** method, an empty string is displayed by default, consistent with the ArkTS documentation. |

> **NOTE**
>
> - Each item must provide at least one of an icon and text, which can be icon only, text only, or both.
> - When the text length is greater than the column width, the text content is truncated for display.
> - It is recommended that you use [OH_ArkUI_TextPickerRangeContentArray_Create](capi-picker-h.md#oh_arkui_textpickerrangecontentarray_create) to create the array, and then use [OH_ArkUI_TextPickerRangeContentArray_SetIconAtIndex](capi-picker-h.md#oh_arkui_textpickerrangecontentarray_seticonatindex) and [OH_ArkUI_TextPickerRangeContentArray_SetTextAtIndex](capi-picker-h.md#oh_arkui_textpickerrangecontentarray_settextatindex) to set the data at each position, so as to ensure the correctness of the data structure. Manually assembling the raw struct is not recommended. If the struct is manually assembled or the **Create** method is not used for initialization, problems such as incorrect array object initialization, abnormal memory management, or type mismatch may occur.
> - This struct is used in [NODE_TEXT_PICKER_OPTION_RANGE](capi-native-node-h-nodeattributetype-informationselection.md#node_text_picker_option_range) when **rangeType** is set to `ARKUI_TEXTPICKER_RANGETYPE_RANGE_CONTENT` (value **2**).