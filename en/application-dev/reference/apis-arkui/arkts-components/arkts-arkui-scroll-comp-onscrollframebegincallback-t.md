# OnScrollFrameBeginCallback

```TypeScript
declare type OnScrollFrameBeginCallback = (offset: number, state: ScrollState) => OnScrollFrameBeginHandlerResult
```

Represents the callback triggered before each frame scrolling starts.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-unnamed-declare type OnScrollFrameBeginCallback = (offset: number, state: ScrollState) => OnScrollFrameBeginHandlerResult--><!--Device-unnamed-declare type OnScrollFrameBeginCallback = (offset: number, state: ScrollState) => OnScrollFrameBeginHandlerResult-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | Yes | Amount to scroll by, in vp. |
| state | [ScrollState](arkts-arkui-list-comp-scrollstate-e.md) | Yes | Current scroll state. Idle indicates the idle state, Scroll indicates the scroll state, and Fling indicates the inertial scroll state. |

**Return value:**

| Type | Description |
| --- | --- |
| [OnScrollFrameBeginHandlerResult](arkts-arkui-scroll-comp-onscrollframebeginhandlerresult-i.md) | Actual scroll amount. The **Scroll** component will scroll based on the **offsetRemain** in the return value. |
