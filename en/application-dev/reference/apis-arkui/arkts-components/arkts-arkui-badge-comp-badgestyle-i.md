# BadgeStyle

```TypeScript
declare interface BadgeStyle
```

Describes the badge style. It includes the font color, font size, badge color, badge size, etc.

> **NOTE:** 
> 
> - When **borderWidth** is set to a value greater than 0 and **borderColor** is different from **badgeColor**, the badge is drawn before the border. Edge pixels are anti-aliased, which produces semi-transparent pixels. This causes the border in **badgeColor** to become visible at the four corners. To implement related scenarios, it is recommended that you use the [Text](arkts-arkui-text-comp.md#text) component with its [outline](arkts-arkui-common-comp-commonmethod-c.md#outline) attribute instead of the **Badge** component.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## badgeColor

```TypeScript
badgeColor?: ResourceColor
```

Badge color.

Default value: **Color.Red**

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Default:** Color.Red

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## badgeSize

```TypeScript
badgeSize?: number | ResourceStr
```

Badge size. The value of this parameter is a string of the number type. The unit can be px, vp, fp, or lpx, for example, 10 or 16fp. If no unit is specified, fp is used by default. If the value is **0**, the badge is not displayed.

Unit: fp. Default value: **16vp**.

**NOTE:** 

1. Percentage values are not supported. If a percentage value is set, the default value is used.
2. If **fontSize** is set and **badgeSize** is smaller than fontSize, **badgeSize** will take effect based on the
value of **fontSize**.

**Type:** number &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Default:** 16vp

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderColor

```TypeScript
borderColor?: ResourceColor
```

Color of the background border.

Default value: **Color.Red**

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Default:** Color.Red

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderWidth

```TypeScript
borderWidth?: Length
```

Width of the background border.

Default value: **1**

Unit: vp

**NOTE:** 

Percentage values are not supported. If a percentage value is set, the default value is used.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Default:** 1vp

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ResourceColor
```

Font color.

Default value: **Color.White**

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Default:** Color.White

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableAutoAvoidance

```TypeScript
enableAutoAvoidance?: boolean
```

Whether to enable avoidance when the badge text is extended.

The value **true** means to enable avoidance, and **false** means the opposite.

Default value: **false**.

**NOTE:** 

1. The avoidance effect is that the badge text is extended to the inside of the component.
2. When the width of the outer border is greater than 0, the extension start point of the badge is the inner side
of the outer border.
3. When position is set to a specific coordinate value, the badge does not perform avoidance.

**Type:** boolean

**Default:** false

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: number | ResourceStr
```

Font size. The value of this parameter is a string of the number type. The unit can be px, vp, fp, or lpx, for example, 10 or 10fp. If no unit is specified, fp is used by default.

Default value: **10vp**

Default unit: fp

The value must be greater than 0. If the value is **0**, the text is not displayed. If the value is less than 0, the default value is used.

**NOTE:** 

1. Percentage values are not supported. If a percentage value is set, the default value is used.

**Type:** number &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Default:** 10vp

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontWeight

```TypeScript
fontWeight?: number | FontWeight | ResourceStr
```

Font weight of the text. For the number type, the value ranges from 100 to 900, at an interval of 100. A larger value indicates a bolder font. For the number type, if the value is not within the range, the default value **400** is used. For the string type, only strings that represent a number, for example, **400**, and the following enumerated values of **FontWeight** are supported: **bold**, **bolder**, **lighter**, **regular**, and **medium**.

Default value: **FontWeight.Normal**

**NOTE:** 

Percentage values are not supported. If a percentage value is set, the default value is used. The ResourceStr type is supported since API version 20.

**Type:** number &#124; [FontWeight](../arkts-apis/arkts-arkui-fontweight-e.md) &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## outerBorderColor

```TypeScript
outerBorderColor?: ResourceColor
```

Color of the background outer border.

Default value: **Color.White**

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Default:** Color.White

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## outerBorderWidth

```TypeScript
outerBorderWidth?: LengthMetrics
```

Width of the background outer border.

Default value: **0**.

Unit: vp

Percentage values are not supported. If a percentage value is set, the default value is used.

**Type:** LengthMetrics

**Default:** 0vp

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
