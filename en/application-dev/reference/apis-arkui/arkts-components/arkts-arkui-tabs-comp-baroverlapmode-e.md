# BarOverlapMode

```TypeScript
declare enum BarOverlapMode
```

Enumerates the overlap modes of the tab bar and tab content.

**Since:** 26.1.0

<!--Device-unnamed-declare enum BarOverlapMode--><!--Device-unnamed-declare enum BarOverlapMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SAFE_AREA_PADDING

```TypeScript
SAFE_AREA_PADDING = 2
```

The tab bar area becomes part of the safe area padding for the tab content. The tab content can extend into the tab bar area.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-BarOverlapMode-SAFE_AREA_PADDING = 2--><!--Device-BarOverlapMode-SAFE_AREA_PADDING = 2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## STACK

```TypeScript
STACK = 1
```

The tab bar floats on top of the tab content. The tab content occupies all available space. This is equivalent to **barOverlap(true)**.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-BarOverlapMode-STACK = 1--><!--Device-BarOverlapMode-STACK = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## STANDARD

```TypeScript
STANDARD = 0
```

The tab bar does not overlap with the tab content. The tab content height equals the Tabs height minus the tab bar height. This is equivalent to **barOverlap(false)**.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-BarOverlapMode-STANDARD = 0--><!--Device-BarOverlapMode-STANDARD = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
