# OnTabsAnimationStartCallback

```TypeScript
declare type OnTabsAnimationStartCallback = (index: number, targetIndex: number, extraInfo: TabsAnimationEvent) => void
```

Defines the callback triggered when the page transition animation starts.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-unnamed-declare type OnTabsAnimationStartCallback = (index: number, targetIndex: number, extraInfo: TabsAnimationEvent) => void--><!--Device-unnamed-declare type OnTabsAnimationStartCallback = (index: number, targetIndex: number, extraInfo: TabsAnimationEvent) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the currently displayed element. The index starts from 0. |
| targetIndex | number | Yes | Index of the target element of the switching animation. The index starts from 0. |
| extraInfo | [TabsAnimationEvent](arkts-arkui-tabs-comp-tabsanimationevent-i.md) | Yes | Animation-related information, including the displacement of the currently displayed element and the target element relative to the start position of **Tabs** along the main axis, and the release velocity. |
