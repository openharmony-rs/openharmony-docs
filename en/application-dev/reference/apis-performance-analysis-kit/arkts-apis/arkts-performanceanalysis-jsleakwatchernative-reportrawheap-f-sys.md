# reportRawHeap (System API)

## Modules to Import

```TypeScript
```

## reportRawHeap

```TypeScript
function reportRawHeap(report: RawHeapReport): void
```

Reports the raw heap result through HiSysEvent.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-jsLeakWatcherNative-function reportRawHeap(report: RawHeapReport): void--><!--Device-jsLeakWatcherNative-function reportRawHeap(report: RawHeapReport): void-End-->

**System capability:** SystemCapability.HiviewDFX.HiChecker

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| report | [RawHeapReport](arkts-performanceanalysis-hiviewdfx-jsleakwatchernative-rawheapreport-i-sys.md) | Yes | Raw heap report information. |
