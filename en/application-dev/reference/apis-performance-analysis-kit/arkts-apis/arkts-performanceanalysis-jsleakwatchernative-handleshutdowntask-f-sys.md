# handleShutdownTask (System API)

## Modules to Import

```TypeScript
```

## handleShutdownTask

```TypeScript
function handleShutdownTask(cb: TaskCallback): void
```

Registers the shutdown task callback.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-jsLeakWatcherNative-function handleShutdownTask(cb: TaskCallback): void--><!--Device-jsLeakWatcherNative-function handleShutdownTask(cb: TaskCallback): void-End-->

**System capability:** SystemCapability.HiviewDFX.HiChecker

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cb | [TaskCallback](arkts-performanceanalysis-taskcallback-t-sys.md) | Yes | Callback to execute when jsLeakWatcher is shut down. |
