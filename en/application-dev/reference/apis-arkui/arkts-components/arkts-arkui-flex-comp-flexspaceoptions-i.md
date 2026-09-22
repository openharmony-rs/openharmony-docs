# FlexSpaceOptions

```TypeScript
declare interface FlexSpaceOptions
```

Sets the spacing between child components along the main axis or cross axis of the **Flex** component.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## cross

```TypeScript
cross?: LengthMetrics
```

Spacing between adjacent lines on the cross axis of the **Flex** container. After being set, adjacent lines in the cross axis direction are separated by the specified spacing. This takes effect only in multi-line layouts (when **wrap** is set to **Wrap** or **WrapReverse**). This parameter does not take effect when **space.cross** is a negative number, or when **justifyContent** is set to **FlexAlign.SpaceBetween**, **FlexAlign.SpaceAround**, or **FlexAlign.SpaceEvenly**.

Default value: **LengthMetrics.px(0)**

**Type:** LengthMetrics

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## main

```TypeScript
main?: LengthMetrics
```

Spacing between adjacent child components on the main axis of the **Flex** container. After being set, adjacent child components in the main axis direction are separated by the specified spacing. This takes effect in both single-line and multi-line layouts. This parameter does not take effect when **space.main** is a negative number, or when **justifyContent** is set to **FlexAlign.SpaceBetween**, **FlexAlign.SpaceAround**, or **FlexAlign.SpaceEvenly**.

Default value: **LengthMetrics.px(0)**

**Type:** LengthMetrics

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
