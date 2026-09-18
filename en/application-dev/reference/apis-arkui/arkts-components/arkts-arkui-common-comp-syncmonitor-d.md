# @SyncMonitor

```TypeScript
declare const SyncMonitor: MonitorDecorator
```

Define SyncMonitor MethodDecorator. Decorator path parameters are the same as defined for Monitor. The function decorator is functionally equivalent to the UIUtils.addMonitor API with isSynchronous enabled. SyncMonitor must contain at least one path item, with multiple path items separated by commas. Path items are either observed attribute names or array item indices.The path in SyncMonitor supports wildcard at the end of a path item, but path items must never appear at the beginning or in the middle of a path. All other paths using one or more wildcard are invalid.

Functions decorated with @SyncMonitor can be used in @ObservedV2 objects and @ComponentV2.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [130001](../errorcode-stateManagement.md#130001-invalid-path-for-addmonitorclearmonitor) | The path is invalid. |
