# handleGCTask (System API)

## Modules to Import

```TypeScript
```

## handleGCTask

```TypeScript
function handleGCTask(cb: TaskCallback): void
```

Trigger and start a periodic GC task. When the term expires, the incoming call is automatically triggered.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-jsLeakWatcherNative-function handleGCTask(cb: TaskCallback): void--><!--Device-jsLeakWatcherNative-function handleGCTask(cb: TaskCallback): void-End-->

**System capability:** SystemCapability.HiviewDFX.HiChecker

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cb | [TaskCallback](arkts-performanceanalysis-taskcallback-t-sys.md) | Yes | Callback to execute on each GC event. |
