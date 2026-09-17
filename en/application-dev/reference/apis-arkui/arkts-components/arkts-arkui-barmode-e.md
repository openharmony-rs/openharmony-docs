# BarMode

Enumerates layout modes of the tab bar.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Scrollable

```TypeScript
Scrollable = 0
```

The width of each tab is determined by the actual layout. The tabs are scrollable in the following case: In horizontal layout, the total width exceeds the tab bar width; in vertical layout, the total height exceeds the tab bar height.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Fixed

```TypeScript
Fixed = 1
```

The width of each tab is determined by equally dividing the number of tabs by the bar width (or bar height in the vertical layout).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
