# ArkUI_PickerIndicatorBackground

```c
typedef struct ArkUI_PickerIndicatorBackground {...} ArkUI_PickerIndicatorBackground
```

## Overview

Defines the style parameter of the background-style indicator of the selected item. The background-style indicator highlights the selected item with a background color and rounded corners, including the background color and corner radius of the selected item.<br>Usage scenarios:

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Related module**: [ArkUI_NativeModule](capi-others-arkui-nativemodule.md)

**Header file**: [picker.h](capi-picker-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t backgroundColor | Background color of the selected item.<br>Default value: **0** (fully transparent, with an ARGB value of 0x00000000, meaning the background is invisible).<br>Format requirement: 0xAARRGGBB format, where the first byte is the alpha channel (**00** indicates fully transparent and **FF** indicates fully opaque), and the second to fourth bytes are the red, green, and blue channels, respectively, for example, **0xFF1122FF**.<br>**Since**: 23 |
| float topLeftRadius | Radius of the upper left corner.<br>Default value: **0**<br>Unit: vp<br>Value range: Use the smaller of the width and height of the selected item as **x**. The maximum value does not exceed half of **x**. If the value is less than 0, the style parameter of the background-style indicator of the selected item fails to be set. If the value is greater than the maximum value, the maximum value is used.<br>**Since**: 23 |
| float topRightRadius | Radius of the upper right corner.<br>Default value: **0**<br>Unit: vp<br>Value range: Use the smaller of the width and height of the selected item as **x**. The maximum value does not exceed half of **x**. If the value is less than 0, the style parameter of the background-style indicator of the selected item fails to be set. If the value is greater than the maximum value, the maximum value is used.<br>**Since**: 23 |
| float bottomLeftRadius | Radius of the lower left corner.<br>Default value: **0**<br>Unit: vp<br>Value range: Use the smaller of the width and height of the selected item as **x**. The maximum value does not exceed half of **x**. If the value is less than 0, the style parameter of the background-style indicator of the selected item fails to be set. If the value is greater than the maximum value, the maximum value is used.<br>**Since**: 23 |
| float bottomRightRadius | Radius of the lower right corner.<br>Default value: **0**<br>Unit: vp<br>Value range: Use the smaller of the width and height of the selected item as **x**. The maximum value does not exceed half of **x**. If the value is less than 0, the style parameter of the background-style indicator of the selected item fails to be set. If the value is greater than the maximum value, the maximum value is used.<br>**Since**: 23 |


