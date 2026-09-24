# CircleStyleOptions

```TypeScript
declare interface CircleStyleOptions
```

Describes the parameters of the ring style.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ResourceColor
```

Color of the background circle.

Default value: **'#33182431'**

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableForeground

```TypeScript
enableForeground?: boolean
```

Whether the background circle is displayed above the grid dot.

**true**: The background ring is displayed above the grid dot to cover the grid dot. **false**: The background ring is displayed below the grid dot and does not cover the grid dot.

Default value: **false**

**Type:** boolean

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableWaveEffect

```TypeScript
enableWaveEffect?: boolean
```

Whether to enable the wave effect after a grid dot is selected.

**true** to enable; **false** otherwise.

Default value: **true**

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## radius

```TypeScript
radius?: LengthMetrics
```

Radius of the background circle.

Default value: 1.833 times (that is, 11/6) of the value of [circleRadius](arkts-arkui-patternlock-comp-attribute.md#circleradius)

**Type:** LengthMetrics

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
