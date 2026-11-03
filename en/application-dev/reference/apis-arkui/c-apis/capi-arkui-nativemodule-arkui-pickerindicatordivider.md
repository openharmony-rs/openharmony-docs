# ArkUI_PickerIndicatorDivider

```c
typedef struct ArkUI_PickerIndicatorDivider {...} ArkUI_PickerIndicatorDivider
```

## Overview

Defines the style parameter of the divider-style indicator. This struct supports customizing the stroke width of the divider, color of the divider, and distance between the divider and the container edges. It applies to scenarios where the appearance of the **Picker** control's divider needs to be beautified. You can configure this struct to achieve personalized divider effects, improving the aesthetics of the UI and the user experience.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Related module**: [ArkUI_NativeModule](capi-others-arkui-nativemodule.md)

**Header file**: [picker.h](capi-picker-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| float strokeWidth | Stroke width of the divider.<br>Default value: **0**<br>Unit: vp<br>Value range: [0, Half the height of the selected item (that is, 20 vp)].<br>Setting the style parameter for the divider-style indicator fails when ** strokeWidth** is less than 0. If **strokeWidth** exceeds half the height of the selected item, **0** is used. Percentages are not supported.<br>**Since**: 23 |
| uint32_t dividerColor | Color of the divider.<br>Default value: **0** (indicating a fully transparent color, so the divider is invisible) <br>Format requirement: 0xARGB format, for example, **0xFF1122FF**. If no color is set, the default value is used.<br>**Since**: 23 |
| float startMargin | Distance between the divider and the start edge of the **Picker** container.<br>Default value: **0**<br>Unit: vp< br>Value range: The sum of **startMargin** and **endMargin** must not exceed the width of the **Picker** container.<br>Setting the style parameter for the divider-style indicator fails when the value less than 0 is set. If the sum of **startMargin** and **endMargin** exceeds the container width, the default value **0** is used. Percentages are not supported.<br>**Since**: 23 |
| float endMargin | Distance between the divider and the end edge of the **Picker** container.<br>Default value: **0**<br>Unit: vp< br>Value range: The sum of **startMargin** and **endMargin** must not exceed the width of the **Picker** container.<br>Setting the style parameter for the divider-style indicator fails when the value less than 0 is set. If the sum of **startMargin** and **endMargin** exceeds the container width, the default value **0** is used. Percentages are not supported.<br>**Since**: 23 |


