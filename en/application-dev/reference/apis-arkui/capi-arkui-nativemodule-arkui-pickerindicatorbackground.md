# ArkUI_PickerIndicatorBackground

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @luoying_ace_admin-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->

``` c
typedef struct {...} ArkUI_PickerIndicatorBackground
```

## Overview

Defines the style parameter of the background-style indicator.

**Since**: 23

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_type.h](capi-native-type-h.md)

**Sample**: <!--RP1-->[native_type_sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeType/native_type_sample)<!--RP1End-->

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t backgroundColor | Background color of the selected item.<br>Default value: **0**<br>Value range: 0xARGB format, for example, <b>0xFF1122FF</b>.|
| float topLeftRadius | Radius of the upper left corner.<br>Default value: **0**<br>Unit: vp<br>Value range: no more than half of the smaller value between the width and height of the selected item. Setting the style parameters for the background-style indicator fails when the value is less than **0**. If the value is greater than the maximum value, the maximum value is used.|
| float topRightRadius | Radius of the upper right corner.<br>Default value: **0**<br>Unit: vp<br>Value range: no more than half of the smaller value between the width and height of the selected item. Setting the style parameters for the background-style indicator fails when the value is less than **0**. If the value is greater than the maximum value, the maximum value is used.|
| float bottomLeftRadius | Radius of the lower left corner.<br>Default value: **0**<br>Unit: vp<br>Value range: no more than half of the smaller value between the width and height of the selected item. Setting the style parameters for the background-style indicator fails when the value is less than **0**. If the value is greater than the maximum value, the maximum value is used.|
| float bottomRightRadius | Radius of the lower right corner.<br>Default value: **0**<br>Unit: vp<br>Value range: no more than half of the smaller value between the width and height of the selected item. Setting the style parameters for the background-style indicator fails when the value is less than **0**. If the value is greater than the maximum value, the maximum value is used.|
