# TabsCustomContentTransitionCallback

```TypeScript
declare type TabsCustomContentTransitionCallback = (from: number, to: number) => TabContentAnimatedTransition | undefined
```

Callback invoked when the custom page switching animation of **Tabs** starts.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-unnamed-declare type TabsCustomContentTransitionCallback = (from: number, to: number) => TabContentAnimatedTransition | undefined--><!--Device-unnamed-declare type TabsCustomContentTransitionCallback = (from: number, to: number) => TabContentAnimatedTransition | undefined-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| from | number | Yes | Index of the currently displayed page when the animation starts. The index starts from 0.<br>Value range: [0, total number of tabs - 1]. If the value exceeds the maximum index or is less than 0, no transition animation is applied. |
| to | number | Yes | Index of the target page when the animation starts. The index starts from 0.<br>Value range: [0, total number of tabs - 1]. If the value exceeds the maximum index or is less than 0, no transition animation is applied. |

**Return value:**

| Type | Description |
| --- | --- |
| [TabContentAnimatedTransition](arkts-arkui-tabs-comp-tabcontentanimatedtransition-i.md) &#124; undefined | Information about the custom switching animation. |
