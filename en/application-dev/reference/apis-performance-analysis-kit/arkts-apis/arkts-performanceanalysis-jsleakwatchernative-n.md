# jsLeakWatcherNative(This module provides the native implementation interfaces of jsLeakWatcher.)

```TypeScript
declare namespace jsLeakWatcherNative
```

Provides the native implementation interfaces used by jsLeakWatcher.

These interfaces are internal implementation details and are exposed as system APIs only. They should not be called directly by third-party applications.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-unnamed-declare namespace jsLeakWatcherNative--><!--Device-unnamed-declare namespace jsLeakWatcherNative-End-->

**System capability:** SystemCapability.HiviewDFX.HiChecker

**System API:** This is a system API.

## Modules to Import

```TypeScript
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [apiRecord](arkts-performanceanalysis-jsleakwatchernative-apirecord-f-sys.md#apirecord-1) | Records the API call metric. Only takes effect when API metrics are enabled. |
| [dumpRawHeap](arkts-performanceanalysis-jsleakwatchernative-dumprawheap-f-sys.md#dumprawheap-1) | Asynchronously dumps the raw heap snapshot to the given file path. |
| [dumpRawHeapSync](arkts-performanceanalysis-jsleakwatchernative-dumprawheapsync-f-sys.md#dumprawheapsync-1) | Synchronously dumps the raw heap snapshot to the given file path. |
| [getDumpStatus](arkts-performanceanalysis-jsleakwatchernative-getdumpstatus-f-sys.md#getdumpstatus-1) | Obtains the status parameter to determine whether to automatically perform jsleakwatcher detection. |
| [handleDumpTask](arkts-performanceanalysis-jsleakwatchernative-handledumptask-f-sys.md#handledumptask-1) | Sets the callback of the dump task. After GC, if a leak is determined, the incoming callback is executed. |
| [handleGCTask](arkts-performanceanalysis-jsleakwatchernative-handlegctask-f-sys.md#handlegctask-1) | Trigger and start a periodic GC task. When the term expires, the incoming call is automatically triggered. |
| [handleShutdownTask](arkts-performanceanalysis-jsleakwatchernative-handleshutdowntask-f-sys.md#handleshutdowntask-1) | Registers the shutdown task callback. |
| [registerArkUIObjectLifeCycleCallback](arkts-performanceanalysis-jsleakwatchernative-registerarkuiobjectlifecyclecallback-f-sys.md#registerarkuiobjectlifecyclecallback-1) | Registers a callback for ArkUI object lifecycle, which is invoked with a weak reference when the object is destroyed. |
| [registerWindowLifeCycleCallback](arkts-performanceanalysis-jsleakwatchernative-registerwindowlifecyclecallback-f-sys.md#registerwindowlifecyclecallback-1) | Registers a callback for window lifecycle, which is invoked when a window is destroyed. |
| [removeTask](arkts-performanceanalysis-jsleakwatchernative-removetask-f-sys.md#removetask-1) | Stops the periodic GC and dump task loop. |
| [reportRawHeap](arkts-performanceanalysis-jsleakwatchernative-reportrawheap-f-sys.md#reportrawheap-1) | Reports the raw heap result through HiSysEvent. |
| [setDumpDelay](arkts-performanceanalysis-jsleakwatchernative-setdumpdelay-f-sys.md#setdumpdelay-1) | Sets the delay before executing the dump after GC, in milliseconds. |
| [setGcDelay](arkts-performanceanalysis-jsleakwatchernative-setgcdelay-f-sys.md#setgcdelay-1) | Sets the interval between each round of GC, in milliseconds. |
| [unregisterArkUIObjectLifeCycleCallback](arkts-performanceanalysis-jsleakwatchernative-unregisterarkuiobjectlifecyclecallback-f-sys.md#unregisterarkuiobjectlifecyclecallback-1) | Unregisters the ArkUI object lifecycle callback. |
| [unregisterWindowLifeCycleCallback](arkts-performanceanalysis-jsleakwatchernative-unregisterwindowlifecyclecallback-f-sys.md#unregisterwindowlifecyclecallback-1) | Unregisters the window lifecycle callback. |
<!--DelEnd-->
