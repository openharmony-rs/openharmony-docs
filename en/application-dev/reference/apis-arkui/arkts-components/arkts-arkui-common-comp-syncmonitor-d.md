# @SyncMonitor

```TypeScript
declare const SyncMonitor: MonitorDecorator
```

\@SyncMonitor is used for state management V2 to synchronously listen to the changes of state variables, enabling deep listening for state variables. It is applicable to scenarios where precise listening to deep state changes, such as changes in nested object properties and in elements in an array, is required. This addresses the issue that traditional listening methods cannot detect changes in deep-level properties, thereby improving the accuracy of state management and development efficiency.

For details, see [\@SyncMonitor Decorator: Synchronous Listening for Value Changes of the State Variables](../../../ui/state-management/arkts-new-syncmonitor.md).

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-unnamed-declare const SyncMonitor: MonitorDecorator--><!--Device-unnamed-declare const SyncMonitor: MonitorDecorator-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [130001](../errorcode-stateManagement.md#130001-invalid-path-for-addmonitorclearmonitor) | The path is invalid. |
