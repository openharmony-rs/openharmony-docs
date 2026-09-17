# OnScrollCallback

```TypeScript
declare type OnScrollCallback = (scrollOffset: number, scrollState: ScrollState) => void
```

On scroll callback using in scrollable onDidScroll.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scrollOffset | number | Yes | offset this frame did scroll. |
| scrollState | [ScrollState](arkts-arkui-scrollstate-e.md) | Yes | current scroll state. |
