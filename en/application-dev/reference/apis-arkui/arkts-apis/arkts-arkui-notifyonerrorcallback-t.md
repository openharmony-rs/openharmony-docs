# NotifyOnErrorCallback

```TypeScript
export type NotifyOnErrorCallback = (error: RecoverableStorageError) => void
```

Defines a callback used to report errors of [RecoverableStorage](../../../ui/state-management/arkts-new-recoverablestorage.md). The callback is invoked on the UI thread and must not throw exceptions.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-unnamed-export type NotifyOnErrorCallback = (error: RecoverableStorageError) => void--><!--Device-unnamed-export type NotifyOnErrorCallback = (error: RecoverableStorageError) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| error | [RecoverableStorageError](arkts-arkui-arkui-statemanagement-recoverablestorageerror-i.md) | Yes | Error information. |
