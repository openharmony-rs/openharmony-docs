# LayoutStyle

```TypeScript
declare enum LayoutStyle
```

Enumerates the tab layout modes when the tab bar is not scrolled in [Scrollable](arkts-arkui-tabs-comp-attribute.md#barmode3) mode.

| Name | Value | Description |  
| ---------- | -- | ---------------------------------------- |  
| ALWAYS_CENTER | 0 | When the tab content exceeds the tab bar width, the tab bar is scrollable.

When the tab content does not exceed the tab bar width, the tab bar is not scrollable and the tabs are compactly centered.|

| ALWAYS_AVERAGE_SPLIT | 1 | When the tab content exceeds the tab bar width, the tab bar is scrollable.

When the tab content does not exceed the tab bar width, the tab bar is not scrollable and all tabs evenly share the tab bar width.|

| SPACE_BETWEEN_OR_CENTER | 2 | When the tab content exceeds the tab bar width, the tab bar is scrollable.

When the tab content does not exceed the tab bar width but exceeds half of the tab bar width, the tab bar is not scrollable and the tabs are compactly centered.

When the tab content does not exceed half of the tab bar width, the tab bar is not scrollable, the tabs are centered, the spacing between tabs is equal, and the total width of all tabs occupies half of the tab bar width.|

**Since:** 10

<!--Device-unnamed-declare enum LayoutStyle--><!--Device-unnamed-declare enum LayoutStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ALWAYS_AVERAGE_SPLIT

```TypeScript
ALWAYS_AVERAGE_SPLIT = 1
```

If the tab content exceeds the tab bar width, the tabs are scrollable. If not, the tabs are not scrollable, and the width of the tab bar is evenly distributed among all tabs.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-LayoutStyle-ALWAYS_AVERAGE_SPLIT = 1--><!--Device-LayoutStyle-ALWAYS_AVERAGE_SPLIT = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ALWAYS_CENTER

```TypeScript
ALWAYS_CENTER = 0
```

If the tab content exceeds the tab bar width, the tabs are scrollable.

If not, the tabs are compactly centered on the tab bar and not scrollable.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-LayoutStyle-ALWAYS_CENTER = 0--><!--Device-LayoutStyle-ALWAYS_CENTER = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SPACE_BETWEEN_OR_CENTER

```TypeScript
SPACE_BETWEEN_OR_CENTER = 2
```

If the tab content exceeds the tab bar width, the tabs are scrollable.

If the tab content exceeds half the width of the tab bar but is still within the tab bar width, the tabs are compactly centered and not scrollable.

If the tab content does not exceed half the width of the tab bar, the tabs are centered within half the width of the tab bar with even spacing between them and are not scrollable.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-LayoutStyle-SPACE_BETWEEN_OR_CENTER = 2--><!--Device-LayoutStyle-SPACE_BETWEEN_OR_CENTER = 2-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
