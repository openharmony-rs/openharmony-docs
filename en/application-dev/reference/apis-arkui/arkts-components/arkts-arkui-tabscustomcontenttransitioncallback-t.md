# TabsCustomContentTransitionCallback

```TypeScript
declare type TabsCustomContentTransitionCallback = (from: number, to: number) => TabContentAnimatedTransition | undefined
```

Defines the callback invoked when the custom tab transition animation starts.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| from | number | Yes | Index of the currently displayed tab before the animation starts. The index is zero-based.<br>Value range: [0, Index value — 1]. If the value exceeds the index value or is less than 0, no transition animation is displayed. |
| to | number | Yes | Index of the target tab before the animation starts. The index is zero-based.<br>Value range: [0, Index value — 1]. If the value exceeds the index value or is less than 0, no transition animation is displayed. |

**Return value:**

| Type | Description |
| --- | --- |
| [TabContentAnimatedTransition](arkts-arkui-tabcontentanimatedtransition-i.md) &#124; undefined | Information about the custom tab switching animation. |
