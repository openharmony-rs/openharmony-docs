# CircleStyleOptions

```TypeScript
declare interface CircleStyleOptions
```

Describes the parameters of the ring style.

**Since:** 12

<!--Device-unnamed-declare interface CircleStyleOptions--><!--Device-unnamed-declare interface CircleStyleOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ResourceColor
```

Background ring color.

Default value: '#33182431' (dark gray, 20% opacity).

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CircleStyleOptions-color?: ResourceColor--><!--Device-CircleStyleOptions-color?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableForeground

```TypeScript
enableForeground?: boolean
```

Whether the background ring is displayed above the grid dots.

true: the background ring is displayed above the grid dots and covers them; false: the background ring is displayed below the grid dots and does not cover them.

Default value: false.

**Type:** boolean

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-CircleStyleOptions-enableForeground?: boolean--><!--Device-CircleStyleOptions-enableForeground?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableWaveEffect

```TypeScript
enableWaveEffect?: boolean
```

Switch for the wave effect after a grid dot is selected.

true: displays the wave effect; false: does not display the wave effect.

Default value: true.

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CircleStyleOptions-enableWaveEffect?: boolean--><!--Device-CircleStyleOptions-enableWaveEffect?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## radius

```TypeScript
radius?: LengthMetrics
```

Radius of the background ring.

Default value: approximately 1.833 times (that is, 11/6) of [circleRadius](arkts-arkui-patternlock-comp-attribute.md#circleradius).

Value range: greater than 0.

**Type:** LengthMetrics

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CircleStyleOptions-radius?: LengthMetrics--><!--Device-CircleStyleOptions-radius?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
