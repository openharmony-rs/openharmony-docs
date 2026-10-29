# setGcDelay (System API)

## Modules to Import

```TypeScript
```

## setGcDelay

```TypeScript
function setGcDelay(delay: number): void
```

Sets the interval between each round of GC, in milliseconds.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-jsLeakWatcherNative-function setGcDelay(delay: int): void--><!--Device-jsLeakWatcherNative-function setGcDelay(delay: int): void-End-->

**System capability:** SystemCapability.HiviewDFX.HiChecker

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| delay | number | Yes | GC interval. <br>Unit: millisecond. . The value should be an integer. |
