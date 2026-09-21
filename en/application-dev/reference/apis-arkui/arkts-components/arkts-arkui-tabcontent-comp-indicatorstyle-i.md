# IndicatorStyle

```TypeScript
interface IndicatorStyle
```

Represents an indicator style object.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderRadius

```TypeScript
borderRadius?: Length
```

Rounded corner radius of the indicator. It cannot be set in percentage.

Default value: **0.0**

Unit: vp

Value range: [0, +∞)

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Default:** 0

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ResourceColor
```

Color of the indicator and board.

Default value: **#FF007DFF**

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height?: Length
```

Height of the indicator. It cannot be set in percentage.

Default value: **2.0**

Unit: vp

Value range: [0, +∞)

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## marginTop

```TypeScript
marginTop?: Length
```

Spacing between the indicator and text. It cannot be set in percentage.

Default value: **8.0**

Unit: vp

Value range: [0, +∞)

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Default:** 8

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: Length
```

Width of the indicator. It cannot be set in percentage.

Default value: **0.0**

Unit: vp

Value range: [0, +∞)

**NOTE:** 

If this parameter is set to **0**, the tab text width will be used instead.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Default:** 0

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
