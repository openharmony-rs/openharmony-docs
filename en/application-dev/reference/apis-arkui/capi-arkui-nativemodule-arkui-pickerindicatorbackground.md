# ArkUI_PickerIndicatorBackground

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @luoying_ace_admin-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=23e3af99bbbae5d3ef1af76c14a5ad32ec002e14 translatedAt=2026-08-19T08:27:21.554Z pushedAt=2026-08-20T06:18:58.140Z -->

```c
typedef struct {...} ArkUI_PickerIndicatorBackground
```

## Overview

Defines the style parameter of the background-style indicator of the selected item. The background-style indicator highlights the selected item with a background color and rounded corners, including the background color and corner radius of the selected item.

Usage scenarios:

- Set a custom background style for the selected item in the **Picker** component, for example, the background of the selected item in the song list in a music player.

- Highlight the currently selected date or time in the date picker to improve user experience.

- Add a rounded-corner background to the selected item in the option list to enhance the visual hierarchy.

**Since**: 23

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [picker.h](capi-picker-h.md)

**Sample**: <!--RP1-->[native_type_sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeType/native_type_sample)<!--RP1End-->

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t backgroundColor | Background color of the selected item.<br>Default value: **0** (fully transparent, with an ARGB value of 0x00000000, meaning the background is invisible).<br>Format requirement: 0xAARRGGBB format, where the first byte is the alpha channel (**00** indicates fully transparent and **FF** indicates fully opaque), and the second to fourth bytes are the red, green, and blue channels, respectively, for example, **0xFF1122FF**. |
| float topLeftRadius | Radius of the upper left corner.<br>Default value: **0**<br>Unit: vp<br>Value range: Use the smaller of the width and height of the selected item as **x**. The maximum value does not exceed half of **x**. If the value is less than 0, the style parameter of the background-style indicator of the selected item fails to be set. If the value is greater than the maximum value, the maximum value is used. |
| float topRightRadius | Radius of the upper right corner.<br>Default value: **0**<br>Unit: vp<br>Value range: Use the smaller of the width and height of the selected item as **x**. The maximum value does not exceed half of **x**. If the value is less than 0, the style parameter of the background-style indicator of the selected item fails to be set. If the value is greater than the maximum value, the maximum value is used. |
| float bottomLeftRadius | Radius of the lower left corner.<br>Default value: **0**<br>Unit: vp<br>Value range: Use the smaller of the width and height of the selected item as **x**. The maximum value does not exceed half of **x**. If the value is less than 0, the style parameter of the background-style indicator of the selected item fails to be set. If the value is greater than the maximum value, the maximum value is used. |
| float bottomRightRadius | Radius of the lower right corner.<br>Default value: **0**<br>Unit: vp<br>Value range: Use the smaller of the width and height of the selected item as **x**. The maximum value does not exceed half of **x**. If the value is less than 0, the style parameter of the background-style indicator of the selected item fails to be set. If the value is greater than the maximum value, the maximum value is used. |