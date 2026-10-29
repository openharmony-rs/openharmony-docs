# setDumpDelay (System API)

## Modules to Import

```TypeScript
```

## setDumpDelay

```TypeScript
function setDumpDelay(delay: number): void
```

Sets the delay before executing the dump after GC, in milliseconds.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-jsLeakWatcherNative-function setDumpDelay(delay: int): void--><!--Device-jsLeakWatcherNative-function setDumpDelay(delay: int): void-End-->

**System capability:** SystemCapability.HiviewDFX.HiChecker

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| delay | number | Yes | Dump delay. <br>Unit: millisecond. . The value should be an integer. |
