# LayoutStyle

Enumerates the tab layout styles of the tab bar when not scrolling in scrollable mode.

**Since:** 10

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ALWAYS_AVERAGE_SPLIT

```TypeScript
ALWAYS_AVERAGE_SPLIT = 1
```

If the tab content exceeds the tab bar width, the tabs are scrollable. If not, the tabs are not scrollable, and the width of the tab bar is evenly distributed among all tabs.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full
