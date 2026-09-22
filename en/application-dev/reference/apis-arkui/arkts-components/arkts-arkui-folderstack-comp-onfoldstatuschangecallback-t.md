# OnFoldStatusChangeCallback

```TypeScript
declare type OnFoldStatusChangeCallback = (event: OnFoldStatusChangeInfo) => void
```

Triggered when the fold status changes&lt;!--RP4--&gt;, which takes effect only in landscape mode&lt;!--RP4End--&gt;.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [OnFoldStatusChangeInfo](arkts-arkui-folderstack-comp-onfoldstatuschangeinfo-i.md) | Yes | Information about the fold status change. This takes effect only in landscape mode. |
