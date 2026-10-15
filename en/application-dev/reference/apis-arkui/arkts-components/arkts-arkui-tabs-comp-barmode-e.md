# BarMode

```TypeScript
declare enum BarMode
```

Enumerates layout modes of the tab bar.

**Since:** 7

<!--Device-unnamed-declare enum BarMode--><!--Device-unnamed-declare enum BarMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Fixed

```TypeScript
Fixed = 1
```

All **TabBars** evenly share the **barWidth** (or the **barHeight** for a vertical **Tabs**).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-BarMode-Fixed = 1--><!--Device-BarMode-Fixed = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Scrollable

```TypeScript
Scrollable = 0
```

Each tab bar uses its actual layout width. When the total length exceeds the [barWidth](arkts-arkui-tabs-comp-attribute.md#barwidth) of a horizontal **Tabs** or the [barHeight](arkts-arkui-tabs-comp-attribute.md#barheight1) of a vertical **Tabs**, the tab bar can be scrolled.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-BarMode-Scrollable = 0--><!--Device-BarMode-Scrollable = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
