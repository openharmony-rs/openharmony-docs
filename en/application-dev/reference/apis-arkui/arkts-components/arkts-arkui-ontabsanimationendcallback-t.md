# OnTabsAnimationEndCallback

```TypeScript
declare type OnTabsAnimationEndCallback = (index: number, extraInfo: TabsAnimationEvent) => void
```

Defines the callback triggered when the tab switching animation ends.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the currently displayed element. The index is zero-based. |
| extraInfo | [TabsAnimationEvent](arkts-arkui-tabsanimationevent-i.md) | Yes | Extra information of the animation, which is the offset of the currently displayed element relative to the start position of the **Tabs** along the main axis. |
