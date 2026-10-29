# handleDumpTask (System API)

## Modules to Import

```TypeScript
```

## handleDumpTask

```TypeScript
function handleDumpTask(cb: TaskCallback): void
```

Sets the callback of the dump task. After GC, if a leak is determined, the incoming callback is executed.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-jsLeakWatcherNative-function handleDumpTask(cb: TaskCallback): void--><!--Device-jsLeakWatcherNative-function handleDumpTask(cb: TaskCallback): void-End-->

**System capability:** SystemCapability.HiviewDFX.HiChecker

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cb | [TaskCallback](arkts-performanceanalysis-taskcallback-t-sys.md) | Yes | Callback to execute on each dump event. |
