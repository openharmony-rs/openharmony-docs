# BadgeStyle

```TypeScript
declare interface BadgeStyle
```

Defines the style of a badge, including the text color, size, font weight, badge color, and badge size.

> **NOTE:** 
> 
> When `borderWidth` is greater than 0 and the colors of `borderColor` and `badgeColor` are different, the badge is
> drawn first and then the border. Because edge pixels are anti-aliased, semi-transparent pixels are generated, and
> border lines in the `badgeColor` color appear at the four corners. To implement such a scenario, you are advised to
> use the [Text](arkts-arkui-text-comp.md) component and set [outline](arkts-arkui-common-comp-commonmethod-c.md#outline) instead
> of the Badge component.

**Since:** 7

<!--Device-unnamed-declare interface BadgeStyle--><!--Device-unnamed-declare interface BadgeStyle-End-->

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

<!--Device-BadgeStyle-badgeColor?: ResourceColor--><!--Device-BadgeStyle-badgeColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## badgeSize

```TypeScript
badgeSize?: number | ResourceStr
```

Size of the badge. The string type supports only the string form of a number value, which can carry a unit. The supported units are "px", "vp", "fp", and "lpx", for example, "16" and "16fp". If no unit is carried, the default unit is "fp".

Default value: **16vp**

Default unit: **fp**

Value range: greater than 0. When the value is 0, the badge is not displayed. When the value is less than 0, the default value is used.

**NOTE:** 

1. Percentage is not supported. When a percentage is set, the default value is used.
2. The ResourceStr type is supported since API version 20.
3. When **fontSize** is set and **badgeSize** is smaller than **fontSize**, **badgeSize** takes effect as **fontSize**.

**Type:** number &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Default:** 16vp

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-BadgeStyle-badgeSize?: number | ResourceStr--><!--Device-BadgeStyle-badgeSize?: number | ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderColor

```TypeScript
borderColor?: ResourceColor
```

Base border color.

Default value: **Color.Red**

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Default:** Color.Red

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-BadgeStyle-borderColor?: ResourceColor--><!--Device-BadgeStyle-borderColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## borderWidth

```TypeScript
borderWidth?: Length
```

Base border width.

Default value: **1**

Unit: **vp**

**NOTE:** 

Percentage is not supported. When a percentage is set, the default value is used.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Default:** 1vp

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-BadgeStyle-borderWidth?: Length--><!--Device-BadgeStyle-borderWidth?: Length-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ResourceColor
```

Text color.

Default value: **Color.White**

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Default:** Color.White

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-BadgeStyle-color?: ResourceColor--><!--Device-BadgeStyle-color?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableAutoAvoidance

```TypeScript
enableAutoAvoidance?: boolean
```

Whether to avoid the badge text when it extends beyond the component.

The value **true** means to avoid, and **false** means not to avoid.

Default value: **false**

**NOTE:** 

1. The avoidance effect means that the badge text extends toward the inside of the component.
2. When the outer border width is greater than 0, the badge starts to extend from the inner side of the outer border.
3. When **position** is set to specific coordinate values, the badge does not perform avoidance.

**Type:** boolean

**Default:** false

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-BadgeStyle-enableAutoAvoidance?: boolean--><!--Device-BadgeStyle-enableAutoAvoidance?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: number | ResourceStr
```

Text size. The string type supports only the string form of a number value, which can carry a unit. The supported units are "px", "vp", "fp", and "lpx", for example, "10" and "10fp". If no unit is carried, the default unit is "fp".

Default value: **10vp**

Default unit: **fp**

Value range: greater than 0. When the value is 0, the text is not displayed. When the value is less than 0, the default value is used.

**NOTE:** 

1. Percentage is not supported. When a percentage is set, the default value is used.
2. The ResourceStr type is supported since API version 20.

**Type:** number &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Default:** 10vp

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-BadgeStyle-fontSize?: number | ResourceStr--><!--Device-BadgeStyle-fontSize?: number | ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fontWeight

```TypeScript
fontWeight?: number | FontWeight | ResourceStr
```

Font weight of the text. For the number type, the value range is [100, 900] at an interval of 100. A larger value indicates a heavier font weight. When a number value outside the range is set, the default value 400 is used. The string type supports only the string form of a number value, for example, "400", as well as "bold", "bolder", "lighter", "regular", and "medium", which correspond to the respective enum values in FontWeight.

Default value: **FontWeight.Normal**

**NOTE:** 

Percentage is not supported. When a percentage is set, the default value is used. The ResourceStr type is supported since API version 20.

**Type:** number &#124; [FontWeight](../arkts-apis/arkts-arkui-fontweight-e.md) &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-BadgeStyle-fontWeight?: number | FontWeight | ResourceStr--><!--Device-BadgeStyle-fontWeight?: number | FontWeight | ResourceStr-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## outerBorderColor

```TypeScript
outerBorderColor?: ResourceColor
```

Base outer border color.

Default value: **Color.White**

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Default:** Color.White

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-BadgeStyle-outerBorderColor?: ResourceColor--><!--Device-BadgeStyle-outerBorderColor?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## outerBorderWidth

```TypeScript
outerBorderWidth?: LengthMetrics
```

Base outer border width.

Default value: **0**

Unit: **vp**

Percentage is not supported. When a percentage is set, the default value is used.

**Type:** LengthMetrics

**Default:** 0vp

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-BadgeStyle-outerBorderWidth?: LengthMetrics--><!--Device-BadgeStyle-outerBorderWidth?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
