# BadgeParam

```TypeScript
declare interface BadgeParam
```

Contains the basic parameters for creating a Badge component.

**Since:** 7

<!--Device-unnamed-declare interface BadgeParam--><!--Device-unnamed-declare interface BadgeParam-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## position

```TypeScript
position?: BadgePosition | Position
```

Badge display position.

Default value: **BadgePosition.RightTop**

**NOTE:** 

When **Position** is used as an input parameter, percentage is not supported. If an invalid value is set, it is processed as (0,0), which is the upper left corner of the component.

When **BadgePosition** is used as an input parameter, the mirrored display is controlled by the Direction attribute.

**Type:** [BadgePosition](arkts-arkui-badge-comp-badgeposition-e.md) &#124; Position

**Default:** BadgePosition.RightTop

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-BadgeParam-position?: BadgePosition | Position--><!--Device-BadgeParam-position?: BadgePosition | Position-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style: BadgeStyle
```

Style of the **Badge** component, including the text color, size, badge color, and badge size.

**Type:** [BadgeStyle](arkts-arkui-badge-comp-badgestyle-i.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-BadgeParam-style: BadgeStyle--><!--Device-BadgeParam-style: BadgeStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
