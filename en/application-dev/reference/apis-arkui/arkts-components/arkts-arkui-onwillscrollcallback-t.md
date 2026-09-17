# OnWillScrollCallback

```TypeScript
declare type OnWillScrollCallback =
(scrollOffset: number, scrollState: ScrollState, scrollSource: ScrollSource) => void | ScrollResult
```

Called before scroll to allow developer to control real offset the Scrollable can scroll.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scrollOffset | number | Yes | offset this frame will scroll, which may or may not be reached. |
| scrollState | [ScrollState](arkts-arkui-scrollstate-e.md) | Yes | current scroll state. |
| scrollSource | [ScrollSource](../arkts-apis/arkts-arkui-scrollsource-e.md) | Yes | source of current scroll. |

**Return value:**

| Type | Description |
| --- | --- |
| void &#124; [ScrollResult](arkts-arkui-scrollresult-c.md) | the remain offset for the scrollable, same as scrollOffset when no ScrollResult is returned. |
