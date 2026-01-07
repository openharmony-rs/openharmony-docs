# ArkUI_PickerIndicatorDivider

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @luoying_ace_admin-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->

``` c
typedef struct {...} ArkUI_PickerIndicatorDivider
```

## Overview

Defines the style parameter of the divider-style indicator.

**Since**: 23

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_type.h](capi-native-type-h.md)

**Sample**: <!--RP1-->[native_type_sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeType/native_type_sample)<!--RP1End-->

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| float strokeWidth | Stroke width of the divider.<br>Default value: **0**<br>Unit: vp<br>Value range: [0, half the height of the selected item (that is, 20 vp)]. Setting the style parameters for the divider-style indicator fails when **strokeWidth** is less than **0**. If **strokeWidth** exceeds half the height of the selected item, 2.0 px is used. Percentages are not supported.|
| uint32_t dividerColor | Color of the divider.<br>Default value: **0**<br>Value range: 0xARGB format, for example, <b>0xFF1122FF</b>.|
| float startMargin | Distance between the divider and the start edge of the picker container.<br>Default value: **0**<br>Unit: vp<br>Value range: The sum of **startMargin** and **endMargin** must not exceed the width of the **Picker** container. Setting the style parameters for the divider-style indicator fails when the value less than **0** is set. If the sum of **startMargin** and **endMargin** exceeds the width of the **Picker** container, the default value is used. Percentages are not supported.|
| float endMargin | Distance between the divider and the end edge of the **Picker** container.<br>Default value: **0**<br>Unit: vp<br>Value range: The sum of **startMargin** and **endMargin** must not exceed the width of the **Picker** container. Setting the style parameters for the divider-style indicator fails when the value less than **0** is set. If the sum of **startMargin** and **endMargin** exceeds the width of the **Picker** container, the default value is used. Percentages are not supported.|
