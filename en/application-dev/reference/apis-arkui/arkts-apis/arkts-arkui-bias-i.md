# Bias

```TypeScript
declare interface Bias
```

Defines offset parameters for a component under anchor constraints.

Taking horizontal bias as an example, the value is the ratio of D<sub>start</sub> (the distance from the component to the left anchor) to D<sub>start</sub> + D<sub>end</sub> (the total horizontal distance between anchors). In a mirrored language, D<sub>start</sub> represents the distance from the component to the right anchor. In the following figure, D<sub>width</sub> indicates the width of the component.

![bias_horizontal_example.png](../../../reference/apis-arkui/arkui-ts/figures/bias_horizontal_example.png)

The same rule applies to the vertical direction. The value is the ratio of D<sub>top</sub> (the distance from the component to the top anchor) to D<sub>top</sub> + D<sub>bottom</sub> (the total vertical distance between anchors). In the following figure, D<sub>height</sub> indicates the height of the component.

![bias_vertical_example.png](../../../reference/apis-arkui/arkui-ts/figures/bias_vertical_example.png)

**Since:** 11

<!--Device-unnamed-declare interface Bias--><!--Device-unnamed-declare interface Bias-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## horizontal

```TypeScript
horizontal?: number
```

Bias value in the horizontal direction.

This parameter takes effect only when the child component has a valid **width** value and two horizontal anchors. The value must be greater than or equal to 0.

Default value: **0.5**

**Type:** number

**Default:** 0.5

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

<!--Device-Bias-horizontal?: number--><!--Device-Bias-horizontal?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## vertical

```TypeScript
vertical?: number
```

Bias value in the vertical direction.

This parameter takes effect only when the child component has a valid **height** value and two vertical anchors. The value must be greater than or equal to 0.

Default value: **0.5**

**Type:** number

**Default:** 0.5

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

<!--Device-Bias-vertical?: number--><!--Device-Bias-vertical?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
