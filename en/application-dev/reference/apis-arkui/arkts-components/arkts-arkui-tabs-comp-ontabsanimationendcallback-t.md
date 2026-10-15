# OnTabsAnimationEndCallback

```TypeScript
declare type OnTabsAnimationEndCallback = (index: number, extraInfo: TabsAnimationEvent) => void
```

Defines the callback triggered when the page transition animation ends.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-unnamed-declare type OnTabsAnimationEndCallback = (index: number, extraInfo: TabsAnimationEvent) => void--><!--Device-unnamed-declare type OnTabsAnimationEndCallback = (index: number, extraInfo: TabsAnimationEvent) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the currently displayed element, starting from 0. |
| extraInfo | [TabsAnimationEvent](arkts-arkui-tabs-comp-tabsanimationevent-i.md) | Yes | Animation information, which returns only the offset of the currently displayed element relative to the start position of **Tabs** along the main axis. |
