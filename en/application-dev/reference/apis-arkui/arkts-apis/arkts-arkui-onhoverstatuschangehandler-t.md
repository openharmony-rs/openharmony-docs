# OnHoverStatusChangeHandler

```TypeScript
export type OnHoverStatusChangeHandler = (status: HoverModeStatus) => void
```

Defines an event handler for hover state changes.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| status | [HoverModeStatus](arkts-arkui-arkui-advanced-foldsplitcontainer-hovermodestatus-i.md) | Yes | Status information when the foldable screen enters or exits hover mode. |
