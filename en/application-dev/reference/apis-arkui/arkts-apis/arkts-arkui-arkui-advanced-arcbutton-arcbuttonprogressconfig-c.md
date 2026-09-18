# ArcButtonProgressConfig

Defines the progress indicator configuration options of the **ArcButton** component.

**Since:** 23

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## Modules to Import

```TypeScript
import { ArcButton, ArcButtonOptions, ArcButtonProgressConfig, ArcButtonPosition, ArcButtonStyleMode, ArcButtonStatus } from '@kit.ArkUI';
```

## color

```TypeScript
color?: ResourceColor
```

Foreground color of the progress indicator. If the component's background color ([backgroundColor](arkts-arkui-arkui-advanced-arcbutton-arcbuttonoptions-c.md)) is set, it is used as the default foreground color of the progress indicator. The foreground color of the progress indicator is not affected by the button style ([ArcButtonStyleMode](arkts-arkui-arkui-advanced-arcbutton-arcbuttonstylemode-e.md)). The progress indicator's background color is derived solely from its foreground color, with an opacity value of 25%.

Default value: **"#1F71FF"**, which is blue.

**Type:** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## total

```TypeScript
total?: number
```

Maximum progress value.

Default value: **100**

Value range: [0, 2147483647]. If the value is 0 or out of the range, the default value 100 is used.

**Type:** number

**Default:** 100

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## value

```TypeScript
value: number
```

Current progress value. Values less than 0 are adjusted to **0**, and values greater than the **total** value are capped at the **total** value.

Default value: **0**.

Value range: [0, total]

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle
