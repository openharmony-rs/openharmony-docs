# IndicatorStyle

```TypeScript
declare interface IndicatorStyle
```

Defines the style of the navigation indicator.

**Since:** 8

**Deprecated since:** 10

**Substitutes:** [Indicator](arkts-arkui-swiper-comp-indicator-c.md)

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## bottom

```TypeScript
bottom?: Length
```

Position of the navigation indicator relative to the bottom edge of the **Swiper** component.

If neither **top** nor **bottom** is set, the navigation indicator is aligned at the bottom along the cross axis based on its own size and the size of the **Swiper** component, which is the same effect as setting **bottom=0**.

If the value specified is **0**, the navigation indicator is placed at the position 0.

Priority: lower than the **top** property

Value range: [0, Swiper height - Navigation indicator area height]. Values outside this range are adjusted to the nearest boundary.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 8

**Deprecated since:** 10

**Substitutes:** bottom

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ResourceColor
```

Color of the navigation indicator.

Default value: **'#1A182431'** (light gray)

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Since:** 8

**Deprecated since:** 10

**Substitutes:** [color](arkts-arkui-swiper-comp-dotindicator-c.md#color)

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## left

```TypeScript
left?: Length
```

Position of the navigation indicator relative to the left edge of the **Swiper** component.

If neither **left** nor **right** is set, the navigation indicator is centered along the main axis based on its own size and the size of the **Swiper** component.

If the value specified is **0**, the navigation indicator is placed at the position 0.

Priority: higher than the **right** property

Value range: [0, Swiper width - Navigation indicator area width]. Values outside this range are adjusted to the nearest boundary.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 8

**Deprecated since:** 10

**Substitutes:** left

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## mask

```TypeScript
mask?: boolean
```

Whether to enable the mask for the navigation indicator.

**true**: yes; **false**: no

Default value: **false**.

**Type:** boolean

**Since:** 8

**Deprecated since:** 10

**Substitutes:** [mask](arkts-arkui-swiper-comp-dotindicator-c.md#mask)

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## right

```TypeScript
right?: Length
```

Position of the navigation indicator relative to the right edge of the **Swiper** component.

If neither **left** nor **right** is set, the navigation indicator is centered along the main axis based on its own size and the size of the **Swiper** component.

If the value specified is **0**, the navigation indicator is placed at the position 0.

Priority: lower than the **left** property.

Value range: [0, Swiper width - Navigation indicator area width]. Values outside this range are adjusted to the nearest boundary.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 8

**Deprecated since:** 10

**Substitutes:** right

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## selectedColor

```TypeScript
selectedColor?: ResourceColor
```

Color of the selected navigation indicator.

Default value: **'#007DFF'** (blue)

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Since:** 8

**Deprecated since:** 10

**Substitutes:** selectColor

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: Length
```

Diameter of the navigation indicator. Percentage values are not supported.

Default value: **6vp**

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 8

**Deprecated since:** 10

**Substitutes:** [DotIndicator](arkts-arkui-swiper-comp-dotindicator-c.md)

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## top

```TypeScript
top?: Length
```

Position of the navigation indicator relative to the top edge of the **Swiper** component.

If neither **top** nor **bottom** is set, the navigation indicator is aligned at the bottom along the cross axis based on its own size and the size of the **Swiper** component, which is the same effect as setting **bottom=0**.

If the value specified is **0**, the navigation indicator is placed at the position 0.

Priority: higher than the **bottom** property

Value range: [0, Swiper height - Navigation indicator area height]. Values outside this range are adjusted to the nearest boundary.

**Type:** [Length](../arkts-apis/arkts-arkui-length-t.md)

**Since:** 8

**Deprecated since:** 10

**Substitutes:** top

**System capability:** SystemCapability.ArkUI.ArkUI.Full
