# BadgeParam

```TypeScript
declare interface BadgeParam
```

Provides basic parameters for creating a badge.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## position

```TypeScript
position?: BadgePosition | Position
```

Position to display the badge relative to the parent component.

Default value: **BadgePosition.RightTop**

**NOTE:** 

With the **Position** type, percentage values are not supported. If an invalid value is set, the default value **(0,0)**, which indicates the upper left corner of the component, will be used.

With the **BadgePosition** type, the position is mirrored based on the Direction property.

**Type:** [BadgePosition](arkts-arkui-badge-comp-badgeposition-e.md) &#124; Position

**Default:** BadgePosition.RightTop

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style: BadgeStyle
```

Style of the badge, including the font color, font size, badge color, and badge size.

**Type:** [BadgeStyle](arkts-arkui-badge-comp-badgestyle-i.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
