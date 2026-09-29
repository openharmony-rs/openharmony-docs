# TabBarBadgeStyle

```TypeScript
declare interface TabBarBadgeStyle
```

Represents a tab bar badge style object.

**Since:** 26.0.1

<!--Device-unnamed-declare interface TabBarBadgeStyle--><!--Device-unnamed-declare interface TabBarBadgeStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maxCount

```TypeScript
maxCount?: number
```

Maximum count of the badge. When the badge value exceeds this count, the badge displays the maximum count followed by a plus sign.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-TabBarBadgeStyle-maxCount?: number--><!--Device-TabBarBadgeStyle-maxCount?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value?: TabBarBadgeType
```

Badge value. If this parameter is not set or set to **undefined**, the badge is displayed as a dot without content.

**Type:** [TabBarBadgeType](arkts-arkui-tabcontent-comp-tabbarbadgetype-t.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

<!--Device-TabBarBadgeStyle-value?: TabBarBadgeType--><!--Device-TabBarBadgeStyle-value?: TabBarBadgeType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
