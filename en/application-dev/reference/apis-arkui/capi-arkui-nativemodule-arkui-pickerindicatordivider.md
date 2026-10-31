# ArkUI_PickerIndicatorDivider

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @luoying_ace_admin-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=dca3602d000791dfb3b371084e93da57f553080b translatedAt=2026-08-19T08:27:19.559Z pushedAt=2026-08-20T06:27:04.834Z -->

```c
typedef struct {...} ArkUI_PickerIndicatorDivider
```

## Overview

Defines the style parameter of the divider-style indicator. This struct supports customizing the stroke width of the divider, color of the divider, and distance between the divider and the container edges. It applies to scenarios where the appearance of the **Picker** control's divider needs to be beautified. You can configure this struct to achieve personalized divider effects, improving the aesthetics of the UI and the user experience.

**Since**: 23

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [picker.h](capi-picker-h.md)

**Sample**: <!--RP1-->[native_type_sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeType/native_type_sample)<!--RP1End-->

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| float strokeWidth | Stroke width of the divider.<br>Default value: **0**<br>Unit: vp<br>Value range: [0, Half the height of the selected item (that is, 20 vp)].<br>Setting the style parameter for the divider-style indicator fails when **strokeWidth** is less than 0. If **strokeWidth** exceeds half the height of the selected item, **0** is used. Percentages are not supported. |
| uint32_t dividerColor | Color of the divider.<br>Default value: **0** (indicating a fully transparent color, so the divider is invisible)<br>Format requirement: 0xARGB format, for example, **0xFF1122FF**. If no color is set, the default value is used. |
| float startMargin | Distance between the divider and the start edge of the **Picker** container.<br>Default value: **0**<br>Unit: vp<br>Value range: The sum of **startMargin** and **endMargin** must not exceed the width of the **Picker** container.<br>Setting the style parameter for the divider-style indicator fails when the value less than 0 is set. If the sum of **startMargin** and **endMargin** exceeds the container width, the default value **0** is used. Percentages are not supported. |
| float endMargin | Distance between the divider and the end edge of the **Picker** container.<br>Default value: **0**<br>Unit: vp<br>Value range: The sum of **startMargin** and **endMargin** must not exceed the width of the **Picker** container.<br>Setting the style parameter for the divider-style indicator fails when the value less than 0 is set. If the sum of **startMargin** and **endMargin** exceeds the container width, the default value **0** is used. Percentages are not supported. |